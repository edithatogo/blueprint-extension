---
description: Trace a call path or data flow for a symbol, endpoint, or file.
---

# trace

## Description

Trace the call chain and data flow for a specific symbol, function, class, or endpoint. Produces a detailed report showing callers, callees, and file transitions.

## Inputs

- **Target** (required): One of:
  - Symbol name (function, class, method)
  - File path with optional line hint
  - Endpoint or route pattern
- **Direction** (optional): "callers" (who calls this), "callees" (what this calls), or "both" (default: both)

## Steps

1. **Parse the target**: Use text after `/trace` as the symbol/file to trace. Ask for clarification if ambiguous.

2. **Locate the definition**:
   - Search for the symbol in the codebase
   - If multiple matches, list them and ask user to clarify
   - Open the definition file and identify the exact location (file + line range)

3. **Find callers** (upstream):
   - Search for references to the symbol
   - For each caller, note: file, function/method, line number
   - Continue up the chain until reaching entry points or reasonable depth

4. **Find callees** (downstream):
   - Read the symbol's implementation
   - Identify function/method calls made
   - Follow each call to its definition
   - Continue down the chain until reaching leaf functions or reasonable depth

5. **Document the call chain**:
   - Create a text-based diagram showing the flow
   - Note file boundaries and module transitions
   - Highlight any async/callback patterns

6. **Create the reports directory** if it doesn't exist:
   ```bash
   mkdir -p reports
   ```

7. **Write the report** to `reports/trace_<symbol>_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Trace: [Symbol Name]
   
   Generated: [timestamp]
   
   ## Target Definition
   - **Symbol**: `symbol_name`
   - **Location**: `file/path.py:L42-L67`
   - **Type**: function/class/method
   
   ## Call Chain Diagram
   ```
   entry_point()
     → middleware()
       → TARGET_SYMBOL()
         → helper_a()
         → helper_b()
           → database_call()
   ```
   
   ## Upstream (Callers)
   | Caller | Location | Context |
   |--------|----------|---------|
   | ...    | ...      | ...     |
   
   ## Downstream (Callees)
   | Callee | Location | Purpose |
   |--------|----------|---------|
   | ...    | ...      | ...     |
   
   ## Data Flow
   [describe how data transforms through the chain]
   
   ## File Transitions
   [list module/file boundaries crossed]
   
   ## Notes
   [observations about patterns, coupling, complexity]
   ```

8. **Present a summary** showing the main call path and report location.

## Output

- `reports/trace_<symbol>_<YYYYMMDD-HHMM>.md`

## Example

```
/trace handleRequest
/trace src/auth/login.py:authenticate
```
