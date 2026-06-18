Act as the Civic Resilience OS orchestrator (GPT 5.5 High via OpenAI).

Read AGENTS.md, docs/product-spec.md, and civic_resilience_os_agentic_development_playbook.md.

Health check first:
- git status --short
- git branch --show-current
- git worktree list
- git log -5 --oneline
- Confirm main is clean and CI is green.

The repository already has: GitHub remote, branch protection, baseline CI, opencode plugins (superpowers, ponytail), context7 MCP, ui-ux-pro-max skill, and 11 agent configs. Do not recreate these.

Execute Milestone 0 autonomously in order:

CR-0002: Create agentic control plane
- Create docs/agentic/STATE.md, DECISIONS.md, QUALITY-GATES.md, RISKS.md, BLOCKERS.md, HANDOFF.md, METRICS.md
- Populate them per playbook §4

CR-0003: Verify obra/superpowers loads
- Run a skill tool invocation to list/load skills
- Record result in runs/CR-0003.md

CR-0004: Configure OpenCode agents
- Verify .opencode/agents/*.md exist and have correct model/provider routing
- Record result in runs/CR-0004.md

CR-0005: Add worktree helper scripts
- scripts/agent/check_worktree.py

CR-0006: Add task validation script
- scripts/agent/validate_task.py
- Enforce task file structure and TDD evidence

CR-0007: Add unified verification command
- scripts/quality/verify.sh
- scripts/quality/backend.sh
- scripts/quality/frontend.sh
- make verify works

CR-0008: Add baseline CI
- Update .github/workflows/ci.yml to run verify.sh
- Ensure CI passes

CR-0009: Add secret and dependency scanning
- .github/workflows/security.yml

CR-0010: Add recovery workflow
- .github/workflows/recovery.yml
- Hourly green-main check; opens P0 repair issue if red

For each task:
- Read BACKLOG.md and mark task CLAIMED
- Create worktree: git worktree add ../cro-<task-id> -b agent/<task-id>-<short-desc> main
- Dispatch planner if plan is missing
- Dispatch implementer (Kimi 2.7 Code) or frontend (MiniMax 2.7) as appropriate
- Implementer must write failing test first, prove it fails, implement, prove it passes
- Record evidence in docs/agentic/runs/<task-id>.md
- Dispatch spec reviewer (Kimi 2.7 Code) and quality reviewer (Kimi 2.7 Code)
- Route BLOCKER/MAJOR findings back to implementer
- Dispatch release manager (DeepSeek V4 Pro Max) to merge
- Update STATE.md, BACKLOG.md, HANDOFF.md, METRICS.md
- Remove worktree

Rules:
- Use TDD for every behavior change
- Never work directly on main
- Never claim success without command output
- If CI fails on a branch, fix before integrating
- If main breaks, stop and create RESTORE MAIN TO GREEN task
- If a task fails >3 times, invoke debugger (DeepSeek V4 Pro Max)
- Stop only for: blocker requiring human approval, budget exhausted, no READY work, or repeated unknown systemic failure

After CR-0010 integrates, continue to Milestone 1 platform foundation (CR-0101+).
