# GitHub Actions のワークフローを置く場所

複数リポジトリから呼び出して使う reusable workflow を置きます。

## Structurizr diagrams

`structurizr-diagrams.yml` は、Antora content root 配下の
`modules/**/examples/diagrams/structurizr/workspace.json` を検出し、
Structurizr の SVG export を実行します。

呼び出し側の例は以下です。

```yaml
name: Generate Structurizr Diagrams

on:
  pull_request:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  contents: read

jobs:
  diagrams:
    uses: f-vermi-lion/github-workflows/.github/workflows/structurizr-diagrams.yml@main
    with:
      content-root: docs
```
