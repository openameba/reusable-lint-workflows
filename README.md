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
    uses: openameba/reusable-lint-workflows/.github/workflows/action.yml@d5d3390650196e1e10ad9b8a8aa0b1e28684e649
```
