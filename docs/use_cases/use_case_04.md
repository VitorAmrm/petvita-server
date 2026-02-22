# UC-04 - Atualizar Dados do Animal

## Atores
- Veterinário
- Administrador
- Recepcionista
- Estagiário

## Descrição
Permite atualizar informações cadastrais de um animal já registrado no sistema.

## Pré-condições
- Animal deve estar previamente cadastrado
- Usuário deve possuir permissão de edição

## Fluxo Principal
1. Usuário busca o animal pelo nome, registro ou tutor
2. Sistema exibe os dados atuais do animal
3. Usuário altera as informações desejadas (ex: raça, peso padrão, particularidades, status de bravo, registro, etc.)
4. Usuário confirma a atualização
5. Sistema valida os dados informados
6. Sistema salva as alterações
7. Sistema registra auditoria da modificação (usuário e data/hora)

## Fluxos Alternativos

### 1A - Animal não encontrado
- Sistema informa que o animal não está cadastrado

### 5A - Dados inválidos
- Sistema informa inconsistências
- Usuário deve corrigir antes de salvar

## Pós-condições
- Dados do animal atualizados no sistema
- Histórico de auditoria registrado

## Regras de Negócio Relacionadas
- Alterações não devem impactar internamentos já encerrados
- Sistema deve manter rastreabilidade de quem realizou a alteração
- Campos obrigatórios não podem ser removidos