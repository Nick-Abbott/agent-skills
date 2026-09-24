# Engineering skills

Small, independent skills for engineering decisions that recur across projects. They grew from Chirli's test, CI, and release work; they do not prescribe its stack or commands.

## Defaults

Keep the code understandable to a human who must change, build, test, and debug it without an agent. Prefer conventional structure, clear ownership, direct control flow, familiar commands, and useful diagnostics. Choose the smallest solution that preserves correctness, authorization, privacy, durability, recovery, and release integrity. A good abstraction removes concepts a maintainer must understand; speculative extension points add them.

Keep ordinary work low ceremony. Add tests for credible regressions at meaningful boundaries and documentation for recurring questions or non-obvious decisions. More tests, reports, or pages are not goals. Start with the language ecosystem's build and test tools. Before adding custom orchestration, identify the missing requirement, why native tools or a simple command do not meet it, and the concepts the wrapper adds. Stop when that cost outweighs the demonstrated benefit.

These are defaults, not universal rules. Explicit task requirements and the consuming project's instructions govern its commands, architecture, safety constraints, and deliberate exceptions. Keep project facts there. Install shared skills unchanged when possible; adapt locally only for a real project need.

## Skills

- **[test-audit](skills/test-audit/SKILL.md):** assess the value and ownership of tests; use its deeper audit method only for an audit or broad cleanup.
- **[verify-change](skills/verify-change/SKILL.md):** select and report proportionate checks for a change.
- **[ci-performance](skills/ci-performance/SKILL.md):** diagnose CI elapsed time and compute cost before changing execution.
- **[release-safety](skills/release-safety/SKILL.md):** protect the identity, qualification, and authorization of a published artifact.

## Use in a project

Ask Codex's built-in `skill-installer` to install the desired `skills/<name>` paths from `Nick-Abbott/agent-skills` at a reviewed Git ref. It supports private repositories through existing Git credentials or GitHub token access, `--ref` for an exact reviewed revision, and an alternate destination when needed. Installed skills become available on the next turn. Review an update before reinstalling; the installer refuses to replace an existing destination, so remove or relocate that installation deliberately first. Project instructions should point to real local commands and constraints without copying the shared skill text.

## Contribute

Use Codex's built-in `skill-creator` guidance and `quick_validate.py` when authoring or changing a skill. Give each skill a precise discovery description, keep its `SKILL.md` self-contained, and add a reference only when detail should be loaded conditionally. Promote a method only when it prevents a demonstrated failure and applies beyond one project. Prefer editing or deleting existing prose over adding a new skill or governance file. The built-in format and installation guidance remain the source of truth.

The test-audit skill adapts ideas from OpenClaw under its MIT license; its [notice](skills/test-audit/NOTICE.md) travels with an individual skill installation. No license is granted here for the remaining original material.
