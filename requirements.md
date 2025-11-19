# Requirements: Qwen Code & MCP Adaptation

## Functional
- Preserve Blueprint workflow commands (research, plan, define, implement, test, refine, resume, clear) with consistent behaviors and markdown outputs (`PLAN.md`, `TODO.md`, `ACT.md`, etc.).
- Allow the extension to run in Qwen Code with equivalent command triggers, prompts, and user-approval steps.
- Provide an MCP server exposing endpoints that mirror the workflow operations (e.g., create plan, define tasks, run implementation steps, fetch/update markdown artifacts).
- Support resumable workflows by reading/writing the same markdown artifacts across platforms.
- Offer clear user prompts/responses suited to each platform while keeping core business logic identical.

## Compatibility & Upstream Alignment
- Keep Gemini CLI implementation as the upstream source of truth; shared logic should be platform-agnostic to ease syncing.
- Minimize duplication by extracting reusable workflow code into common modules consumable by Gemini, Qwen, and MCP entrypoints.
- Document a sync process so updates from the upstream Gemini repo can be merged without rewriting platform adapters.
- Ensure configuration/manifests for each platform are isolated but reference the same shared logic and artifacts.

## Technical & Operational
- Define Qwen extension manifest/spec equivalent to `gemini-extension.json` (naming, triggers, permissions, outputs).
- Specify MCP server transport (likely JSON-RPC over stdin/stdout) and payload schemas for workflow operations.
- Logging/telemetry should remain lightweight and optional; errors must be surfaced in platform-appropriate formats.
- Provide testing strategy: unit tests for shared core, integration stubs for Qwen and MCP command flows.
- Establish versioning approach (e.g., semantic tags) and changelog notes for multi-platform releases.

## Documentation & Developer Experience
- Deliver design and task breakdown docs that describe architecture, adapters, and sync steps.
- Include setup instructions for running Qwen extension and MCP server locally for validation.
- Clarify any platform-specific limitations or feature gaps compared to Gemini.
