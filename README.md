# CodeRabbit central configuration

[`.coderabbit.yaml`](.coderabbit.yaml) in this repository is CodeRabbit's
[central configuration](https://docs.coderabbit.ai/configuration/central-configuration)
for every tinkerologie repository without its own `.coderabbit.yaml`.

It sets `inheritance: true`, so the Organization UI settings still apply to
anything not defined here. It adds:

- Automatic issue enrichment and `bug` / `enhancement` labeling for issues the
  org's Issue Type Labeler workflow could not classify.
- Automatic coding plans for issues labeled `bug` or `enhancement`
  (opt out with `no-plan`).
- Issue labeling and planning skip issues labeled `question`, `duplicate`,
  `invalid`, `wontfix`, or `no-type`, matching the Issue Type Labeler.
- A pre-merge check that warns when changed code has no tests. It complements
  Codecov's `codecov/patch` gate, which enforces coverage. It is a warning, not
  an error, because the rulesets require no approving reviews, so a CodeRabbit
  change request would not block the merge anyway.
- The docstring, title, and description pre-merge checks are off.

The review profile is `quiet`, the same as the Organization UI.

Validate changes with:

```bash
coderabbit config validate .coderabbit.yaml
```

To see the configuration CodeRabbit resolves for a pull request, comment
`@coderabbitai configuration` on it.

See [GOVERNANCE.md](https://github.com/tinkerologie/.github/blob/main/GOVERNANCE.md)
for the contribution rules this supports.
