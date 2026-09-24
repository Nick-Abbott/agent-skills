---
name: test-audit
description: Assess whether new or materially changed tests protect distinct production contracts, or conduct an explicitly scoped suite audit; do not turn routine fixes into full audits.
---

# Test value and ownership

Use the consuming project's test policy and commands. A test is valuable when a credible production regression makes it fail at a meaningful boundary. Preserve coverage for correctness, authorization, privacy, durability, recovery, and release safety even when its setup is costly.

## For a new or materially changed test

Answer these before adding it:

1. What observable production contract does it protect?
2. What credible regression makes it fail for the intended reason?
3. Why would existing coverage not already catch that regression?
4. Does it require a production seam primarily for testing, and is that seam justified?

Read the implementation and overlapping tests, not just their names. Prefer the lowest boundary that can prove the contract. Another layer earns a test when it protects a distinct failure boundary, such as wiring or persistence. When practical, show a bug regression failing for the intended reason before the fix. If the answers are weak, add no test.

Testing seams are a tradeoff, not a ban. Controlled clocks, scheduler injection, and completion signals can expose causal behavior that would otherwise require fragile sleeps. Prefer direct tests and small fixtures; question exports, flags, wrappers, or mocks that exist only to make an assertion possible. A mock should expose the production decision, not manufacture the outcome being asserted.

## For an explicitly requested audit

Start from production contracts and their failure modes, then map relevant tests across layers. Identify the primary owner and any secondary owner with a genuinely different boundary. Read candidate tests, production paths, fixtures, callers, and relevant history before deciding. Investigate duplicated proof, assertions tied to private implementation, self-fulfilling mocks, obsolete contracts, and unnecessary setup. Names, assertion similarity, test duration, and test counts alone are insufficient evidence.

Before deleting a test, establish the contract it actually protected and the surviving owner, or establish that the contract is obsolete. Run focused checks and, when useful and proportionate, demonstrate that a credible production regression fails the surviving test for the intended reason. Retain uncertain coverage. A move between frameworks is a means of proving a contract, not a cleanup outcome by itself. Remove dead fixtures or seams only after checking callers and real coverage.

Keep the audit scoped. Record decisions, actual checks, and limits in the task or review, with temporary evidence in the project's usual ignored location. Do not require a permanent inventory, mutation campaign, test-count target, or report package for ordinary work. A successful audit may retain nearly every test.

Adapted in part from [OpenClaw's test-audit skill](https://github.com/openclaw/openclaw/blob/30e67dbd5fe630ce692e18abb576680085d82ff5/.agents/skills/test-audit/SKILL.md). See [NOTICE.md](NOTICE.md) for its license and attribution.
