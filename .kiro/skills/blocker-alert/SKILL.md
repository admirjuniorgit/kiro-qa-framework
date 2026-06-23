# Blocker Alert — Detecta Tasks Paradas

## Quando ativar
- `blocker-alert` ou `blocker-alert [nome-sprint]`
- "o que está parado", "tem algo travado", "blockers"

## Workflow

1. Buscar tasks da sprint ativa que NÃO estão em Done/Closed
2. Calcular tempo na lane atual (time_in_current_step)
3. Aplicar thresholds:
   - In Progress >5 dias sem MR aberto → ⚠️ parada
   - Code Review >7 dias → ⚠️ CR lento
   - Testing >5 dias → ⚠️ fila de teste
   - To Do com prioridade High/Critical → ⚠️ não iniciada
4. Cruzar com GitLab: se MR tem discussions não resolvidas → bloqueado por CR
5. Ordenar por criticidade

## Output
- Lista de tasks paradas com tempo e motivo provável
- Sugestão de ação (cobrar CR, pedir ajuda, dividir task)
- Destaque para items do objetivo que estão parados

## Output HTML
- Caminho: `.kiro/skills/blocker-alert/reports/blocker-alert-{data}.html`
- Tema dark, visual profissional
- Todos IDs de tasks = links clicáveis
- Incluir: alertas coloridos por severidade, tempo parado, ação sugerida
