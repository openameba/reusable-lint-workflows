# action-lint-workflows

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
    uses: openameba/reusable-lint-workflows/.github/workflows/action.yml@4baef1161e214d85130d0a1a281f876ac9956442
```
