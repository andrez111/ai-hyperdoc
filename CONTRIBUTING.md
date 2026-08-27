# Contributing

Contributions should keep the project small, portable, and behaviorally predictable.

## Good contributions

Useful changes include:

- clearer category boundaries;
- better edge-case handling;
- stronger examples;
- fixes to Agent Skills compatibility;
- evidence that a title rule causes unnecessary churn;
- support for an official conversation-title update action.

## Before opening a pull request

1. Explain the behavioral problem being solved.
2. Show at least one before/after example.
3. Avoid introducing a new macro unless existing categories cannot represent the case cleanly.
4. Keep the installable skill free of repository-only documentation.
5. Do not add dependencies without a deterministic runtime need.
6. Preserve the rule that the skill must never claim a rename occurred when the host cannot perform it.

## Changing the taxonomy

Taxonomy changes have high compatibility impact.

A proposal should include:

- the new or changed category;
- at least three representative conversation examples;
- the categories it could be confused with;
- the decision rule that resolves the ambiguity.

## Pull request scope

Prefer one behavioral change per pull request.

Large rewrites should explain why incremental changes are insufficient.
