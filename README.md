# Blueprint Rules & Workflows for Google Antigravity

This repo provides Antigravity **Workspace Rules** and **Workflows** that implement a structured engineering loop: **RESEARCH → PLAN → DEFINE → IMPLEMENT → TEST**, with optional **REFINE / RESUME / CLEAR**.

## What’s Included

- Rules: `.agent/rules/blueprint.md`
- Workflows: `.agent/workflows/*.md` (invoked as `/workflow-name`)
- Workflow state files written to your workspace: `RESEARCH.md`, `PLAN.md`, `TODO.md`, `ACT.md`, `TEST.md`

## Install (Workspace)

1. Copy `.agent/rules/` and `.agent/workflows/` into the root of the repo you want Antigravity to work in.
2. In Antigravity, open the Editor’s Agent panel → `...` → **Rules** / **Workflows** and add/enable the Workspace entries as needed.

Notes:
- Antigravity global rules live at `~/.gemini/GEMINI.md`.
- Rules and workflow files are limited to 12,000 characters each.

## Usage

Run these workflows from the Agent input box:

- `/blueprint-research <topic>` → writes `RESEARCH.md`
- `/blueprint-plan <goal>` → writes `PLAN.md` (asks for approval)
- `/blueprint-define` → writes `TODO.md` (asks for approval)
- `/blueprint-implement` → executes `TODO.md`, logs to `ACT.md`
- `/blueprint-test [instructions]` → logs to `TEST.md`
- `/blueprint-refine <feedback>` / `/blueprint-resume` / `/blueprint-clear`

## Legacy (Gemini CLI)

The original Gemini CLI extension files are still present (`gemini-extension.json`, `blueprint.md`, `commands/blueprint/`) if you want to keep using the CLI-based version.
