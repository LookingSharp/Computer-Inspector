# Specifications

This directory contains implementation-independent behavioral specifications
for Computer Inspector.

## Lifecycle

- [Project-Spec.md](Project-Spec.md) is the single authoritative current
  behavioral contract. Implementations and tests conform to it; its release-tag
  state defines the behavior released at that tag. The specification has no
  independent version.
- `speclets/` contains focused proposed or in-progress behavioral changes.
  After acceptance, merge the decision into the authoritative specification and
  normally delete the speclet. Git history preserves the development record;
  do not keep duplicate archived specifications merely to preserve history.
- [CHANGELOG.md](../CHANGELOG.md) records notable unreleased and released
  changes under Keep a Changelog. Assess Semantic Versioning release impact
  alongside behavior changes.
- Give each acceptance scenario a stable identifier. Tests added by the project
  must cite the identifier or identifiers they verify.
