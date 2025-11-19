# Design: Multi-Platform Blueprint Extension

## Overview
Create a platform-neutral core for the Blueprint workflow, with thin adapters for Gemini (upstream), Qwen Code, and an MCP server. The core handles workflow logic and markdown artifacts; adapters map platform-specific events, manifests, and IO to the core.

## Architecture
- **Core Workflow Module (new):** Encapsulates command behaviors (research/plan/define/implement/test/refine/resume/clear), markdown read/write helpers, and approval messaging templates. Lives in a neutral path consumable by all platforms.
- **Platform Adapters:**
  - **Gemini Adapter (existing):** Continues to use `gemini-extension.json` and `commands/` TOML specs; rewire command execution to call shared core where possible.
  - **Qwen Adapter (new):** Provides a Qwen extension manifest plus command bindings that invoke the shared core. Handles Qwen-specific permission/config syntax and output formatting.
  - **MCP Server (new):** Implements an MCP server exposing RPC methods for each workflow action. Translates requests/responses to/from core, handling JSON-RPC transport, error codes, and streaming if supported.
- **Shared Assets:** Markdown templates and docs (`PLAN.md`, `TODO.md`, `requirements.md`, `design.md`, `tasks.md`) remain common across platforms.

## Data Flow
1. Platform event/command triggers adapter entrypoint.
2. Adapter normalizes input (goal text, context paths, user approvals) and calls the corresponding core function.
3. Core updates markdown artifacts and returns structured response (status, messages, file paths) plus any prompts needed.
4. Adapter renders response according to platform conventions (e.g., Qwen message formatting, MCP JSON-RPC result object).

## Upstream Sync Strategy
- Treat Gemini implementation as upstream; extract reusable logic into the core without altering user-facing behaviors.
- Keep platform manifests/configs separate to reduce merge conflicts; place shared code in a neutral directory referenced by all adapters.
- Document a sync checklist (e.g., rerun tests, regenerate manifests) to apply upstream changes to Qwen and MCP layers.
- Prefer composition over forking: adapters import core modules rather than copy-pasting command logic.

## Testing Approach
- **Unit Tests:** Core workflow functions and markdown IO.
- **Integration Smoke Tests:** Qwen command invocations against the shared core; MCP RPC calls exercising each workflow action.
- **Compatibility Checks:** Ensure generated markdown artifacts and prompts match upstream expectations.
- **CI Hooks:** Optional scripts to run the above suites across platforms.

## Open Questions / Risks
- Exact Qwen extension manifest format and permission model—may need sample scaffolding.
- MCP transport details (streaming, auth) and whether long-running actions require async handling.
- How to package/distribute shared core for use across extension ecosystems (e.g., npm/pypi/module path).
