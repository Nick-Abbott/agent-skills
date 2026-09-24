---
name: verify-change
description: Select proportionate local checks and report evidence for a code or configuration change using the consuming project's existing tools.
---

# Verify a change

Read the project's instructions and the affected production contract. Use its package manager, build system, and test runner directly where they already provide the needed commands. A custom wrapper needs a demonstrated missing capability and should remain thin. Do not create a command-selection system merely to make verification look uniform.

While iterating, run focused checks at the boundary that can expose the failure. For the final change, run the project's required gate and any additional check justified by the affected behavior or risk. Broader changes may need broader checks; a routine fix does not require a whole-system audit. Reuse passing evidence when the relevant inputs and environment have not changed.

Investigate a failure before changing tests or policy. Check whether it comes from production behavior, test setup, infrastructure, or an unrelated environment change. Preserve assertions that protect real guarantees. If a check cannot run, state what remains unverified; never turn a failed check into a claimed pass.

Report the commands or checks actually run, their results, and material limits. Keep the summary short when the evidence is simple. Use disposable state and synthetic data when the project requires them; follow its specific rules for external services and secrets. If choosing tests becomes a substantial coverage review, the `test-audit` skill can guide that deeper decision when available.
