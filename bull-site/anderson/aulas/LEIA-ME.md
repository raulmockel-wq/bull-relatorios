# /anderson/aulas/ NAO e arquivo estatico

Desde 08/09/2026 esse caminho e servido por um **aplicativo**, nao pelo `index.html` desta pasta.

- nginx `painel-bull`: `location /anderson/aulas/` faz `proxy_pass http://127.0.0.1:3220/`
- App: pm2 `aulas-bull`, codigo em `/opt/aulas-bull/server.js` no VPS Bull (2.25.179.122)
- Estado das aulas: `/opt/aulas-bull/data/anderson.json` (o `anderson.json` da raiz e so a semente)
- **PIN do Anderson: 4969** (o 8937 da semente nao vale)
- Painel do Raul pra marcar aula dada: https://painel.bullinvest.com.br/anderson/aulas/admin

## Marcar uma aula como dada

Pelo painel admin, ou pela API:

```
curl -X POST https://painel.bullinvest.com.br/anderson/aulas/api/toggle \
  -H "Content-Type: application/json" \
  -d '{"pin":"4969","n":7,"feita":true}'
```

O `index.html` desta pasta e a versao estatica antiga, mantida so como historico.
Editar ele NAO muda nada no ar.
