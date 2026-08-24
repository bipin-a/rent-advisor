# Testing rules

Shared rules for proving behaviour efficiently.

## A test is earned when it protects

- an acceptance criterion;
- a defect that could return; or
- a material technical or product risk.

Do not use test count as a measure of confidence.

## Stable proof

- Test the public behaviour or observable consequence, not how it happens internally.
- A test should fail when its protected guarantee is broken, but stay green when the implementation is safely refactored.
- Do not pin incidental wording, JSON shape, database query text, private interface structure, snapshots, helper output, or mock call order unless that detail is the contract.
- Lower-level tests may supplement public proof when they isolate a meaningful rule, risk, or failure.
- Update a test when the protected contract changes or the test was wrong—not merely because the implementation changed.

## Efficient sequence

1. Check whether existing tests already prove the behaviour.
2. Name the guarantee and the primary boundary that proves it.
3. Choose the narrowest meaningful boundary that proves the observable result.
4. For defects and high-risk changes, prove the failure for the intended reason before applying the fix.
5. Run focused tests first, then the wider required checks.
6. Record exact commands, results, failures, and skipped checks.

Avoid duplicate proof. Reuse shared test infrastructure when it has one canonical owner, while keeping scenario-specific data local to the test.

## Test data and environment evidence

- Identify the environment, data source and type, and dataset version or baseline used for material proof.
- Prefer deterministic, resettable fixtures or generators when repeatability matters.
- Keep Project-specific scenarios with the tests or Project that owns them. Extract shared data infrastructure only when several Projects genuinely need one maintained owner.
- Synthetic, fixture, mock, or anonymized data proves only the behaviours and relationships it represents. Record important differences from production rather than presenting proxy evidence as real-world evidence.
- Do not copy production secrets or personal data into non-production environments without an explicit, approved privacy and security design.
- Keep mock or seed data compatible with the schema it exercises and make drift detectable.

## States to consider when relevant

- create or first use;
- existing data or returning use;
- change;
- reverse or undo;
- disable, remove, or retire;
- reload or restart;
- partial failure and recovery.

## Repository commands

These commands are intentionally deferred until the Technical Specification selects the stack and executable test configuration exists. Record stable repository entry commands here before the first build candidate is handed to Validate. Keep Project-specific proof requirements in the owning Technical Specification.

Focused tests: Deferred until executable test configuration exists.

Full required checks: Deferred until executable test and CI configuration exist.
