# AI Playbook

Multi-agent workflow (Planner → Developer → Security → DevOps) for building apps with AI coding agents. See [AGENTS.md](AGENTS.md).

## Install

Run in your project root to write `AGENTS.md` and `skills/` from [jinomdeveloper/ai-playbook](https://github.com/jinomdeveloper/ai-playbook):

```bash
curl -fsSL https://github.com/jinomdeveloper/ai-playbook/archive/refs/heads/main.tar.gz \
  | tar -xz --strip-components=1 ai-playbook-main/AGENTS.md ai-playbook-main/skills
mkdir -p workspace
```

Re-run to update. Existing `AGENTS.md` and skill files with the same name are overwritten.

Using Claude Code? It reads `CLAUDE.md`, so link it:

```bash
ln -s AGENTS.md CLAUDE.md
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
