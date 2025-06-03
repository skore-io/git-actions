# Assign PR

Esta action atribui automaticamente o PR ao seu criador quando um novo PR é aberto.

## Como usar

```yaml
name: Assign PR to creator

on:
  pull_request_target:
    types: [opened]

jobs:
  assign_pr:
    name: Assign
    runs-on: ubuntu-latest

    steps:
      - uses: skore-io/git-actions/assign-pr@main
```

## Permissões necessárias

Esta action requer as seguintes permissões:

- `contents: read`
- `pull-requests: write`
