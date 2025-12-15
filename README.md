# Blueprint Extension

A powerful workflow engine for **Google Antigravity**, designed to structure your engineering process from research to implementation.

## 🚀 Features

- **Structured Workflows**: Follow a proven **RESEARCH → PLAN → DEFINE → IMPLEMENT → TEST** loop.
- **Stateful Context**: Keeps track of your progress in `PLAN.md`, `TODO.md`, and `ACT.md`.
- **Agent Integration**: Seamlessly integrates with Antigravity's agent capabilities.

## 📦 Installation

Install directly from the repository:

```bash
gemini extensions install https://github.com/edithatogo/blueprint-extension.git --auto-update
```

## 🛠 Usage

Once installed, use the slash commands to drive your workflow:

- **/blueprint-research** `[topic]`: Gather context and information.
- **/blueprint-plan** `[goal]`: Generate a high-level plan.
- **/blueprint-define**: Break down the plan into actionable tasks.
- **/blueprint-implement**: Execute the tasks.
- **/blueprint-test**: Verify the results.

## 📂 Project Structure

- `.agent/rules/`: Custom agent rules.
- `.agent/workflows/`: Workflow definitions.
- `commands/`: Extension command configurations.

## 🤝 Contributing

1. Fork the repository.
2. Create a feature branch.
3. Submit a Pull Request.
