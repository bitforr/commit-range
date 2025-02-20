# GitHub Action: bitforr/commit-range

This action determines updated commit ranges based on workflow's event payloads.

Possible use cases for the computed outputs are:
- Adjustment of the `fetch-depth` parameter for [actions/checkout](https://github.com/actions/checkout)
- Configuration of commit ranges for [crate-ci/commited](https://github.com/crate-ci/committed)

## Example

```yaml
on:
  push:
    branches:
    - main
  pull_request:
    branches:
    - main
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
    - uses: bitforr/commit-range@v0.5
      id: commit-range
    - uses: actions/checkout@v4
      with:
        fetch-depth: ${{ steps.commit-range.outputs.fetch-depth }}
```

## License

This project is licensed under the [Apache-2.0](./LICENSE) license.
