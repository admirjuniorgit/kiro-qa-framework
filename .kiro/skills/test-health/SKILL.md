# Test Health — Análise Completa de Testes Automatizados

## Quando ativar
- `test-health` ou `test-health [período]`
- "testes falhando", "pipeline quebrada", "estabilidade dos testes", "flaky"

## Workflow

### 1. Coletar Pipelines Recentes
- Buscar últimas N pipelines do repositório de testes (padrão: 30 dias)
- Filtrar: failed ou success (ignorar canceled)

### 2. Identificar Jobs Falhados
Para cada pipeline falhada:
- Extrair nome do teste que falhou
- Extrair mensagem de erro do log do job
- Capturar screenshot diff se disponível

### 3. Classificar Causa da Falha

| Padrão no Log | Classificação |
|---|---|
| `TimeoutError`, `waiting for selector` | 🕐 Timeout/Seletor |
| `net::ERR_`, `ECONNREFUSED`, `navigation timeout` | 🌐 Ambiente/Rede |
| `Expected image to match`, `pixel diff` | 📸 Diff Visual |
| `AssertionError`, `expect(received)` | ❌ Assertion (bug real?) |
| `StaleElementReference`, `detached from DOM` | 🔄 Race Condition |
| `ENOMEM`, `out of memory` | 💾 Recurso |

### 4. Calcular Métricas
- **Taxa de falha por teste:** falhas / execuções × 100
- **Score de flakiness:** testes que alternam pass/fail na mesma branch
- **Top N mais instáveis** (ordenados por taxa de falha)
- **Clusters de falha:** testes que falham juntos (causa compartilhada)
- **Tendência:** piorando, melhorando ou estável

### 5. Cruzar com Kanban
- Buscar tasks de estabilização existentes
- Para cada top falhando: existe task para corrigir?
- Se não existe → sugerir criação com título padronizado

### 6. Verificar MRs Relacionados no Repositório de Testes
- Buscar MRs abertos/mergeados que tocam o arquivo do teste
- MR aberto → fix em andamento
- MR mergeado recente → verificar se resolveu

### 7. Mapear por Componente
Agrupar falhas por área funcional para identificar hotspots.

### 8. Gerar Relatório

## Output
1. **Score de estabilidade** (% de pipelines green)
2. **Top 10 mais instáveis** com causa, status, MR de fix
3. **Clusters de falha** (testes que falham juntos)
4. **Componentes mais afetados** (ranking por área)
5. **Tendência** (melhorando/piorando)
6. **Ações recomendadas:**
   - Tasks a criar (com título sugerido)
   - Tasks existentes que resolvem
   - Testes para skip temporário (>50% flakiness)
   - Seletores problemáticos a substituir

## Regras
- Ignorar pipelines canceladas
- Testes com >50% falha em >5 execuções = definitivamente flaky
- Testes com 100% falha = provavelmente bug real, não flaky
- Se teste passou a falhar APÓS um MR específico → identificar MR causador
- Formato sugerido de task: "QA - Estabilizar teste {nome_do_teste}"

## Output HTML
- Caminho: `.kiro/skills/test-health/reports/test-health-{data}.html`
- Tema dark, visual profissional
- IDs de tasks = links clicáveis para kanban
- MRs = links clicáveis para GitLab
