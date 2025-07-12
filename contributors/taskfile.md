# Taskfile Refactoring Guidelines

## Rules Table

| Rule ID | Rule Summary                                                       |
| ------- | ------------------------------------------------------------------ |
| R1      | Every task MUST have preconditions                                 |
| R2      | Break complex tasks into atomic units                              |
| R3      | Use `deps:` instead of sequential commands                         |
| R4      | Use `platforms:` for OS-specific commands                          |
| R5      | Use `vars:` instead of shell variables                             |
| R6      | Create `_internal` tasks for reusable logic                        |
| R7      | Use `utils:trash` for all file removal                             |
| R8      | Include default task in every taskfile                             |
| R9      | Add `desc:` to every task                                          |
| R10     | Split PowerShell commands with platforms                           |
| R11     | Use literal style for all commands                                 |
| R12     | Use `status:` field to skip already-completed operations           |
| R13     | Extract repeated environment variables to task-level or file-level |
| R14     | Use `sources:` for file-based task invalidation                    |
| R15     | Use `dotenv:` for environment file loading                         |
| R16     | Mark user-facing tasks with `interactive: true`                    |
| R17     | Avoid complex inline command building - use internal tasks         |
| R18     | Remove echo-only tasks - taskfiles are self-documenting            |
| R19     | Remove all unnecessary output - no colors or progress messages     |
| R20     | Ensure all task dependencies are resolvable                        |
| R21     | Use proper platform conditionals in preconditions                  |

---

## R1: Every task MUST have preconditions

```yaml
# ❌ BAD
tasks:
  build:
    cmds:
      - go build -o bin/app

# ✅ GOOD
tasks:
  build:
    desc: "Build application"
    preconditions:
      - sh: which go
        msg: "Go is not installed or not in PATH"
    cmds:
      - go build -o bin/app
```

## R2: Break complex tasks into atomic units

```yaml
# ❌ BAD
tasks:
  all:
    cmds:
      - go build -o bin/app
      - go test ./...
      - docker build -t app:latest .

# ✅ GOOD
tasks:
  all:
    desc: "Build, test and package"
    deps: [build, test, docker-build]

  build:
    desc: "Build binary"
    preconditions:
      - sh: which go
        msg: "Go not found"
    cmds:
      - go build -o bin/app
```

## R3: Use deps instead of sequential commands

```yaml
# ❌ BAD
tasks:
  deploy:
    cmds:
      - task: build
      - task: test
      - echo "Deploying..."

# ✅ GOOD
tasks:
  deploy:
    desc: "Deploy application"
    deps: [build, test]
    preconditions:
      - sh: which kubectl
        msg: "kubectl not found"
    cmds:
      - echo "Deploying..."
```

## R4: Use platforms for OS-specific commands

```yaml
# ❌ BAD
cmds:
  - |
    {{if eq OS "windows"}}
      powershell Get-Date
    {{else}}
      date
    {{end}}

# ✅ GOOD
cmds:
  - cmd: |
      powershell -NoProfile -Command 'Get-Date'
    platforms: [windows]
  - cmd: date
    platforms: [linux, darwin]
```

## R5: Use vars instead of shell variables

```yaml
# ❌ BAD
tasks:
  build:
    cmds:
      - |
        VERSION=$(git describe --tags)
        go build -ldflags "-X main.version=$VERSION"

# ✅ GOOD
vars:
  VERSION:
    sh: git describe --tags

tasks:
  build:
    preconditions:
      - sh: which go
        msg: "Go not found"
    cmds:
      - go build -ldflags "-X main.version={{.VERSION}}"
```

## R6: Create internal tasks for reusable logic

```yaml
# ❌ BAD
tasks:
  build-linux:
    cmds:
      - GOOS=linux GOARCH=amd64 go build -o bin/app-linux

  build-windows:
    cmds:
      - GOOS=windows GOARCH=amd64 go build -o bin/app.exe

# ✅ GOOD
tasks:
  _build-cross:
    internal: true
    preconditions:
      - sh: which go
        msg: "Go not found"
    cmds:
      - GOOS={{.GOOS}} GOARCH={{.GOARCH}} go build -o {{.OUTPUT}}

  build-linux:
    desc: "Build for Linux"
    cmds:
      - task: _build-cross
        vars: {GOOS: linux, GOARCH: amd64, OUTPUT: bin/app-linux}
```

## R7: Use utils:trash for file removal

```yaml
# ❌ BAD
tasks:
  clean:
    cmds:
      - rm -rf build/
      - del /Q /S build\*

# ✅ GOOD
tasks:
  clean:
    desc: "Clean build artifacts"
    preconditions:
      - sh: test -d build
        msg: "Nothing to clean"
    cmds:
      - task: utils:trash
        vars:
          TARGET_PATH: build
```

## R8: Include default task

```yaml
# ✅ REQUIRED in every taskfile
tasks:
  default:
    silent: true
    cmds:
      - task: utils:default
```

## R9: Add desc to every task

```yaml
# ❌ BAD
tasks:
  test:
    cmds:
      - go test ./...

# ✅ GOOD
tasks:
  test:
    desc: "Run unit tests"
    preconditions:
      - sh: which go
        msg: "Go not found"
    cmds:
      - go test ./...
```

## R10: Split PowerShell commands

```yaml
# ❌ BAD
cmds:
  - powershell: Get-Process | Where-Object {$_.CPU -gt 100}

# ✅ GOOD
cmds:
  - cmd: |
      powershell -NoProfile -Command '
        Get-Process | Where-Object {$_.CPU -gt 100}
      '
    platforms: [windows]
  - cmd: ps aux | awk '$3 > 10.0'
    platforms: [linux, darwin]
```

## R11: Use literal style for commands

```yaml
# ❌ BAD
tasks:
  setup:
    cmds:
      - mkdir -p build/tmp
      - cp config.yaml build/
      - echo "Setup complete"

# ✅ GOOD
tasks:
  setup:
    desc: "Setup build environment"
    preconditions:
      - sh: test -f config.yaml
        msg: "config.yaml not found"
    cmds:
      - cmd: |
          mkdir -p build/tmp
      - cmd: |
          cp config.yaml build/
      - cmd: |
          echo "Setup complete"
```

## R12: Use status field to skip completed operations

```yaml
# ✅ GOOD
tasks:
  install-hooks:
    desc: "Install git hooks"
    preconditions:
      - sh: which pre-commit
        msg: "pre-commit not found"
    cmds:
      - cmd: |
          pre-commit install
    status:
      - test -f .git/hooks/pre-commit
```

## R13: Extract repeated environment variables

```yaml
# ❌ BAD - Same env vars repeated in every task
tasks:
  plan:
    env:
      AWS_ACCESS_KEY_ID:
        sh: jq -r ".data.access_key" < .aws-credentials.json
      AWS_SECRET_ACCESS_KEY:
        sh: jq -r ".data.secret_key" < .aws-credentials.json
    cmds:
      - terraform plan

  apply:
    env:
      AWS_ACCESS_KEY_ID:
        sh: jq -r ".data.access_key" < .aws-credentials.json
      AWS_SECRET_ACCESS_KEY:
        sh: jq -r ".data.secret_key" < .aws-credentials.json
    cmds:
      - terraform apply

# ✅ GOOD - Centralized at file level
env:
  AWS_ACCESS_KEY_ID:
    sh: jq -r ".data.access_key" < .aws-credentials.json
  AWS_SECRET_ACCESS_KEY:
    sh: jq -r ".data.secret_key" < .aws-credentials.json

tasks:
  plan:
    desc: "Plan infrastructure"
    preconditions:
      - sh: which terraform
        msg: "Terraform not found"
    cmds:
      - terraform plan
```

## R14: Use sources for file-based invalidation

```yaml
# ✅ GOOD
tasks:
  build:
    desc: "Build only if source changed"
    preconditions:
      - sh: which go
        msg: "Go not found"
    sources:
      - "**/*.go"
      - go.mod
      - go.sum
    cmds:
      - go build -o bin/app
```

## R15: Use dotenv for environment files

```yaml
# ✅ GOOD
version: "3"
dotenv: [.env, .env.local]

tasks:
  deploy:
    desc: "Deploy with env vars from .env"
    preconditions:
      - sh: test -f .env
        msg: ".env file not found"
    cmds:
      - echo "Deploying to $ENVIRONMENT"
```

## R16: Mark interactive tasks

```yaml
# ✅ GOOD
tasks:
  login:
    desc: "Interactive login"
    interactive: true
    preconditions:
      - sh: which vault
        msg: "Vault not found"
    cmds:
      - vault login
```

## R17: Avoid complex inline command building

```yaml
# ❌ BAD
tasks:
  lint:
    cmds:
      - cmd: |
          powershell -c '
            $files=(git ls-files "*.go");
            $COMMAND=@("golint");
            foreach ($file in $files) {
              $COMMAND+=@($file)
            };
            Invoke-Expression ($COMMAND -join " ")'

# ✅ GOOD
tasks:
  _get-go-files:
    internal: true
    cmds:
      - cmd: git ls-files "*.go"

  lint:
    desc: "Lint Go files"
    preconditions:
      - sh: which golint
        msg: "golint not found"
    vars:
      GO_FILES:
        sh: task _get-go-files
    cmds:
      - cmd: |
          golint {{.GO_FILES}}
```

## R18: Remove echo-only tasks

Tasks that only echo or print information are useless. Taskfiles are
self-documenting through `desc:` fields and the default task with fzf provides
interactive discovery.

```yaml
# ❌ BAD
tasks:
  detect-tool:
    desc: "Auto-detect tool name"
    cmds:
      - cmd: |
          echo "Auto-detected tool: {{.TOOL_FINAL}}"

  show-results:
    desc: "Display build results"
    cmds:
      - cmd: |
          echo "==> Results:"
          ls -hl bin/

  help:
    desc: "Show usage"
    cmds:
      - cmd: |
          echo "Usage: task build"

# ✅ GOOD
tasks:
  # Remove these tasks entirely
  # The default task with fzf provides discovery
  # Task descriptions provide documentation
```

## R19: Remove all unnecessary output

Tasks should be silent by default. Remove color variables and progress
messages.

```yaml
# ❌ BAD
vars:
  RED: '\033[0;31m'
  GREEN: '\033[0;32m'
  YELLOW: '\033[1;33m'

tasks:
  build:
    cmds:
      - cmd: |
          echo -e "{{.GREEN}}==> Building...{{.NC}}"
          go build -o bin/app
          echo -e "{{.GREEN}}Build complete!{{.NC}}"

# ✅ GOOD
tasks:
  build:
    desc: "Build application"
    preconditions:
      - sh: which go
        msg: "Go not found"
    cmds:
      - cmd: |
          go build -o bin/app
```

## R20: Ensure all task dependencies are resolvable

All task references must be resolvable within the taskfile's context, including
proper includes for external dependencies.

```yaml
# ❌ BAD
version: '3'

tasks:
  clean:
    cmds:
      - task: utils:trash  # Fails - utils not included
        vars:
          TARGET_PATH: bin

  helper:
    cmds:
      - task: nonexistent:task  # Fails - reference doesn't exist

# ✅ GOOD
version: '3'

includes:
  utils: "../utils/Taskfile.yaml"

tasks:
  clean:
    cmds:
      - task: utils:trash  # Works - utils is included
        vars:
          TARGET_PATH: bin

  helper:
    deps: [_internal-helper]  # Works - internal task exists

  _internal-helper:
    internal: true
    cmds:
      - echo "helper"
```

## R21: Use proper platform conditionals in preconditions

Preconditions must handle platform differences using Go templating with correct
syntax for each platform.

```yaml
# ❌ BAD
tasks:
  stop-processes:
    preconditions:
      - sh: command -v pgrep || command -v ps
        msg: "Process tools not available"

# ✅ GOOD
tasks:
  stop-processes:
    preconditions:
      - sh: |
          {{if eq OS "windows"}}
            powershell -NoProfile -Command "try { Get-Command Get-Process -ErrorAction Stop; exit 0 } catch { exit 1 }"
          {{else}}
            command -v pgrep >/dev/null 2>&1 || command -v ps >/dev/null 2>&1
          {{end}}
        msg: "Process management tools not available"
```

## Common Variables Pattern

```yaml
vars:
  BINARY_EXT: '{{if eq OS "windows"}}.exe{{else}}{{end}}'
  GIT_COMMIT:
    sh: git rev-parse HEAD
  GIT_DIRTY:
    sh: |
      {{if eq OS "windows"}}
        powershell -NoProfile -Command 'if (git status --porcelain) { "+CHANGES" } else { "" }'
      {{else}}
        test -n "$(git status --porcelain)" && echo "+CHANGES" || echo ""
      {{end}}
```

## Testing Checklist

- \[ ] Default task works: `task`
- \[ ] All tasks have preconditions
- \[ ] All commands use literal style `|`
- \[ ] Platform commands are split
- \[ ] File operations use utils:trash
- \[ ] No repeated env vars across tasks
- \[ ] Complex commands use internal tasks
- \[ ] No echo-only tasks (R18)
- \[ ] No color variables or unnecessary output (R19)
- \[ ] All task dependencies resolvable (R20)
- \[ ] Platform-aware preconditions (R21)
- \[ ] Each task runs individually
