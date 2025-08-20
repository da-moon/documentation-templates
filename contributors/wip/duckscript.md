1. **Use arrays for command arguments**:
   ```duckscript
   args = array
   array_push ${args} "check"
   exec --fail-on-error cargo %{args}
   ```

2. **Avoid string concatenation for commands**:
   ```duckscript
   # BAD: cmd = concat "cargo " ${command}
   # GOOD: Use arrays and %{} expansion
   ```

3. **Handle empty environment variables**:
   ```duckscript
   value = get_env VAR_NAME
   if not is_empty ${value}
       # use value
   end
   ```


