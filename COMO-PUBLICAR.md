# Bull Relatórios — pasta online dos clientes

Repositório **público** que hospeda os relatórios dos clientes da Bull Invest via GitHub Pages.
Os links são **não listados** (noindex + robots Disallow) — só quem recebe o link direto acessa.

**URL base:** https://raulmockel-wq.github.io/bull-relatorios/

## Clientes publicados
| Cliente | Pasta (código secreto) | Link pra mandar |
|---|---|---|
| Victor Prado (Bigodon) · Maio/2026 | `victor-a6d5c4` | https://raulmockel-wq.github.io/bull-relatorios/victor-a6d5c4/ |
| Anderson "Gu" · Roteiro 1º encontro | `anderson-001ad6` | https://raulmockel-wq.github.io/bull-relatorios/anderson-001ad6/ |
| Victor Prado (Bigodon) · Reunião 15/06/2026 | `bigodon-reuniao-7608e4` | https://raulmockel-wq.github.io/bull-relatorios/bigodon-reuniao-7608e4/ |

> Dashboard avulso do Victor: https://raulmockel-wq.github.io/bull-relatorios/victor-a6d5c4/dashboard.html

## Como publicar um novo cliente (passo a passo do Claude)
1. Gerar código secreto: `python -c "import secrets;print(secrets.token_hex(3))"`
2. `mkdir <cliente>-<token>` e copiar os HTMLs pra dentro (renomeando o principal pra `index.html`).
3. Garantir que os HTMLs usam `../chart.umd.min.js` (a lib mora na raiz do repo).
4. Inserir `<meta name="robots" content="noindex, nofollow">` logo após `<head>` em cada HTML.
5. `git add -A && git commit -m "..." && git push`
6. Esperar ~1 min e mandar o link `.../<cliente>-<token>/`.

## Regras
- Sempre código secreto aleatório na pasta (segurança por obscuridade).
- Sempre noindex em todo HTML publicado.
- Nunca subir extratos brutos, CPF, áudios — só o relatório/dashboard já tratado.
