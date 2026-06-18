# Backlog

| ID | Priority | Status | Milestone | Title | Depends on | Owner/worktree | Spec |
|----|----------|--------|-----------|-------|------------|----------------|------|
| CR-0001 | P0 | INTEGRATED | M0 | Initialize repository | - | - | - |
| CR-0002 | P0 | READY | M0 | Create agentic control plane | CR-0001 | - | playbook §3, §4 |
| CR-0003 | P0 | READY | M0 | Verify obra/superpowers loads | CR-0001 | - | - |
| CR-0004 | P0 | READY | M0 | Configure OpenCode agents | CR-0001 | - | .opencode/agents/*.md |
| CR-0005 | P1 | READY | M0 | Add worktree helper scripts | CR-0002 | - | scripts/agent/check_worktree.py |
| CR-0006 | P1 | READY | M0 | Add task validation script | CR-0002 | - | scripts/agent/validate_task.py |
| CR-0007 | P1 | READY | M0 | Add unified verification command | CR-0006 | - | scripts/quality/verify.sh |
| CR-0008 | P1 | READY | M0 | Add baseline CI | CR-0007 | - | .github/workflows/ci.yml |
| CR-0009 | P1 | READY | M0 | Add secret and dependency scanning | CR-0008 | - | .github/workflows/security.yml |
| CR-0010 | P2 | READY | M0 | Add recovery workflow | CR-0008 | - | .github/workflows/recovery.yml |

## Legend
- DRAFT: incomplete task spec
- READY: valid, unblocked, selectable
- CLAIMED: assigned to a worktree
- IN_PROGRESS: implementation started
- IN_REVIEW: awaiting review
- CHANGES_REQUESTED: repair cycle
- VERIFIED: all gates passed
- INTEGRATED: merged to main
- BLOCKED: cannot proceed
- CANCELLED: no longer needed

## Next actions
1. Execute CR-0002 through CR-0010 in Milestone 0.
2. Begin M1 platform foundation after all M0 tasks integrate.
