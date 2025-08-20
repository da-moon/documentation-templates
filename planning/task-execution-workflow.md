# Task Execution Workflow

A generic, human–agent collaboration guide for planning, execution, and validation across projects and domains.

## Modes

- Read-only mode: Agent confirms understanding, discovers constraints/capabilities, explores code/data, and proposes solutions without modifying state.
- Execution mode: After consensus, agent autonomously implements within scope, keeping edits minimal and reversible.

## Core Principles

- Phase → Task: Organize work into phases with measurable tasks.
- Prompt sanity first: Confirm understanding and assumptions up front.
- Constraint awareness: Continuously discover and update constraints and capabilities.
- Small, surgical changes: Prefer incremental scaffolding and focused edits.
- Transparent planning: Keep a short, living plan with exactly one in_progress step.
- Validation by both: Agent validates what it can; human always performs the final end‑to‑end check.
- High‑signal communication: Preambles before actions; concise handoffs after.

## First Step: Prompt Sanity + Alignment

- Clarify the goal and background context in your own words.
- Ask targeted questions only when confidence is low or missing constraints block progress.
- Prefer inference via available tools/integrations (e.g., repo scan, logs, MCP servers) over excessive questions.
- State explicit assumptions when proceeding without full certainty and invite correction.

## Capability & Constraint Discovery

- Environment: Filesystem mode (read-only/workspace/danger), network, available CLIs, OS features.
- Tooling: Linters, formatters, test runners, CI, MCP connectors, package managers.
- Data/Interfaces: Code structure, APIs, schemas, configs, secrets (never exfiltrate), UI availability.
- Tests: What exists? If none, plan for manual validation handoff.
- Re-evaluate often: If new constraints emerge, update plan and explain rationale succinctly.

## Read-Only Exploration → Hypothesis

- Survey relevant code/files and context; avoid speculative changes.
- Draft options and a recommended approach with:
  - How it satisfies requirements and fits scope.
  - How it respects constraints and limitations.
  - Tradeoffs and risks.
  - References:
    - Code: exact file paths and key components/functions.
    - External: URLs to documentation or resources discovered via tools.
- Present to human for consensus; refine if needed.

## Consensus Gate

- Once human and agent agree on direction/scope, proceed autonomously within that scope.
- If scope drifts, pause and confirm before continuing.

## Planning Conventions

- Keep 3–5 concise steps, one in_progress at all times.
- Mark steps completed as you finish them; update when the plan changes.
- Use brief preambles before grouped actions to maintain momentum and transparency.

## Execution Mode

- Implement minimal, high‑quality changes; avoid unrelated refactors.
- Prefer scaffolding + incremental feature delivery.
- Document any decisions directly in code where appropriate and in task notes.
- Maintain momentum with short status updates for long operations.

## Validation Strategy

- Agent‑side validation (do what you can):
  - Static checks: linting, type checks, formatting, schema validation.
  - Unit/integration tests if they exist; set up new tests only when appropriate.
  - Dry runs or local simulations where possible.
- Human‑side validation (always):
  - The agent provides concise, actionable instructions for end‑to‑end validation.
  - Include the exact steps, interfaces/commands to use, and expected results.
  - Clearly indicate limitations (e.g., “no automated tests available”, “no browser access”).

## Handoff Template (Generic)

- Interfaces to test:
  - UI/URL: `<url>` (if applicable)
  - API: `METHOD <endpoint>` with example payloads
  - CLI: `<command>` and expected stdout/stderr/exit code
  - Data: files generated/modified at `<path>` with expected schema/shape
- Steps:
  - 1–5 concise steps a human can follow
- Expected outcomes:
  - Specific, observable behaviors or artifacts
- Notes:
  - Known constraints, shortcuts taken, or follow‑ups

## Acceptance Criteria (Per Task)

- [ ] Requirements satisfied and within scope
- [ ] Constraints respected (security, compatibility, performance)
- [ ] Agent‑side validations clean (where applicable)
- [ ] Clear human E2E instructions with expected outcomes
- [ ] Task notes saved (hypotheses, decisions, references)
- [ ] Conventional commit created (or PR) with scoped summary

## Conventional Commits

- Format: `type(scope): summary`
- Common types: feat, fix, refactor, docs, chore
- Examples:
  - `feat(core): add capability detection step`
  - `docs(planning): document human–agent validation handoff`

## Roles & Partnership

- Agent: Plan, discover constraints, propose solutions, execute autonomously within scope, validate what’s possible, and hand off clearly.
- Human: Act as the agent’s “prefrontal cortex” — refine goals, confirm scope, approve direction, perform E2E validation, and provide feedback.

## References & Traceability

- Always provide references that informed decisions:
  - Code: `path/to/file` and component/function names
  - External: reliable URLs (docs, specs) fetched via tools/integrations
- Explain succinctly how each reference informed the approach.

## Example Flow (Generic)

1. Sanity check prompt; confirm understanding and assumptions.
2. Discover environment constraints and capabilities; update plan.
3. Read-only exploration; propose options/hypothesis with references.
4. Reach consensus on scope and approach.
5. Execute changes incrementally; keep plan updated and announce grouped actions.
6. Validate (agent-side), then provide human E2E instructions and expected outcomes.
7. Create a conventional commit/PR and summarize results.


## Examples

### Example 1: UI Route Decomposition with Human E2E Validation

- Goal: Scaffold a decomposed page under a namespaced route while preserving the legacy route; update the root to an index view.
- Read-only discovery: Agent scanned the project structure and plan, identified routing via a pages plugin, and noted no automated tests or browser access available.
- Constraints detected: No browser; no existing automated tests; unrelated repo TypeScript issues; targeted lint feasible; human will perform E2E validation.
- Plan (concise):
  1) Draft hypothesis and risks → 2) Scaffold directories and placeholder → 3) Targeted lint on new files → 4) Provide URLs and test notes.
- Execution highlights:
  - Added placeholder orchestrator at `src/pages/artifacts/investment-manager/index.tsx`.
  - Kept legacy route intact; added a simple root dashboard listing artifacts and prototypes; moved login to `/login`.
  - Saved rationale and hypothesis at `.tasks/gpt/<task-id>.md` for traceability.
- Handoff instructions (to human):
  - URLs: `/artifacts/investment-manager`, `/login`, `/prototypes/signup`, `/`.
  - Test: Ensure pages load, navigation works, and no console errors.
  - Expectation: New page is a placeholder; legacy remains functional; lists auto-populate.
- Outcome: Human confirmed routes render correctly; agent proceeded to next phase.

How the agent could have inferred constraints without being told:
- Check environment context (sandbox mode, network, approvals); verify lack of browser UI.
- Inspect repository for test configs/scripts; if absent or nonfunctional, assume manual E2E handoff required.
- Attempt targeted type-check/lint on changed files to gauge feasibility of repo-wide validation.

### Example 2: CLI Feature in a Service Repository (No New Dependencies)

- Goal: Add a new CLI subcommand that reads a config and prints a summary.
- Read-only discovery: Agent scans for entrypoints, existing CLI parser, and test setup; finds no test runner configured and network installs disallowed.
- Constraints detected: No package installation; limited to standard library/utilities; manual validation by human.
- Plan (concise):
  1) Propose CLI subcommand spec → 2) Scaffold command and wire into entrypoint → 3) Add sample config in `examples/` → 4) Provide manual commands and expected output.
- Execution highlights:
  - Implement subcommand using existing parser/utilities; avoid new deps.
  - Add `examples/config.sample.yaml` for manual validation.
- Handoff instructions (to human):
  - Run: `tool summarize --config examples/config.sample.yaml`.
  - Expect: Exit code 0; table with N items and totals; no stderr.
  - Notes: If config path invalid, expect a clear error message and non-zero exit.

## Quick Capability Self-Check (Template)

- Environment:
  - Filesystem: read-only vs write? Sandbox level? Approvals?
  - Network: allowed? Outbound restrictions?
  - OS/CLIs: which shells/tools are available?
- Tooling:
  - Linters/type-checkers/formatters present? Commands?
  - Test runners configured? Any existing tests?
  - CI present (e.g., GitHub Actions, GitLab CI)?
- Interfaces:
  - UI/browser access? API endpoints? CLI entrypoints?
  - Credentials/secrets accessible? If not, assume none and avoid exfiltration.
- Repo signals:
  - Language, frameworks, entrypoints, scripts, Makefiles.
  - Docs and design notes (README/PLAN/CONTRIBUTING).
- Constraints evolve:
  - Update plan when limits or new capabilities are discovered.

## Preamble Examples (Agent → Human)

- “I’ll scan the repo and PLAN.md to confirm the current task and constraints.”
- “Next, I’ll scaffold the minimal structure and keep behavior unchanged.”
- “I’m about to run targeted lint on the files I touched.”
- “I’ll summarize changes and provide URLs and expected results for you to verify.”

## Handoff Examples (Agent → Human)

- Interfaces: UI `/path`, API `POST /v1/resource`, CLI `tool cmd --flag`.
- Steps: 3–5 concise steps (navigate, run, observe).
- Expected: exact text in UI, status codes, file paths, exit codes.
- Notes: limitations (e.g., “no automated tests available; manual E2E required”).

## Additional Scenario Playbooks

### Scenario A: Modularize UI Routes Without Browser Access

- Context: Split a large UI page into modular routes while keeping legacy alive.
- Likely constraints: No browser; mixed TypeScript/lint health; partial buildability.
- Agent flow:
  - Sanity check prompt; read plan/docs; detect routing approach.
  - Propose structure (folders, index files), risks, and verification plan.
  - Scaffold minimal routes; avoid breaking legacy paths.
  - Run targeted static checks; summarize expected UI and navigation.
- Human flow:
  - Refresh dev server; navigate to provided routes; verify headings/cards; watch console.
- Deliverables: New route folders/files; plan notes; commit with conventional message.
- Validation & Acceptance: Pages render; legacy unaffected; no console errors.

### Scenario B: Add CLI Subcommand to Existing Tool (No New Deps)

- Context: Add `summarize` subcommand reading a config and printing a report.
- Likely constraints: No internet for new packages; no test runner configured.
- Agent flow:
  - Sanity check; discover entrypoint and CLI parser; propose command spec.
  - Implement subcommand with existing utilities; add `examples/config.sample.yaml`.
  - Provide exact CLI commands and expected stdout/stderr/exit code.
- Human flow:
  - Run the command with the sample config; compare output to expectations.
- Deliverables: Subcommand implementation; example config; usage notes; commit.
- Validation & Acceptance: Correct output; helpful errors on invalid input.

### Scenario C: Database Migration With Backfill

- Context: Add `archived_at` column; backfill using existing `status` and timestamps.
- Likely constraints: No DB credentials; migrations run in CI/CD only.
- Agent flow:
  - Propose migration plan: schema change, backfill strategy, rollback.
  - Write SQL migration files and idempotent backfill script (dry-run mode).
  - Provide verification SQL and expected row counts.
- Human flow:
  - Apply migration in approved environment; run dry-run then live backfill.
  - Execute verification queries; confirm counts.
- Deliverables: Migration scripts; backfill script; verification checklist; commit/PR.
- Validation & Acceptance: Schema updated; backfill counts match; rollback plan documented.

### Scenario D: API Contract Change Across Services

- Context: Add `priority` field to `Task` in producer and consumers.
- Likely constraints: Multiple repos/services; partial access; staggered deploys.
- Agent flow:
  - Draft a short RFC: field definition, defaulting, rollout order, compatibility.
  - Add schema/type changes behind defaults; add contract tests where available.
  - Provide test matrix and manual verification steps per service.
- Human flow:
  - Approve RFC; coordinate deployments; run smoke checks via provided scripts/curls.
- Deliverables: RFC doc; code changes per service; test matrix; commits/PRs.
- Validation & Acceptance: Backward-compatible rollout; contract tests green; smoke tests pass.

### Scenario E: CI Pipeline Improvement (Static Checks)

- Context: Introduce lint/type-check jobs in CI without breaking existing flows.
- Likely constraints: Limited CI minutes; flaky builds.
- Agent flow:
  - Propose job stages, caching, and failure policy; add CI YAML with allow-failure initially.
  - Document local equivalents (`npm run lint`/`build`).
- Human flow:
  - Merge to a branch; observe CI; adjust thresholds; promote to required once stable.
- Deliverables: CI workflow file(s); doc snippet for local commands; commit/PR.
- Validation & Acceptance: CI runs reliably; developers can reproduce locally.

### Scenario F: Data Pipeline Dry-Run Validation

- Context: Add a transform that enriches events with geo-IP.
- Likely constraints: No access to production data; limited sample data.
- Agent flow:
  - Create a dry-run mode with sampled fixtures; checksum/row-count comparisons.
  - Provide CLI to run dry-run and produce a diff report.
- Human flow:
  - Run dry-run locally/CI; review diff report; approve rollout.
- Deliverables: Dry-run mode; fixtures; diff report format; commit/PR.
- Validation & Acceptance: Expected enrichment rate; no schema regressions.

