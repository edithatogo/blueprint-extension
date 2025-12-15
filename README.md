# Blueprint Extension

A powerful workflow engine for **Google Antigravity**, designed to structure your engineering process from research to implementation.

## 🚀 Features

- **Structured Workflows**: Follow a proven **RESEARCH → REQUIREMENTS → DESIGN → PLAN → DEFINE → IMPLEMENT → TEST** loop.
- **Stateful Context**: Keeps track of your progress in `PLAN.md`, `TODO.md`, `ACT.md`, and more.
- **Task Validation**: Ensures all tasks are completed before moving forward.
- **Backup/Archive**: Automatically archives previous workflow files when starting new work.
- **Agent Integration**: Seamlessly integrates with Antigravity's agent capabilities.

## 📦 Installation

Install directly from the repository:

```bash
gemini extensions install https://github.com/edithatogo/blueprint-extension.git --auto-update
```

## 🛠 Usage

Once installed, use the slash commands to drive your workflow:

### Discovery & Planning
- **/bp-research** `[topic]`: Gather context and information → `RESEARCH.md`
- **/bp-requirements** `[goal]`: Define user stories and acceptance criteria → `REQUIREMENTS.md`
- **/bp-design** `[feature]`: Document technical decisions → `DESIGN.md`
- **/bp-plan** `[goal]`: Generate a high-level plan → `PLAN.md`
- **/bp-define**: Break down the plan into tasks → `TODO.md`

### Execution
- **/bp-implement**: Execute tasks with validation → `ACT.md`
- **/bp-test**: Run test plan → `TEST.md`

### Iteration
- **/bp-refine** `[feedback]`: Fix failures or incorporate feedback
- **/bp-improve**: Proactively review and enhance artifacts

### Utilities
- **/bp-commit**: Commit with Conventional Commits format
- **/bp-review**: Self-review checklist before finalizing
- **/bp-branch** `[name]`: Isolate work in a new Git branch
- **/bp-resume**: Detect state and recommend next step
- **/bp-clear**: Delete workflow files (with confirmation)

## 📂 Project Structure

- `.agent/rules/`: Custom agent rules
- `.agent/workflows/`: Workflow definitions
- `commands/`: Extension command configurations

## 🤝 Contributing

1. Fork the repository.
2. Create a feature branch.
3. Submit a Pull Request.
