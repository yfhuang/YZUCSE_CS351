# Project Plan (Jira + Git Workflow)

## 1. Milestones
| Milestone | Deliverable | Due | Owner |
|---|---|---:|---|
| M1 | SRS + SDS draft + CI skeleton |  |  |
| M2 | Core engine complete + unit tests |  |  |
| M3 | CLI end-to-end + golden tests |  |  |
| M4 | v1.0 release + deploy notes |  |  |

## 2. Jira Structure
- Epic: Project (A/B/C)
- Stories: SRS, SDS, Parser, Engine, CLI, Tests, CI, Docs, Release
- Definition of Done (DoD):
  - PR merged (no direct push to main)
  - CI green
  - Tests added
  - Docs updated

## 3. Git Collaboration Rules
- Branch naming: feature/<JIRA-KEY>-short-title
- PR required for merge to main
- Collaborator must:
  - review every PR (at least one “request changes” cycle overall)
  - approve before merge

## 4. Meeting / Checkpoint Notes (optional)
- Sprint demo checklist:
  - show CLI run
  - show tests
  - show CI run
