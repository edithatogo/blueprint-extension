---
description: Generate focused API reference documentation.
---

# apidocs

## Description

Generate focused API reference documentation for a codebase. Lighter than `/codewiki`, focusing only on public interfaces, signatures, and usage examples.

## Inputs

- **Scope** (optional): Directory or module to document (default: entire repo).
- **Format** (optional): Output format (`markdown`, `html`, `json`).
- **Include** (optional): What to include (`classes`, `functions`, `types`, `all`).

## Steps

1. **Scan for public APIs**:
   - Public classes and methods
   - Exported functions
   - Type definitions
   - Constants and enums

2. **Extract documentation**:
   - Docstrings/JSDoc
   - Type annotations
   - Default values
   - Example usage

3. **Organize by module**:
   ```
   For each module:
   - Module description
   - Classes with methods
   - Functions
   - Types/Interfaces
   - Constants
   ```

4. **Generate cross-references**:
   - Link types to definitions
   - Link methods to classes
   - Link examples to implementations

5. **Create output directory**:
   ```bash
   mkdir -p docs/api
   ```

6. **Generate documentation**:
   
   ### docs/api/index.md
   ```markdown
   # API Reference
   
   Generated: [timestamp]
   
   ## Modules
   | Module | Description |
   |--------|-------------|
   | [auth](auth.md) | Authentication utilities |
   ```
   
   ### docs/api/<module>.md
   ```markdown
   # module_name
   
   > Module description
   
   ## Classes
   
   ### ClassName
   > Class description
   
   #### Constructor
   ```python
   ClassName(param: Type = default)
   ```
   
   #### Methods
   | Method | Description |
   |--------|-------------|
   | `method_name(args)` | Brief description |
   
   ## Functions
   
   ### function_name
   ```python
   def function_name(param: Type) -> ReturnType
   ```
   > Description
   
   **Parameters:**
   - `param` (Type): Description
   
   **Returns:** ReturnType - Description
   
   **Example:**
   ```python
   result = function_name(value)
   ```
   
   ## Types
   
   ### TypeName
   ```python
   TypeName = Union[A, B]
   ```
   ```

7. **Validate output**:
   - Check for missing docstrings
   - Verify cross-references
   - List undocumented items

8. **Present summary**:
   - Classes documented
   - Functions documented
   - Coverage percentage
   - Missing documentation

## Output

```
docs/api/
├── index.md
├── <module1>.md
├── <module2>.md
└── ...
```

## Examples

```
/apidocs
/apidocs src/lib/
/apidocs include=classes,functions
```

## Comparison with /codewiki

| Feature | /apidocs | /codewiki |
|---------|----------|-----------|
| Scope | Public APIs only | Full codebase |
| Output | `docs/api/` | `wiki/` |
| Architecture | ❌ | ✅ |
| Getting Started | ❌ | ✅ |
| Dependencies | ❌ | ✅ |
| Speed | Fast | Comprehensive |
