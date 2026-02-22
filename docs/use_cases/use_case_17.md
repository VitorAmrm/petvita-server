# UC-17 – Substituir Arquivo de Exame

## Atores
- Veterinário  
- Administrador  

## Descrição
Permite substituir o arquivo digital de um exame já registrado, mantendo histórico de alteração.

## Pré-condições
- Exame deve estar ativo
- Usuário deve possuir permissão de edição

## Fluxo Principal

1. Usuário acessa o exame
2. Seleciona “Substituir Arquivo”
3. Sistema solicita novo upload
4. Usuário envia novo arquivo
5. Sistema valida o arquivo
6. Sistema atualiza o arquivo vinculado
7. Sistema registra auditoria da alteração

## Fluxos Alternativos

### 4A – Arquivo inválido
- Sistema bloqueia envio

### 1A – Usuário sem permissão
- Sistema bloqueia operação

## Pós-condições
- Novo arquivo associado ao exame
- Histórico de alteração registrado