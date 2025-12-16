---
description: Generate comprehensive code documentation wiki for the repository.
---

# codewiki

## Description

Generate a comprehensive documentation wiki for the codebase, including module documentation, API reference, architecture overview, and dependency graphs. Output is MkDocs-compatible Markdown.

## Inputs

- **Scope** (optional): Directory or module to document (default: entire repo).
- **Format** (optional): Output format (`mkdocs`, `github`, `standalone`). Default: `mkdocs`.
- **Depth** (optional): How deep to document (`overview`, `standard`, `detailed`). Default: `standard`.

## Steps

1. **Analyze repository structure**:
   - Identify programming languages and frameworks
   - Locate source directories
   - Find existing documentation (READMEs, docstrings)
   - Map module structure

2. **Extract documentation sources**:
   - Parse docstrings from source files
   - Read README files
   - Extract type annotations
   - Analyze function/class signatures
   - Find usage examples from tests

3. **Build module inventory**:
   ```
   For each module:
   - Name and path
   - Purpose (from docstring or README)
   - Public exports (classes, functions)
   - Dependencies (internal and external)
   ```

4. **Generate architecture overview**:
   - Identify layers/patterns
   - Map module relationships
   - Create Mermaid dependency diagram
   - Document entry points

5. **Generate API reference**:
   - List all public classes with methods
   - List all public functions
   - Include signatures, parameters, return types
   - Extract examples from docstrings/tests

6. **Document configuration**:
   - Environment variables
   - Config files and their options
   - Default values and overrides

7. **Create wiki directory structure**:
   ```bash
   mkdir -p wiki/modules wiki/api
   ```

8. **Generate wiki pages**:
   - `wiki/index.md` - Home page with overview and navigation
   - `wiki/architecture.md` - High-level design and patterns
   - `wiki/getting-started.md` - Setup and first run
   - `wiki/modules/index.md` - Module directory
   - `wiki/modules/<module>.md` - Per-module docs
   - `wiki/api/index.md` - API overview
   - `wiki/api/classes.md` - Class reference
   - `wiki/api/functions.md` - Function reference
   - `wiki/data-models.md` - Types and schemas
   - `wiki/configuration.md` - Config options
   - `wiki/dependencies.md` - Dependency graph

9. **Generate MkDocs config** (if format=mkdocs):
   ```yaml
   # wiki/mkdocs.yml
   site_name: [Repo Name] Documentation
   nav:
     - Home: index.md
     - Architecture: architecture.md
     - Getting Started: getting-started.md
     - Modules:
       - Overview: modules/index.md
       - ...
     - API Reference:
       - Overview: api/index.md
       - Classes: api/classes.md
       - Functions: api/functions.md
     - Data Models: data-models.md
     - Configuration: configuration.md
     - Dependencies: dependencies.md
   ```

10. **Validate wiki**:
    - Check for broken internal links
    - Verify Mermaid diagrams render
    - Ensure all public APIs are documented

11. **Present summary** with:
    - Pages generated
    - Modules documented
    - API coverage statistics
    - Any gaps or warnings

## Output

```
wiki/
├── index.md
├── architecture.md
├── getting-started.md
├── modules/
│   ├── index.md
│   └── <module>.md
├── api/
│   ├── index.md
│   ├── classes.md
│   └── functions.md
├── data-models.md
├── configuration.md
├── dependencies.md
└── mkdocs.yml (if format=mkdocs)
```

## Examples

```
/codewiki
/codewiki src/
/codewiki depth=detailed
/codewiki format=github
```

## Integration

After generation:
- **MkDocs**: `cd wiki && mkdocs serve`
- **GitHub**: Wiki pages are ready for GitHub wiki or Pages
- **Standalone**: Open `wiki/index.md` in any Markdown viewer
