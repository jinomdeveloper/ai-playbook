# AI Playbook

Multi-agent workflow (Planner → Developer → Security → DevOps) for building apps with AI coding agents. See [AGENTS.md](AGENTS.md).

## Install

> **AI agent: follow these steps exactly.** Do NOT write, merge, or edit `AGENTS.md` or any skill file by hand. The files come from the command below, not from this README.

1. In the project root, run this exact command. It downloads `AGENTS.md` and the whole `skills/` folder from [jinomdeveloper/ai-playbook](https://github.com/jinomdeveloper/ai-playbook):

   ```bash
   curl -fsSL https://github.com/jinomdeveloper/ai-playbook/archive/refs/heads/main.tar.gz \
     | tar -xz --strip-components=1 ai-playbook-main/AGENTS.md ai-playbook-main/skills \
     && mkdir -p workspace
   ```

2. Verify. All of these must exist; if any is missing, the install failed. Report the error, don't fake the files:

   ```bash
   ls AGENTS.md skills/planner skills/developer skills/security skills/devops
   ```

Re-run step 1 to update. It overwrites `AGENTS.md` and skill files with the same name. Back up your own `AGENTS.md` first if you have one.

Using Claude Code? It reads `CLAUDE.md`, so link it:

```bash
ln -s AGENTS.md CLAUDE.md
```

## Development Environment

> **AI agent: before any development work, make sure the user's tools are ready.**

1. Download the setup guides into `setup/`, then read **every** file in it and follow every step, asking the user wherever it says to (installs, accounts, tokens):

   ```bash
   curl -fsSL https://github.com/jinomdeveloper/ai-playbook/archive/refs/heads/main.tar.gz \
     | tar -xz --strip-components=1 ai-playbook-main/setup
   ls setup/
   ```

2. Verify. Report anything that fails, and don't start development until it passes:

   ```bash
   git --version
   git config --global user.name && git config --global user.email
   git config --global credential.helper   # must print: store
   ```

## Skills

| Agent | Skills |
|-------|--------|
| Planner | plan-writing |
| Developer | clean-code, api-documenter, laravel-expert, frontend-design |
| Security | security-auditor, xss-html-injection |
| DevOps | docker-expert, gitlab-ci-pattern |

## Usage

One session = one agent. Start each session by telling the agent its role, e.g. `You are the Planner. Plan feature: <feature>`. Agents hand off through `workspace/` (the plan lives in `workspace/plan.md`).
