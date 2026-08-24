# GitHub delivery rules

Shared rules for commits, pull requests, and release traceability.

## Configuration state

Git is initialized on `main` with `origin` set to the public repository [`bipin-a/rent-advisor`](https://github.com/bipin-a/rent-advisor). GitHub owns the live visibility and repository settings; re-check them before relying on this recorded configuration.

Repository-specific delivery policy is not fully configured. Do not treat a deferred choice below as approved.

- Every change to `main` must arrive through a pull request. GitHub branch protection applies this rule to repository administrators.
- Choose the commit convention before the first Project commit.
- Use the existing `.github/pull_request_template.md` for the first and subsequent pull requests.
- Derive required check names from the approved Technical Specification, executable test commands, and CI configuration. Record them here before the first Project pull request is merged.
- Use the Release workflow's explicit human authorization gate until a named production-release owner is recorded here.

## Sources of truth

- The Project and approved specifications own intended behaviour.
- Git owns code history.
- GitHub owns live pull request and check status.
- The deployment platform owns live release status.

Re-check live state before merging or releasing.

## Public repository hygiene

- Never commit credentials, secrets, private keys, or populated environment files. Store secret values in an appropriate local, GitHub, deployment, or service secret store; record only safe setup requirements and variable names.
- Do not commit unapproved personal or production data. Use synthetic, anonymized, or otherwise approved data according to [`testing-rules.md`](testing-rules.md).
- Review the staged diff for sensitive content before every push.

## Delivery profile

Every Project selects one profile through its approved Delivery Assessment before Build:

- `single-pr` — use when one pull request can be reviewed, validated, and released safely; target `main` directly.
- `multi-pr` — use when several independently reviewed pull requests must be assembled before the Project has value; follow `multi-pr-delivery.md`.
- `undecided` — allowed during Spec & Design and Assess Delivery, but not when Build begins.

Recommend `multi-pr` when two or more are true:

- several pull requests must work together before the result is useful;
- the assembled result needs shared-environment or end-to-end validation;
- delivery slices have blockers or a required merge order;
- explicit human review or release gates apply;
- merging slices directly to `main` would expose incomplete behaviour;
- parallel delivery lanes must converge on one integrated proof.

The human approves the profile and proposed delivery shape before implementation begins. Do not create live GitHub delivery objects from an unapproved assessment.

## Commits

- Keep each commit focused, traceable and easy to review and follow along.
- Preserve unrelated work.
- Link material code changes to the relevant Project or specification.

Commit naming convention: Deferred; choose before the first Project commit.

## Pull requests

Fill out `.github/pull_request_template.md` for every pull request.
Write the description according to [`../voice.md`](../voice.md).

Main branch policy: Every change to `main` requires a pull request; direct pushes are prohibited, including for repository administrators.

Branch naming convention: project name, issue number, summary

Merge method: Squash. GitHub permits squash merges only. Use the final pull request title as the commit subject and the pull request body as the commit body on `main`.

Required checks: Deferred until the technical stack, executable test commands, and CI check names exist; record them before the first Project pull request is merged.

## Traceability

- Build and validation summaries link to the relevant commit or pull request.
- Release summaries link to the released commit, pull request, and deployment evidence.
- Lessons link to their evidence and to the source they changed.

## Human gates

Required approval before merge: Zero approving reviews while the repository has one maintainer. Pull requests remain mandatory as a self-review and delivery-hygiene gate. Revisit this rule when another maintainer receives merge access.

Required approval before production release: Explicit human authorization for the exact candidate, as required by [`06_release`](../../workflows/06_release/CONTEXT.md). Record a named owner here when production ownership is known.
