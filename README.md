# iter8-action

## Getting started

The Iter8 action runs an Iter8 experiment by reference to the experiment chart and, optionally, a chart repository. The experiment is configured by the definition of a `values.yaml` file. For example:

``` yaml
    - run: |
        cat << EOF > myvalues.yaml
          url: http://127.0.0.1/get
        EOF
    - uses: iter8-tools/iter8-action@v0.9
      with:
        chart: load-test-http
        valuesFile: myvalues.yaml
```

Experiment configuration depends on the definition of the experiment chart. Default charts are defined [here](https://github.com/iter8-tools/hub/tree/main/charts).
For more information about Iter8, see the [Iter8 documentation](https://iter8.tools/0.9).

## Action Inputs

| Input Name | Description | Default |
| ---------- | ----------- | ------- |
| `chart` | Name of the experiment chart. Required. | None |
| `chartRepo` | URL of experiment chart repo. | `https://iter8-tools.github.io/hub` |
| `chartVersion` | Version constraint for the chart. | None |
| `valuesFile` | Path to configuration values file. | None |
| `validateSLOs` | Validate any specified SLOs. | `true` |
| `logLevel` | Logging level; valid values are `trace`, `debug`, `info`, `warning`, `error`, `fatal`, `panic` | `info` |

## Log output

For each execution of the Iter8 action, the output of the action includes the following for reference:

- Version of iter8 (output of `iter8 version`)
- The experiment run in yaml
- An experiment report (the output of `iter8 report`)
- Assessmet of success (output of `iter8 assert -c completed -c nofailures -c slos`)

## Iter8 Documentation

Iter8 documentation is available at <https://iter8.tools>.

## Developing Iter8

We welcome PRs!

See [here](CONTRIBUTING.md) for information about ways to contribute, Iter8 community meetings, finding an issue, asking for help, pull-request lifecycle, and more.
