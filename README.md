# reusable-lint-workflows

lint workflow files

## How to use

```yaml
name: lint workflow files

on:
  pull_request:
    paths:
      - ".github/workflows/**"
  push:
    branches:
      - main
    paths:
      - ".github/workflows/**"

permissions: {}

jobs:
  lint-workflow-files:
    permissions:
      contents: read
    uses: openameba/reusable-lint-workflows/.github/workflows/action.yml@3348ac7c85b021c13669e91a51e5f7a8bef91577 # v1.0.0
```

## Inputs

| name          | type   | default             | description                                             |
| ------------- | ------ | ------------------- | ------------------------------------------------------- |
| `runner`      | string | `'"ubuntu-latest"'` | The value passed to `runs-on`, as a JSON string         |
| `extra-paths` | string | `''`                | Extra newline-separated paths to add to sparse-checkout |

`runner` must be passed as a JSON string. The default is fine for most cases.

```yaml
jobs:
  lint-workflow-files:
    permissions:
      contents: read
    uses: openameba/reusable-lint-workflows/.github/workflows/action.yml@<ref>
    with:
      # single label
      runner: '"macos-latest"'
      # multiple labels (e.g. self-hosted)
      # runner: '["self-hosted", "linux", "x64"]'
```

`extra-paths` adds paths to the sparse-checkout of every lint job, on top of the
always-included `.github/workflows` and `.github/actions`. Use it when your
actions or lint config live elsewhere (e.g. custom action directories, or
`.github/actionlint.yml`). If those directories also need to trigger the
workflow, add them to the caller's `on.*.paths` as well.

```yaml
jobs:
  lint-workflow-files:
    permissions:
      contents: read
    uses: openameba/reusable-lint-workflows/.github/workflows/action.yml@<ref>
    with:
      extra-paths: |
        restore
        save
        .github/actionlint.yml
```
