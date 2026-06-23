# Padrões de Relatórios HTML

## Todas as skills que geram relatórios DEVEM seguir estas regras:

### Padrão Visual
1. **Tema:** Background dark (#1a1a2e), texto claro (#e0e0e0)
2. **Cores de destaque:** Primário (#00d4aa), Info (#4fc3f7), Alerta (#ff9800), Erro (#ff5252), Sucesso (#69f0ae)
3. **Fonte:** System font stack (Segoe UI, Tahoma, Geneva, Verdana, sans-serif)
4. **Layout:** Responsivo, summary cards em grid

### Padrão de Conteúdo
1. **IDs de tasks** devem ser links clicáveis abrindo em nova aba (target=_blank)
2. **Referências a MRs** devem linkar para o GitLab
3. **Badges de prioridade** com cores (Crítica=vermelho, Alta=laranja, Média=amarelo, Baixa=verde)
4. **Footer** com nome da skill e data de geração
5. **Nomenclatura:** `{nome-skill}-{contexto}.html`

### Estrutura
- Cards de resumo no topo (métricas-chave)
- Tabelas detalhadas no meio
- Recomendações/ações no final
- Footer com metadados
