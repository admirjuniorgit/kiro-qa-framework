# Sprint Focus — Progresso Real do Objetivo da Sprint

## Quando ativar
- `sprint-focus` ou `sprint-focus [nome-da-sprint]`
- "como está o objetivo da sprint", "prioridades da sprint", "foco da sprint"

## Workflow

### 1. Identificar Sprint e Workspace
- Buscar sprint ativa na ferramenta de gestão
- Obter detalhes do workspace (lanes, steps, tipos de task)

### 2. Buscar Task de Objetivo
- Procurar task do tipo "Objective" na sprint ativa
- Parsear descrição para extrair IDs das tasks que compõem o objetivo

### 3. Consultar Status REAL de Cada Task
- Para cada task ID: buscar lane/step atual no board
- Mapear para: ✅ Concluída | 🟡 Em Andamento | ⚪ Não Iniciada | 🔴 Bloqueada

### 4. Cruzar com GitLab (MRs)
- Para cada task em andamento: buscar MR relacionado
- Detectar: MR aberto → "em code review" | MR merged → "aguardando QA" | MR revertido → "⚠️ REVERTIDO"

### 5. Buscar Tasks FORA do Objetivo
- Buscar todas tasks não-done da sprint
- Filtrar: tasks que NÃO pertencem ao objetivo = bugs/extras puxados
- Classificar por prioridade (critical > high > medium > low)

### 6. Burndown e Projeção (integrado)
- Calcular total de itens vs concluídos
- Comparar real vs ideal (total ÷ dias da sprint)
- Projetar: "no ritmo atual, fecharemos X/Y itens"
- Detectar estagnação (dias consecutivos sem conclusão)

### 7. Gerar Output

```
═══ SPRINT FOCUS — {nome_sprint} ═══

🎯 OBJETIVO: {título}
   Progresso: {barra} {X}% ({done}/{total})
   Sprint: {dias restantes} dias restantes

📉 BURNDOWN
   Real: {done}/{total} ({pct}%) | Ideal: {ideal_pct}%
   Gap: {gap}% | Projeção: ~{projetado}/{total}

🔴 BLOQUEADOS / REVERTIDOS (ação imediata)
 • TASK-XXXX — {título} → {motivo}

🟡 EM ANDAMENTO
 • TASK-XXXX — {título} → {status MR} | {responsável}

⚪ NÃO INICIADOS (risco se não começar logo)
 • TASK-XXXX — {título}

🐛 BUGS PUXADOS: {N}
 • TASK-XXXX — {título} | Prioridade: {X}

💡 RECOMENDAÇÃO
 • {Sugestão acionável baseada no estado atual}
```

## Regras
- Status vem SEMPRE do board (lane/step real), nunca do texto da descrição
- Descrição do objetivo serve apenas para identificar QUAIS tasks pertencem a ele
- Excluir containers (is_container=true) e rejeitados das métricas
- Se uma task foi revertida no GitLab, marcar como 🔴 mesmo que o board diga "Done"
- Ordem de prioridade: Bloqueados > Em andamento sem MR > Em andamento com MR > Não iniciados

## Output HTML
- Caminho: `.kiro/skills/sprint-focus/reports/sprint-focus-{sprint-name}.html`
- Tema dark, visual profissional
- Todos IDs de tasks = links clicáveis para kanban (target=_blank)
