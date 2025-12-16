---
description: Visualize module dependencies in the codebase.
---

# dependency-graph

## Description

Analyze and visualize module dependencies in the codebase. Identifies import relationships, circular dependencies, and architectural layers.

## Inputs

- **Scope** (optional): Directory or file to analyze (default: entire repo).
- **Format** (optional): Output format (`text`, `mermaid`, `dot`).

## Steps

1. **Identify language and import patterns**:
   - Python: `import`, `from ... import`
   - JavaScript/TypeScript: `import`, `require`
   - Go: `import`
   - Rust: `use`, `mod`

2. **Scan for dependencies**:
   ```bash
   # Python example
   rg "^import |^from .* import" --type py -l
   
   # JavaScript/TypeScript
   rg "^import |require\(" --type js --type ts -l
   ```

3. **Build dependency graph**:
   - Parse import statements
   - Map: source file → imported modules
   - Distinguish: internal vs external dependencies
   - Identify: circular dependencies

4. **Analyze architecture**:
   - Identify layers (e.g., api → service → repository)
   - Find highly-coupled modules
   - Detect dependency anti-patterns

5. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

6. **Write report** to `reports/dependency_graph_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Dependency Graph
   
   Generated: [timestamp]
   Scope: [analyzed path]
   
   ## Summary
   - X modules analyzed
   - Y internal dependencies
   - Z external dependencies
   - Circular dependencies: [count]
   
   ## Dependency Diagram
   ```mermaid
   graph TD
     A[module_a] --> B[module_b]
     B --> C[module_c]
     C --> A
   ```
   
   ## Circular Dependencies
   - module_a → module_b → module_c → module_a
   
   ## Highly-Coupled Modules
   | Module | Dependents | Dependencies |
   |--------|------------|--------------|
   | ... | ... | ... |
   
   ## External Dependencies
   | Package | Used By |
   |---------|---------|
   | ... | ... |
   
   ## Architectural Layers
   [description of identified layers]
   
   ## Recommendations
   - [suggestions for improving modularity]
   ```

7. **Present summary** with key findings and report path.

## Output

- `reports/dependency_graph_<YYYYMMDD-HHMM>.md`

## Examples

```
/dependency-graph
/dependency-graph src/
/dependency-graph format=mermaid
```
