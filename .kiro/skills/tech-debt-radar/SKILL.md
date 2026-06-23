# Tech Debt Radar — Rastreamento de Dívida Técnica

## Quando ativar
- `tech-debt-radar`
- "dívida técnica", "o que está acumulando", "vulnerabilidades pendentes"

## Workflow

1. Buscar tasks do tipo "Vulnerability" ou títulos com "refactor/deps/atualizar/migrar"
2. Filtrar: não concluídas, sem sprint ou em sprints passadas não entregues
3. Calcular idade (dias desde criação)
4. Identificar padrões:
   - Vulnerabilidades com deadline próximo
   - Refactorings adiados >3 sprints
   - Dependências desatualizadas há muito tempo
5. Classificar por risco (deadline, severidade, impacto em segurança)

## Output
- Lista de tech debt ordenada por urgência
- Vulnerabilidades com countdown de deadline
- Items adiados repetidamente (quantas sprints?)
- Sugestão: o que endereçar na próxima sprint

## Output HTML
- Caminho: `.kiro/skills/tech-debt-radar/reports/tech-debt-radar-{data}.html`
- Tema dark, visual profissional
- Todos IDs de tasks = links clicáveis
- Incluir: lista por urgência, countdown de deadlines, items adiados
