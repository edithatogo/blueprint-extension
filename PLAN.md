# Plan

Goal: Adapt the existing Gemini CLI Blueprint extension so it can also run as a Qwen Code extension and as an MCP server, while remaining closely aligned with the upstream workflow and benefiting from upstream updates.

## Steps
1. **Understand the current extension:** Review the Gemini-specific extension manifest (`gemini-extension.json`), command definitions under `commands/`, and supporting docs (`README.md`, `blueprint.md`) to catalog behaviors, entry points, and any Gemini-specific assumptions.
2. **Define target platforms and constraints:** Document expectations for a Qwen Code extension and for an MCP server (APIs, packaging, configuration, auth, transport). Capture any compatibility constraints (e.g., command parity, markdown outputs like `PLAN.md`, `TODO.md`).
3. **Design a shared core:** Propose a common abstraction layer (shared workflow logic, markdown file management, state machine) that can be reused by both the Qwen extension and the MCP server to minimize divergence from upstream and simplify syncing changes.
4. **Plan integration adapters:** Specify adapters/wrappers for Qwen and MCP that translate platform-specific events/commands into the shared core, including error handling, logging, and user approval flows.
5. **Upstream alignment strategy:** Establish how to consume upstream changes (e.g., keep Gemini-oriented files as source of truth, factor shared logic into neutral modules, document a sync checklist) so downstream targets stay current.
6. **Implementation tasks and sequencing:** Break work into milestones (bootstrap shared core, port commands, add platform manifests/config, test flows) and map them to concrete tasks with owners/checkpoints.
7. **Validation and testing approach:** Outline testing for each platform (unit tests on shared core, simulated command runs for Qwen, MCP protocol tests), plus CI considerations if applicable.
8. **Documentation deliverables:** Create `requirements.md`, `design.md`, and `tasks.md` summarizing platform requirements, architecture, and actionable task list to guide development.
9. **Review and approval:** Share the plan and accompanying documents for feedback before implementation; adjust based on stakeholder input.
