# AGENTS.md

Canonical operational instructions for coding agents working in this
repository. Read this file before making changes.

## Authority and project structure

- This repository is implementation-language-neutral.
- The authoritative behavioral specification is `specs/Project-Spec.md`.
  Implementations and tests must conform to it.
- Define the mission and initial behavioral contract before product
  implementation. Unresolved placeholders are not accepted requirements.
- This repository contains scripts and tools intended to help inspect machines
  for malware. The specification defines the accepted scope and boundaries;
  do not infer security, detection, remediation, platform, or privacy behavior
  that it does not establish.
- Do not add speculative directory structure, frameworks, packaging,
  abstractions, infrastructure, collectors, telemetry, or remediation behavior
  without a concrete, immediate need accepted in the specification.

## Standards

Agents MUST adhere to:

- Keep a Changelog 1.1.0: https://keepachangelog.com/en/1.1.0/
- Semantic Versioning 2.0.0: https://semver.org/spec/v2.0.0.html

These external standards are authoritative and must not be redefined locally.
Document only a necessary project-specific exception or extension here, and
continue to follow the referenced standard otherwise.

## Design and specification review

`TEAM.md` defines the review team: Maya (design), Alex (product), Priya
(engineering), Marcus (security), and Dave (engineering executive and human
repository owner). "the team" and "theTeam" both refer to that group.

- Required for any change to the authoritative specification or to a speclet
  in `specs/speclets/`. Work through each perspective before proposing the
  change.
- Advisory for everything else. Routine and mechanical changes do not require
  a five-perspective review.
- When asked to have the team review work, evaluate the relevant perspectives,
  converge, and incorporate the result.
- If material disagreement remains, present at most two options, their
  meaningful tradeoff, and a recommendation. Escalate only the decision that
  requires the repository owner's judgment.
- The repository owner is human. Agents must not decide or speak on the
  owner's behalf; leave escalated decisions open for the user.

## Specification lifecycle

- `specs/Project-Spec.md` is the single authoritative current behavioral
   contract.
- Normal accepted changes update that specification in place. Git history and
  release tags preserve historical states.
- Do not keep duplicate archived specification copies merely to preserve
   history.
- The specification is aligned with software releases rather than having an
   independent version. Its state at a release tag defines that release's
   behavior.
- `specs/speclets/` contains focused, proposed, or in-progress behavioral
  design changes.
- When a speclet is accepted, merge its decision into the authoritative
  specification, then normally delete the speclet.
- Introduce parallel or version-specific specifications only when the project
  must maintain multiple behavioral contracts simultaneously.

## Behavioral-change workflow

Before changing behavior, determine whether the change is externally observable
or documented.

If it is:

1. Update the authoritative specification, or create/update a temporary
   speclet while the design is being developed or reviewed.
2. Once accepted, ensure the authoritative specification incorporates the
   speclet's decision and remove the accepted speclet.
3. Update implementation and tests to conform to the accepted specification.
4. Add a notable user-visible change to `CHANGELOG.md` under `Unreleased` when
   required by Keep a Changelog.
5. Assess the release impact under Semantic Versioning.

Do not create a released changelog section or bump a released version merely
because a change was made. Do not silently reinterpret ambiguous requirements;
surface ambiguity for resolution.

## Issue lifecycle

- Create an issue for discovered or requested work that is valid but cannot be
  completed in the current change. Do not create issues merely to restate work
  being completed immediately.
- State the problem, user or project impact, relevant constraints, and
  verifiable acceptance criteria. Link the authoritative specification or
  speclet when behavior is defined or changed there.
- Keep issue status and scope accurate as decisions or implementation evolve.
  Record material deferrals or follow-up work explicitly rather than silently
  dropping them.
- Resolve an issue only after its accepted scope is implemented and applicable
  checks and acceptance criteria have been verified. Link the resolving change,
  relevant tests, and specification or changelog updates when applicable.
- Close without implementation only when the issue is demonstrably duplicate,
  invalid, obsolete, or intentionally out of scope, and record the reason.

## Mandatory completion check

Every coding-agent completion report must include:

```text
Change compliance:
- Spec: <updated | no change required - reason>
- Changelog: <updated | no entry required - reason>
- SemVer impact: <major | minor | patch | none>
- Tests: <updated/run/not run/etc.>
```

Perform these checks even when the request does not explicitly mention the
specification, changelog, versioning, or tests.
