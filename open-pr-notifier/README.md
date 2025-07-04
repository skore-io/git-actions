# Open PR Notifier

Esta action verifica PRs abertos e envia notificações automáticas baseadas no tempo que estão abertos. Ela também pode fechar automaticamente PRs que ficam muito tempo sem atividade. Ela atua apenas nos dias de semana, finais de semana são ignorados.

## Regras

Veja abaixo uma tabela com as regras:
| Ação | Quando rodar? | Mensagem |
| ----------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ⚠️ Alerta: sem review | **Após 1 dia útil aberto, sem nenhum review** | ⚠️ **1 dia útil sem revisão!**<br><br>Que tal dar um ping na galera pra revisar e tirar esse PR da fila? 🚀 |
| 📢 Lembrete de acompanhamento | **Após 2 dias úteis aberto** | 📢 **2 dias úteis!**<br><br>Tem algo travando ou já dá pra seguir com QA?<br>Se precisar de ajuda pra destravar, só avisar! |
| ⏳ Alerta de inatividade | **Após 3 dias úteis aberto** | ⏳ **3 dias úteis!**<br><br>Esse PR já tá esperando faz tempo! Será que hoje ele sai? 👀 |
| 🚨 Check-in de status | **Após 4 dias úteis aberto** | 🚨 **4 dias úteis!**<br><br>Esse PR tá mais velho que aquele bug que virou feature! 😂<br>Tá tudo certo? Se tiver algo travando, o time pode dar uma força — tamo junto! |
| 🏆 Alerta final | **Após 5 dias úteis aberto** | 🏆 **5 dias úteis!**<br><br>Você desbloqueou a conquista: **"PR lendário em modo espera"** 🏅<br><br>⚠️ Se não houver atividade nas próximas 24h, ele será fechado automaticamente. Bora evitar o SHAME? 🔔 |
| ❌ Fechamento automático | **Após 5 dias úteis aberto + 1 dia útil sem atividade** | 🔔 **SHAME! SHAME! SHAME!**<br><br>[GIF do SHAME]<br><br>Esse PR ficou aberto por **X dias úteis** e sem atualizações nas últimas 24h!<br><br>🚨 FECHANDO AUTOMATICAMENTE 🚨<br><br>Se ainda for relevante, sinta-se à vontade pra reabrir. Mas lembre-se:<br>"PRs são como café - quando esfria, perde a graça" - Barista do Git 😂 |

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
