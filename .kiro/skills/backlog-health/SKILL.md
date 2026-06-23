# Backlog Health — Score de Saúde do Backlog

## Quando ativar
- `backlog-health`
- "como está o backlog", "preparar refinamento", "tasks sem estimate"

## Workflow

1. Buscar tasks do backlog (To Do, sem sprint ou sprint futura)
2. Identificar problemas:
   - Sem estimate (story points)
   - Sem descrição ou descrição vazia
   - Sem critério de aceitação
   - Idade >60 dias sem movimentação
   - Épicos estagnados (sem filhas em progresso)
3. Classificar por severidade do problema
4. Sugerir candidatos para refinamento

## Output
- Score de saúde do backlog (%)
- Tasks que precisam de refinamento (sem estimate/descrição)
- Épicos estagnados
- Sugestão de próximo refinamento (quais pegar primeiro)

## Output HTML
- Caminho: `.kiro/skills/backlog-health/reports/backlog-health-{data}.html`
- Tema dark, visual profissional
- Todos IDs de tasks = links clicáveis
- Incluir: score de saúde, tasks sem estimate, épicos estagnados
