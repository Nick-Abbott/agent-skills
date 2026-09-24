---
name: release-safety
description: Review or implement artifact qualification and publication so the published bytes, required evidence, recovery, and authorization remain connected.
---

# Preserve release identity

Identify the actual publishable artifact and the boundary at which it becomes available to users. A source revision identifies inputs; it does not identify artifact bytes. Resolve mutable references to immutable identity with the platform or registry's normal capability. Bind qualification evidence to those actual bytes and ensure publication selects the same identity. Different or rebuilt bytes need applicable qualification; unchanged identified bytes can reuse valid evidence under the project's freshness and environment requirements.

Choose checks for credible release-only failures. Lightweight packaging smoke can catch missing files, entry points, or startup wiring; deeper qualification belongs where runtime behavior, integration, persistence, or recovery can fail despite successful packaging. Scale the checks to the project's actual risk. Use existing build, registry, and deployment facilities before inventing a coordinator, archive, or manifest format.

Define required evidence and fail closed when it is missing, stale, mismatched, failed, cancelled, or ambiguous. Keep publication authorization explicit and separate from tests passing. Preserve compatibility with persisted state and a usable recovery path; a version label or image digest alone does not prove an older reader can handle current data.

Before adding release machinery, state the guarantee it provides, why existing facilities do not provide it, and what the new concepts cost maintainers. For a small release, the right result can be a simple native publish command with an appropriate smoke check. Where real data or irreversible publication is involved, keep the necessary proof even if it adds complexity.
