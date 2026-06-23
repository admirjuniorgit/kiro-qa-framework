# Steering de Segurança — Operações Destrutivas

## Regra
NENHUMA operação destrutiva pode ser executada sem confirmação explícita do usuário.

## Operações que exigem confirmação
- Deleção de arquivos
- Deleção de dados
- Sobrescrita de arquivos existentes
- Push/commit para repositório
- Alteração de permissões
- Operações em produção
- Alteração de configurações

## Protocolo

```
⚠️ OPERAÇÃO DESTRUTIVA
Ação: [descrever o que será feito]
Risco: [descrever o que pode dar errado]
Reversível: [Sim/Não — como reverter se sim]

Confirma? (sim/não)
```

## Operações seguras (não exigem confirmação)
- Leitura de arquivos
- Buscas (somente leitura)
- Geração de arquivos NOVOS
- Análises sem alteração
- Consultas no kanban
