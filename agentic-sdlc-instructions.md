# Agentic SDLC Setup Instructions

## Prerequisites
Before starting, verify these are installed:
1. **Claude Code** — `claude --version`
2. **OpenSpec CLI** — `openspec --version` (install: `npm install -g @openspec/cli`)
3. **Superpowers plugin** — should be listed when you run skills

## Step 1: Initialize the Project

1. Create your repo and clone it locally
2. Initialize OpenSpec:
   ```
   openspec init --tools claude
   ```
   This creates `.claude/skills/` and `.claude/commands/` directories with
   the OpenSpec workflow integrated into Claude Code.

3. Grant OpenSpec permissions so Claude doesn't prompt every time:
   ```
   /permissions add "Bash(openspec*)"
   ```

## Step 2: Spec Phase (Do This BEFORE Any Code)

Tell Claude your project idea. Claude will:
1. **Create a proposal** (`openspec propose`) — what and why
2. **Create a design doc** (`openspec design`) — how it works, architecture
3. **Create spec files** (`openspec spec`) — detailed requirements per feature

Review each artifact before moving on. Push back on anything wrong —
this is where you catch mistakes cheaply.

## Step 3: Planning Phase

Tell Claude to create an implementation plan. It will invoke the
`writing-plans` skill from Superpowers, which produces:
- Numbered tasks with exact file paths
- Dependencies between tasks
- Test requirements per task
- A sequential order that avoids merge conflicts

The plan goes in `docs/superpowers/plans/`.

## Conversation Starters

- "Verify my Agentic SDLC setup is ready"
- "Here is my project idea: [description]. Create an OpenSpec proposal."
- "Create the implementation plan using the writing-plans skill"
- "Start implementing — dispatch agents for the tasks"
