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
