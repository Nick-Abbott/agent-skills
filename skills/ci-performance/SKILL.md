---
name: ci-performance
description: Diagnose and improve CI feedback time or resource cost from measured workflow evidence, while preserving meaningful verification.
---

# Improve CI performance

First define the actual problem: contributor wait time, compute cost, or both. Separate queue delay from execution. For execution, distinguish the critical path from aggregate runner work; adding parallel jobs can shorten one while increasing the other. Break the observed path into setup, dependency restore, compilation, tests, cache or artifact transfer, and cleanup. Compare runs under similar runner, cache, and source conditions. Local timing can locate work but does not prove hosted savings.

Remove unnecessary work and repeated setup first. Use the existing build tool's task graph, incremental behavior, and caching before adding scripts or a scheduler. A no-op cache hit does not prove changed-source correctness; verify work on changed inputs. Measure contention before increasing concurrency, especially when jobs share CPU, memory, disk, or network.

Separate ordinary fast feedback from deeper qualification when the failure boundary allows it. Keep required assurance before the point where failure would matter, and preserve failure visibility: missing, skipped, or cancelled required work must not count as success. Explain any new orchestration in terms of the requirement, why native tools cannot meet it clearly, and its maintenance cost.

Report what changed, comparable before and after evidence, and any unmeasured effects. Stop optimizing when further gains lack evidence or require disproportionate complexity. A small gain may properly end with no change.
