# Action pinning policy

The starter workflows use maintained major tags so that the templates remain
readable. Before using a workflow in a production client repository, replace
every third-party `uses:` revision with its reviewed immutable commit SHA.

Keep the readable upstream version as a trailing comment, for example:

```yaml
uses: actions/checkout/<reviewed-SHA> # v4
```

Do not use an unreviewed pull request branch or a mutable tag in protected
deployment workflows.
