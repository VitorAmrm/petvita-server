# UC-02 - Encerrar Internamento

## Atores
- Veterinário
- Administrador

## Descrição
Permite encerrar um internamento já existente para um animal.

## Pré-condições
- Internamento deve estar cadastrado
- Internamento deve estar com status ATIVO
- Usuário deve ter permissão de encerramento

## Fluxo Principal
1. Usuário solicita encerramento do internamento
2. Sistema deleta logicamente o internamento

## Fluxos Alternativos
### 3A - Internamento já encerrado
- Sistema deve apenas mostrar um erro

## Pós-condições
- Internamento permanece armazenado
- Status Encerrado
- Não permite novos registros clinicos