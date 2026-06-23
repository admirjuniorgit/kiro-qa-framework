# Regression Map — Mapa de Risco de Regressão

## Quando ativar
- `regression-map [componente]`
- "risco de regressão nos filtros", "o que pode quebrar nos portais"

## Workflow

1. Buscar MRs recentes (últimos 30 dias) que tocam arquivos do componente
2. Para cada MR: avaliar risco baseado em:
   - Linhas alteradas (>500 = alto risco)
   - Número de arquivos tocados
   - Se possui testes automatizados
   - Se já foi revertido antes
   - Se é refactoring ou feature nova
3. Cruzar com bugs recentes naquela área
4. Gerar mapa de risco com áreas recomendadas para teste

## Output
- Lista de MRs que podem causar regressão, ordenados por risco
- Áreas que necessitam teste manual
- Cenários de teste automatizado sugeridos para adicionar
- Padrão histórico: com que frequência esse componente quebra?

## Output HTML
- Caminho: `.kiro/skills/regression-map/reports/regression-map-{componente}.html`
- Tema dark, visual profissional
- Links de MR clicáveis para GitLab
