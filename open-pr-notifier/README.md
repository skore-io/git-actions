# Open PR Notifier

Esta action verifica PRs abertos e envia notificações automáticas baseadas no tempo que estão abertos. Ela também pode fechar automaticamente PRs que ficam muito tempo sem atividade. Ela atua apenas nos dias de semana, finais de semana são ignorados.

## Regras
Veja abaixo uma tabela com as regras:
| Ação                          | Quando rodar?                                  | Mensagem                                                                                                                                                                         |
| ----------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ⚠️ Alerta: sem review         | **Após 1 dia útil aberto, sem nenhum review**             | Esse PR tá aberto há 1 dia útil e ainda não recebeu nenhuma revisão. Que tal dar um ping na galera pra revisar? |
| 📣 Lembrete de acompanhamento | **Após 2 dias úteis aberto**                              | Esse PR tá aberto há 2 dias úteis. Tem algo travando ou já dá pra seguir com QA? |
| ⏳ Alerta de inatividade      | **Após 3 dias úteis aberto**                              | Esse PR tá aberto há 3 dias úteis. Que tal dar um gás nele? |
| 🚨 Check-in de status         | **Após 4 dias úteis aberto**                              | Esse PR tá por aqui há 4 dias úteis. Tá tudo certo? Se tiver algo travando, o time pode dar uma força — tamo junto! |
| ⏰ Alerta final               | **Após 5 dias úteis aberto**                              | 5 dias úteis de PR! Você desbloqueou a conquista: "PR lendário em modo espera". Se não houver atividade nas próximas 24h, ele será fechado automaticamente. Bora evitar isso? |
| ❌ Fechamento automático      | **Após 5 dias úteis aberto + 1 dia útil sem atividade**   | Esse PR ficou aberto por X dias e sem atualizações nas últimas 24h. Fechando automaticamente — se ainda for relevante, sinta-se à vontade pra reabrir. |

## Como usar

```yaml
name: Open PR Notifier

on:
  workflow_dispatch:
  schedule:
    - cron: '0 12 * * *' # Every day at 9am BRT

jobs:
  notify_open_prs:
    runs-on: ubuntu-latest

    steps:
      - uses: skore-io/git-actions/open-pr-notifier@main
```

## Permissões necessárias

Esta action requer as seguintes permissões:

- `pull-requests: write`
- `issues: write`
