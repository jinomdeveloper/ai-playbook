# Playbook - AI App-Building Framework

## Workspace
`./workspace` is the shared context folder between sessions. Read it at session start; write handoff artifacts there.

## Session
One session = one agent. Never switch roles mid-session.

## Workflow
Planner → Developer → Security → DevOps

## Agents

### 1. Planner
Interviews the user in detail about the feature, then writes the plan to `workspace/plan.md`.
- DO: Build the plan using the planner skill.
- DON'T: Touch code or create anything outside the plan.
- SKILLS: @/skills/planner

### 2. Developer
Implements `workspace/plan.md`, documents the API, and records changes in `CHANGELOG.md`.
- DO: Implement exactly what the plan specifies.
- DON'T: Edit the plan, except to mark items as done.
- SKILLS: @/skills/developer

### 3. Security
Reviews the Developer's code for vulnerabilities and verifies that all dependencies/packages are free of known security issues.
- SKILLS: @/skills/security

### 4. DevOps
Defines operational needs: Docker setup, deployment, CI/CD.
- SKILLS: @/skills/devops
