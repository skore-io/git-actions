# Open PR Notifier

Esta action verifica PRs abertos e envia notificações automáticas baseadas no tempo que estão abertos. Ela também pode fechar automaticamente PRs que ficam muito tempo sem atividade.

## Funcionalidades

- Notifica quando um PR está aberto há 1 dia sem revisões
- Notifica quando um PR está aberto há 3 dias
- Notifica quando um PR está aberto há 4 dias
- Notifica quando um PR está aberto há 5 dias
- Fecha automaticamente PRs que estão abertos há 7 dias e sem atividade por 1 dia

## Como usar

```yaml
name: Open PR Notifier

on:
  workflow_dispatch:
  schedule:
    - cron: '0 12 * * *' # Every day at 9am BRT

jobs:
  notify-open-prs:
    runs-on: ubuntu-latest
    steps:
      - uses: skore-io/git-actions/open-pr-notifier@main
```

## Permissões necessárias

Esta action requer as seguintes permissões:

- `pull-requests: write`
- `issues: write`
