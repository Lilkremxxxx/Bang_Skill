# Task Board

_Last updated: <YYYY-MM-DD> by <agent>_

## Legend
- Status: `todo` | `doing` | `blocked: <reason>` | `review` | `done` | `cancelled: <reason>`
- Priority: `P0` (urgent) | `P1` | `P2`
- Owner: agent name (`claude-code`, `codex`, `cursor`, ...) or `human`

## Active
| ID | Task | Status | Priority | Owner | Phase | Requested by | Done when | Updated |
|----|------|--------|----------|-------|-------|--------------|-----------|---------|
| T-001 | <task> | todo | P1 | <agent> | 01_<phase> | user | <verifiable condition> | <YYYY-MM-DD> |

## Done
| ID | Task | Finished | Result / link |
|----|------|----------|---------------|
| T-000 | Bootstrap project docs (bang-skill) | <YYYY-MM-DD> | Project_proposal.md, task_board.md, Process_phases/ |

## Rules for agents
- New task -> next free ID, new row in Active.
- Status change -> edit that row and its `Updated` date. Never delete rows.
- Done or cancelled -> move the row to Done with its result (file, PR, commit, report) or `cancelled: <reason>`.
- Update `_Last updated_` on every edit.
