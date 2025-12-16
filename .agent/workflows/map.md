---
description: Create or refresh a repository architecture map quickly.
---

# map

## Description

Create a quick architectural overview of the repository, documenting its structure, tech stack, entry points, and key files.

## Inputs

None required.

## Steps

1. **Scan directory structure**:
   - List top-level directories and their purposes
   - Note any non-standard organization

2. **Identify the tech stack**:
   - Languages (by extension and file signatures)
   - Frameworks (look for config files: `package.json`, `requirements.txt`, `go.mod`, `Cargo.toml`, etc.)
   - Build tools (`Makefile`, `justfile`, `tox.ini`, `pyproject.toml`, etc.)
   - Test infrastructure (test directories, test configs)

3. **Locate entry points**:
   - Main executable files
   - CLI commands
   - HTTP endpoints (if web app)
   - Configuration entry points

4. **Identify key files**:
   - README, CONTRIBUTING, AGENTS.md
   - Core configuration files
   - Primary source files

5. **Create the reports directory** if it doesn't exist:
   ```bash
   mkdir -p reports
   ```

6. **Write the map** to `reports/codebase_map_<YYYYMMDD-HHMM>.md` with:
   ```markdown
   # Codebase Map: [Repo Name]
   
   Generated: [timestamp]
   
   ## Directory Structure
   [tree-like overview]
   
   ## Tech Stack
   - **Languages**: ...
   - **Frameworks**: ...
   - **Build Tools**: ...
   - **Test Infrastructure**: ...
   
   ## Entry Points
   | Entry Point | Location | Description |
   |-------------|----------|-------------|
   | ...         | ...      | ...         |
   
   ## Key Files
   | File | Purpose |
   |------|---------|
   | ...  | ...     |
   
   ## Configuration Files
   [list with brief descriptions]
   
   ## Notes
   [any observations about structure, conventions, or unusual patterns]
   ```

7. **Present a summary** in chat with path to the full map.

## Output

- `reports/codebase_map_<YYYYMMDD-HHMM>.md`

## Example

```
/map
```

Produces: `reports/codebase_map_20251216-2350.md`
