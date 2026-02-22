# UC-16 – Excluir Exame Complementar

## Atores
- Administrador

## Descrição
Permite excluir logicamente um exame registrado em um internamento.

## Pré-condições
- Exame deve estar cadastrado
- Usuário deve possuir permissão de exclusão

## Fluxo Principal

1. Usuário acessa o exame
2. Seleciona “Excluir”
3. Sistema solicita confirmação
4. Usuário confirma
5. Sistema marca o exame como inativo
6. Sistema registra auditoria da operação

## Fluxos Alternativos

### 3A – Cancelamento da operação
- Sistema mantém exame ativo

### 1A – Usuário sem permissão
- Sistema bloqueia operação

## Pós-condições
- Exame não aparece mais na listagem padrão
- Registro permanece no histórico para auditoria