# UC-03 – Reabrir Internamento

## Atores
- Administrador

## Descrição
Permite reabrir um internamento previamente encerrado, exclusivamente para correção administrativa ou continuidade excepcional do atendimento, mantendo rastreabilidade completa da ação.

## Pré-condições
- Internamento deve existir
- Internamento deve estar com status **ENCERRADO**
- Usuário autenticado deve possuir permissão de reabertura
- Justificativa obrigatória deve ser informada

## Fluxo Principal
1. Administrador acessa o histórico do animal
2. Sistema exibe internamentos encerrados
3. Administrador seleciona um internamento encerrado
4. Administrador solicita reabertura
5. Sistema solicita justificativa obrigatória
6. Administrador informa justificativa
7. Sistema valida consistência do registro
8. Sistema altera status para **REABERTO**
9. Sistema registra log contendo:
   - Usuário responsável
   - Data e hora
   - Justificativa informada
10. Sistema libera novamente registros clínicos para o internamento

## Fluxos Alternativos

### 7A – Internamento não está encerrado
- Sistema informa que apenas internamentos encerrados podem ser reabertos
- Operação cancelada

### 6A – Justificativa não informada
- Sistema impede continuidade
- Solicita preenchimento obrigatório

## Pós-condições
- Internamento passa para status **REABERTO**
- Registro de auditoria persistido
- Histórico anterior permanece intacto

## Regras de Negócio
- Reabertura deve ser considerada um **evento excepcional**
- Toda reabertura deve ser **auditável**
- Justificativa é **obrigatória**