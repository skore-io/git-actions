# Open PR Notifier

Esta action verifica PRs abertos e envia notificações automáticas baseadas no tempo que estão abertos. Ela também pode fechar automaticamente PRs que ficam muito tempo sem atividade.

## Funcionalidades

- Notifica quando um PR está aberto há 1 ou 2 dias sem revisões
- Notifica quando um PR está aberto há 3 dias
- Notifica quando um PR está aberto há 4 dias
- Notifica quando um PR está aberto há 5 dias
- Notifica quando um PR está aberto há 7 dias
- Fecha automaticamente PRs que estão abertos há mais de 7 dias e sem atividade por 1 dia

## Regras

| Ação                          | Quando rodar?                                  | Mensagem                                                                                                                                                                         |
| ----------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ⚠️ Alerta: sem review         | **Após 1 ou 2 dias aberto, sem nenhum review** | Esse PR tá aberto há x dias e ainda não recebeu nenhuma revisão. Que tal dar um ping na galera pra revisar?                                                                      |
| 📣 Lembrete de acompanhamento | **Após 3 dias aberto**                         | Esse PR tá aberto há 3 dias. Tem algo travando ou já dá pra seguir com QA?                                                                                                       |
| ⏳ Alerta de inatividade      | **Após 4 dias aberto**                         | Esse PR tá aberto há 4 dias. Que tal dar um gás nele?                                                                                                                            |
| 🚨 Check-in de status         | **Após 5 dias aberto**                         | Esse PR tá por aqui há 5 dias. Tá tudo certo? Se tiver algo travando, o time pode dar uma força — tamo junto!                                                                    |
| ⏰ Alerta final               | **Após 7 dias aberto**                         | 7 dias de PR! Você desbloqueou a conquista: "PR lendário em modo espera" 🏅<br><br>Se não houver atividade nas próximas 24h, ele será fechado automaticamente. Bora evitar isso? |
| ❌ Fechamento automático      | **Após 7 dias aberto + 1 dia sem atividade**   | Esse PR ficou aberto por X dias e sem atualizações nas últimas 24h. Fechando automaticamente — se ainda for relevante, sinta-se à vontade pra reabrir.                           |

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
