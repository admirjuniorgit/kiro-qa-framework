# Escape Analysis — Bugs que Escaparam para Produção

## Quando ativar
- `escape-analysis` ou `escape-analysis [nome-sprint]`
- "bugs que escaparam", "o que foi pra produção com problema"

## Workflow

1. Buscar bugs criados APÓS o fim da sprint que referenciam MRs mergeados durante a sprint
2. Ou: bugs com tag "Service Desk" criados na sprint seguinte
3. Para cada escape:
   - Identificar MR causador (via título ou patch-tracker)
   - Verificar se MR tinha roteiro de teste
   - Verificar se MR tinha teste automatizado
   - Classificar causa: falta de teste / edge case / regressão / ambiente
4. Calcular taxa de escape (bugs escapados ÷ MRs mergeados)

## Output
- Lista de bugs que escaparam com MR causador
- Causa raiz simplificada de cada um
- Taxa de escape da sprint
- Sugestões de melhoria (mais testes? roteiros melhores? mais bancos?)
- Comparativo com sprints anteriores

## Output HTML
- Caminho: `.kiro/skills/escape-analysis/reports/escape-analysis-{sprint-name}.html`
- Tema dark, visual profissional
- Todos IDs de tasks = links clicáveis
- Incluir: lista de escapes, taxa, distribuição de causa, comparativo, ações
