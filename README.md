# 🛡️ Kiro QA Framework

> Framework de automação de Quality Assurance alimentado por IA, construído sobre o [Kiro IDE](https://kiro.dev). Skills são automações invocáveis que utilizam integrações MCP (Model Context Protocol) com GitLab, ferramentas de gestão de projetos e plataformas de observabilidade para entregar insights de qualidade em tempo real.

![Skills](https://img.shields.io/badge/skills-33-blue)
![MCP](https://img.shields.io/badge/MCP-GitLab%20%7C%20Kanban%20%7C%20Datadog-green)
![License](https://img.shields.io/badge/license-MIT-brightgreen)

---

## 🎯 O que é isso?

Uma coleção de **skills de QA orientadas por IA** que automatizam tarefas repetitivas de qualidade para times de desenvolvimento. Cada skill é um arquivo markdown que define um workflow — quando acionada via keyword no chat, o agente de IA executa análises multi-etapas combinando dados de múltiplas fontes.

**Feito para times que querem:**
- Visibilidade da saúde da sprint sem planilhas manuais
- Análise de risco de regressão automatizada antes de releases
- Monitoramento de estabilidade de testes com classificação de causa raiz
- Análise de escapes com sugestões de melhoria acionáveis
- Planning e retrospectivas baseados em dados reais

---

## 🏗️ Arquitetura

```
.kiro/
├── skills/                    # Definições de skills (uma pasta por skill)
│   ├── sprint-focus/
│   │   ├── SKILL.md          # Definição do workflow
│   │   └── reports/          # Relatórios HTML gerados
│   ├── test-health/
│   ├── delivery-metrics/
│   └── ...
├── steering/                  # Regras globais e comportamentos
│   ├── skills-html-reports.md # Padrões de output HTML
│   ├── token-efficiency.md    # Otimização de contexto
│   └── security.md           # Proteção de operações destrutivas
└── settings/
    └── mcp.json              # Configuração dos servidores MCP
```

### Como funciona

1. Usuário digita uma keyword no chat do Kiro (ex: `sprint-focus`)
2. Kiro carrega o SKILL.md e executa o workflow
3. O agente chama ferramentas MCP (API GitLab, API Kanban, API Datadog)
4. Dados são analisados, cruzados e classificados
5. Output é gerado como resumo no chat + relatório HTML

---

## 📋 Catálogo de Skills

### Sprint & Entrega

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `sprint-focus` | Sprint Focus | Progresso real do objetivo com burndown, blockers, projeção e recomendações priorizadas |
| `sprint-planning` | Sprint Planning | Cálculo de velocity, sugestão de capacidade, candidatos priorizados do backlog |
| `delivery-metrics` | Delivery Metrics | Throughput, cycle time, lead time, taxa de bugs entre sprints. Inclui modo retro (reverts, scope creep, ações) |
| `blocker-alert` | Blocker Alert | Detecta tasks paradas na mesma lane além dos thresholds, cruza com MRs no GitLab |
| `workload-balance` | Workload Balance | Distribuição de carga por dev, detecta sobrecarga/ociosidade, sugere redistribuição |
| `review-deck` | Review Deck | Preparação para Sprint Review: entregas agrupadas por tema, sugestões de demo, métricas |

### Qualidade & Testes

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `test-health` | Test Health | Análise completa de testes automatizados: classificação de falhas, score de flakiness, cruzamento com kanban, sugestões de estabilização |
| `escape-analysis` | Escape Analysis | Identifica bugs que escaparam para produção, causa raiz, taxa de escape, ações de melhoria |
| `qa-booster` | QA Booster | Analisa MR + task, avalia cobertura de testes, sugere cenários complementares (negativos, edge cases, regressão) |
| `mr-check` | MR Ready Check | Verifica se MR está pronto para merge (checklist, evidências, aprovações, pipeline, análise de regressão) |
| `preventive-qa` | Preventive QA | Prepara validações preventivas antes do desenvolvimento: cenários baseline, pós-fix, checklist do dev |
| `check-summary` | Check Summary | Compara snapshots de estado da aplicação gerando relatório de diff (erros corrigidos, novos, inalterados) |

### Risco & Segurança

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `regression-map` | Regression Map | Mapeia MRs recentes que podem causar regressão em um componente específico |
| `release-risk` | Release Risk | Analisa risco de release: MRs com alta probabilidade de regressão, componentes frágeis, validações extras |
| `tech-debt-radar` | Tech Debt Radar | Identifica dívida técnica acumulando: vulnerabilidades, deps desatualizadas, refactorings adiados |
| `bug-impact` | Bug Impact | Analisa impacto de um bug: qual MR causou, versões afetadas, clientes impactados, severidade sugerida |

### Conhecimento & Onboarding

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `onboarding` | Onboarding Dev | Contexto rápido sobre um componente: arquitetura, bugs recentes, armadilhas, MRs de referência |
| `code-review` | Code Review | Code Review seguindo padrões do time (segurança, performance, padrões React/Java) |
| `doc-gap` | Doc Gap | Identifica documentação desatualizada cruzando com MRs recentes que alteraram o componente |
| `extract-roteiros` | Extract Roteiros | Extrai roteiros de teste de MRs do GitLab e consolida em formato padronizado |

### Operações & Monitoramento

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `diagnose-client` | Diagnose Client | Diagnostica problemas reportados usando logs (Datadog), análise de HAR, versão e MRs recentes |
| `client-profile` | Client Profile | Perfil completo do cliente: histórico de chamados, padrões, ambiente, componentes afetados |
| `environment-health` | Environment Health | Verifica saúde de um ambiente: erros no Datadog, disponibilidade, estabilidade |
| `daily-digest` | Daily Digest | Resumo diário de atividades do board com prioridades |

### Backlog & Planejamento

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `backlog-health` | Backlog Health | Score de saúde do backlog: tasks sem estimate, épicos estagnados, candidatos para refinamento |
| `sprint-report` | Sprint Report | Relatório completo de qualidade da sprint em HTML (bugs, métricas, análise de causa, comparativo) |

### Utilitários

| Keyword | Skill | O que faz |
|---------|-------|-----------|
| `report-bug` | Report Bug | Gera título e descrição padronizada de bug para cadastro no kanban |
| `clean-reports` | Clean Reports | Apaga todos os HTMLs gerados pelas skills para preparar commits limpos |
| `patch-tracker` | Patch Tracker | Rastreia em quais branches/versões um fix foi liberado |
| `compare-versions` | Compare Versions | Compara diffs entre duas versões/branches do produto |

---

## 🚀 Como Começar

### Pré-requisitos

1. [Kiro IDE](https://kiro.dev) instalado
2. Servidores MCP configurados:
   - **GitLab MCP** — acesso aos repositórios
   - **Kanban/Task MCP** — acesso à ferramenta de gestão de projetos
   - **Datadog MCP** (opcional) — para skills de observabilidade

### Instalação

```bash
# Clone este repositório
git clone https://github.com/SEU_USUARIO/kiro-qa-framework.git

# Copie as skills para seu workspace
cp -r kiro-qa-framework/.kiro/ /seu/workspace/.kiro/
```

### Configuração

Edite `.kiro/settings/mcp.json` apontando para seus servidores:

```json
{
  "mcpServers": {
    "gitlab": {
      "command": "npx",
      "args": ["-y", "@anthropic/gitlab-mcp-server"],
      "env": {
        "GITLAB_TOKEN": "seu-token",
        "GITLAB_URL": "https://gitlab.sua-empresa.com"
      }
    }
  }
}
```

### Uso

No chat do Kiro, digite qualquer keyword de skill:

```
sprint-focus
test-health
delivery-metrics --retro
blocker-alert
```

---

## 📊 Exemplos de Output

### Sprint Focus
```
🎯 OBJETIVO: Implementar acúmulo de filtros nos portais
   Progresso: ████████░░░░ 38% (5/13)
   Sprint: 3 dias restantes

📉 BURNDOWN
   Real: 5/13 (38%) | Ideal: 71% (dia 10/14)
   Gap: -33% | Projeção: ~7/13 no fim

🔴 BLOQUEADOS
 • TASK-4084 — Revisar layout tabela → REVERTIDO hoje

🟡 EM ANDAMENTO
 • TASK-3790 — Acumular filtros → MR aberto, aguarda aprovação

💡 RECOMENDAÇÃO: Focar em desbloquear TASK-3790 (MR pronto para review)
```

### Test Health
```
🧪 Score: 85% ↑ Melhorando

Problemas identificados:
• Race condition no wizard → CORRIGIDO (helper centralizado)
• Seletores CSS hash → MIGRADOS para data-test-selector
• Migração de componente quebrou seletores → RISCO ATIVO

Ação: Decidir sobre seletores de tabela (reverter ou aguardar remerge)
```

### Escape Analysis
```
🐛 Taxa de escape: 14% (5 escapes / 35 MRs)

Distribuição por causa:
• 40% Correção anterior (regressão)
• 40% Ambiente/Config
• 20% Edge case não previsto

Meta próxima sprint: ≤10%
```

---

## 🧠 Princípios de Design

1. **Orientado por dados, não por opinião** — Todo insight é baseado em dados reais do GitLab, kanban e ferramentas de observabilidade
2. **Cruzar tudo** — Um bug não é só um bug: está conectado a um MR, uma sprint, um componente, um cliente
3. **Output acionável** — Todo relatório termina com ações concretas, não apenas dados
4. **Relatórios HTML para compartilhamento** — Tema dark, profissional, com links clicáveis para fácil compartilhamento com stakeholders
5. **Eficiente em tokens** — Desenhado para minimizar chamadas de API e uso de contexto via cache e delta-first
6. **Segurança primeiro** — Operações destrutivas sempre exigem confirmação explícita

---

## 🤝 Contribuindo

1. Fork este repositório
2. Crie uma skill seguindo o template SKILL.md
3. Teste no seu workspace
4. Envie um PR com:
   - O arquivo SKILL.md
   - Exemplo de output (screenshot ou HTML)
   - Descrição das dependências MCP

### Template de Skill

```markdown
# Nome da Skill — Descrição Curta

## Quando ativar
- `keyword` ou `keyword [parâmetro]`
- Gatilhos em linguagem natural

## Workflow
1. Etapa 1: Quais dados buscar
2. Etapa 2: Como processar
3. Etapa 3: O que cruzar
4. Etapa N: Gerar output

## Output
- O que o relatório contém
- Especificações de formato

## Output HTML
- Caminho: `.kiro/skills/{nome}/reports/{nome}-{contexto}.html`
- Tema dark, visual profissional
- Todos IDs de tasks = links clicáveis
```

---

## 📈 Resultados Alcançados

| Métrica | Antes | Depois |
|---------|-------|--------|
| Tempo de preparação do planning | ~2h manual | 5min (skill) |
| Análise de escapes | Arqueologia manual de MRs | Automatizado com causa raiz |
| Detecção de testes instáveis | Descoberto em produção | Detectado antes do merge |
| Retrospectivas | Baseadas em "feeling" | Baseadas em dados concretos |
| Análise de regressão pré-release | Manual, incompleta | Mapa completo em segundos |
| Saúde do backlog | Sem visibilidade | Score + ações de refinamento |

---

## 📄 Licença

MIT — Use, adapte, compartilhe.

---

## 👤 Autor

Construído por um QA Engineer que acredita que qualidade deve ser proativa, orientada por dados e automatizada. Estas skills representam soluções reais para desafios reais de qualidade em um time gerenciando 30+ sprints de um produto SaaS enterprise complexo.
