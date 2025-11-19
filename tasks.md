# Tasks: Adapting Blueprint to Qwen Code & MCP

## 1) Discovery & Preparation
- [ ] **Catalog Gemini behaviors**: Map each existing command (under `commands/` and `gemini-extension.json`) to its workflow steps, required inputs, and markdown side effects. Capture Gemini-specific prompts/strings to parameterize later.
- [ ] **Qwen requirements**: Collect Qwen Code extension manifest schema, permission requirements, and command binding patterns; record any differences from Gemini (e.g., event names, config keys, output formatting).
- [ ] **MCP requirements**: Document MCP transport, request/response schema, error handling, and auth/permission expectations. Identify whether streaming or async responses are needed for long actions.
- [ ] **Environment assumptions**: Decide baseline runtime(s) and packaging approach for the shared core so all platforms can consume it (e.g., node module vs. Python package vs. vendored code path).

## 2) Shared Core Creation
- [ ] **Extract reusable logic**: Lift workflow logic (plan/define/implement/test/refine/resume/clear), markdown helpers, and approval messaging into a platform-neutral module or package path.
- [ ] **Configuration layer**: Add a small config mechanism (per-platform strings, paths, and permission prompts) so adapters can override UX without duplicating logic.
- [ ] **Contract definition**: Define clear input/output interfaces for the core functions that adapters will call (structured request/response objects, error shapes).
- [ ] **Unit tests**: Cover core operations and markdown IO to ensure parity with current Gemini behavior.

## 3) Qwen Code Adapter
- [ ] **Manifest scaffolding**: Draft a Qwen extension manifest that mirrors Gemini commands/permissions and references the shared core entrypoints.
- [ ] **Command bindings**: Implement Qwen-facing command handlers that normalize inputs, invoke the shared core, and render responses in Qwen-friendly format (messages, markdown paths, approvals).
- [ ] **Validation**: Add smoke tests or an example harness showing end-to-end execution of key commands (plan/define/implement) against the core.

## 4) MCP Server Adapter
- [ ] **Server scaffold**: Create an MCP server entrypoint exposing RPC methods for each workflow action with consistent routing/logging.
- [ ] **Request/response mapping**: Translate MCP requests into core inputs, then serialize core results/errors per MCP protocol (including streaming if required).
- [ ] **Integration tests**: Provide a test harness or script that exercises each MCP endpoint end-to-end, asserting response structure and artifact updates.

## 5) Upstream Alignment & Release
- [ ] **Sync checklist**: Document how to consume upstream Gemini changes—files to review, core touchpoints, and how to regenerate manifests/adapters.
- [ ] **Developer docs**: Add setup/run instructions for the Qwen extension and MCP server (local dev, sample commands, troubleshooting).
- [ ] **Versioning & release**: Define how versions track upstream (e.g., tags or notes), and outline release notes for multi-platform support.
