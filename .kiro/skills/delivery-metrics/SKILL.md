# Delivery Metrics — Métricas de Entrega e Retrospectiva

## Quando ativar
- `delivery-metrics` ou `delivery-metrics [últimas N sprints]`
- "métricas do time", "throughput", "cycle time"
- `delivery-metrics --retro` para dados de retrospectiva

## Workflow

### Modo Padrão
1. Buscar últimas N sprints (padrão: 3)
2. Para cada sprint calcular:
   - Throughput (tasks entregues, excluindo containers/rejected)
   - Cycle time (created → finished)
   - Lead time (entered sprint → finished)
   - Taxa de bugs por sprint
   - % do objetivo atingido
3. Comparar evolução entre sprints
4. Identificar tendências (melhorando / piorando / estável)

### Modo Retro (--retro)
Quando chamado com `--retro` ou "preparar retro":
- MRs revertidos na sprint (com links)
- Tempo médio em Code Review (created_at MR → merged_at)
- Scope creep: tasks adicionadas após início da sprint
- Tasks paradas >5 dias na mesma lane
- Top 3 "o que foi bem" (entregas rápidas, cycle time baixo)
- Top 3 "o que melhorar" (reverts, tempo parado, bugs escapados)
- Sugestões de ações concretas para retrospectiva

## Output
- Tabela comparativa entre sprints
- Visualização de tendência
- Destaques: o que melhorou, o que piorou
- Metas sugeridas para próxima sprint

## Output HTML
- Caminho: `.kiro/skills/delivery-metrics/reports/delivery-metrics-{periodo}.html`
- Tema dark, visual profissional
- Incluir: tabela comparativa, gráfico de tendência, destaques, insights retro
