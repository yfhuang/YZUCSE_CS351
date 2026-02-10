# AI Tool Usage Policy

## Allowed Scenarios
1) Unit tests: test plans, edge cases, boilerplate test code (must verify)
2) Troubleshooting: error explanation, debug plan, CI-only failure diagnosis
3) CI: workflow drafting and debugging (must not disable tests to “make green”)
4) Docker: Dockerfile drafting, multi-stage suggestions (must build/run locally)

## Required Logging
Students must maintain AI_USAGE.md:
- prompt (brief)
- AI output summary
- what was changed
- verification steps (commands + results)

## Prohibited
- Submitting AI-generated code without understanding/verifying
- Sharing secrets/tokens/private data in prompts
- Disabling tests/quality gates without permission
