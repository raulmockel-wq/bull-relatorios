# ⭐ PADRÃO NOVO (17/08/2026): publicar no domínio da Bull, área por cliente

A partir de agora o material de cliente vai para o **domínio da Bull**, com uma **área fixa por cliente**:
`https://painel.bullinvest.com.br/<cliente>/` (ex.: `/bigodon/`, `/salomao/`, `/anderson/`).

- Arquivos ficam no VPS Bull (2.25.179.122) em `/var/www/clientes/<cliente>/`, servidos pelo nginx `painel-bull` (bloco `location /<cliente>/`, `noindex`, sem auth pro cliente abrir).
- Fonte versionada em `bull-site/<cliente>/` (neste repo). Cada material é um subcaminho: `/<cliente>/<material>/`.
- A raiz `/<cliente>/` é a "Área do Cliente" (índice premium com cards linkando os materiais).
- **Backup em 3 camadas, sempre:** (1) cérebro/local `bull-site/`, (2) GitHub (este repo), (3) Google Drive `Meu Drive/Bull Invest/site-clientes-bull/`. O VPS é o ao vivo.
- Passo a passo: montar `bull-site/<cliente>/` → `rsync` pro VPS → inserir `location /<cliente>/` no nginx `painel-bull` → `nginx -t && reload` → commit/push → rsync pro Drive.

Meta futura: `<cliente>.bullinvest.com.br` (subdomínio próprio) via wildcard DNS na HostGator, pra o Steve publicar sozinho. Falta só o acesso da HostGator.

---

# Bull Relatórios — pasta online dos clientes (GitHub Pages, modelo antigo)

Repositório **público** que hospeda os relatórios dos clientes da Bull Invest via GitHub Pages.
Os links são **não listados** (noindex + robots Disallow) — só quem recebe o link direto acessa.

**URL base:** https://raulmockel-wq.github.io/bull-relatorios/

## Clientes publicados
| Cliente | Pasta (código secreto) | Link pra mandar |
|---|---|---|
| Victor Prado (Bigodon) · Maio/2026 | `victor-a6d5c4` | https://raulmockel-wq.github.io/bull-relatorios/victor-a6d5c4/ |
| Anderson "Gu" · Roteiro 1º encontro | `anderson-001ad6` | https://raulmockel-wq.github.io/bull-relatorios/anderson-001ad6/ |
| Anderson "Gu" · Auditoria Financeira (jan–mai/2026) | `anderson-auditoria-ae6dd1` | https://raulmockel-wq.github.io/bull-relatorios/anderson-auditoria-ae6dd1/ |
| Anderson "Gu" · Fechamento Julho/2026 (dashboard) | `anderson-fechamento-julho-cf401a` | https://raulmockel-wq.github.io/bull-relatorios/anderson-fechamento-julho-cf401a/ |
| Anderson "Gu" · Plano de Ação | `anderson-plano-b5823b` | https://raulmockel-wq.github.io/bull-relatorios/anderson-plano-b5823b/ |
| Service One · Diagnóstico Trimestral (abr–jun/2026) | `serviceone-diagnostico-3a1e6f` | https://raulmockel-wq.github.io/bull-relatorios/serviceone-diagnostico-3a1e6f/ |
| Victor Prado (Bigodon) · Reunião 15/06/2026 | `bigodon-reuniao-7608e4` | https://raulmockel-wq.github.io/bull-relatorios/bigodon-reuniao-7608e4/ |
| Emilyn Couto (Bigodon) · Auditoria Financeira (15/03–15/06) | `emily-2b2149` | https://raulmockel-wq.github.io/bull-relatorios/emily-2b2149/ |
| Bigodon (Victor) · Proposta Clube Pai & Filho | `bigodon-clube-pai-filho-d09f3c` | https://raulmockel-wq.github.io/bull-relatorios/bigodon-clube-pai-filho-d09f3c/ |
| Nicolas (filho do Alyson) · Treinamento Mercado Financeiro | `nicolas-2b7b70` | https://raulmockel-wq.github.io/bull-relatorios/nicolas-2b7b70/ |
| Treinamento · O Ciclo do Dinheiro | `aula-ciclo-do-dinheiro` | https://raulmockel-wq.github.io/bull-relatorios/aula-ciclo-do-dinheiro/ |
| Victor Prado (Bigodon) · Resumo da Mentoria 17/08/2026 | `bigodon-mentoria-17ago-5812cf` | https://raulmockel-wq.github.io/bull-relatorios/bigodon-mentoria-17ago-5812cf/ |

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
