# UC-18 – Listar Exames por Internamento

## Atores
- Veterinário  
- Administrador  
- Estagiário  
- Recepcionista

## Descrição
Permite visualizar todos os exames vinculados a um internamento específico.

## Pré-condições
- Internamento deve existir
- Usuário deve possuir permissão de visualização

## Fluxo Principal

1. Usuário acessa o internamento
2. Sistema exibe seção “Exames”
3. Sistema lista:
   - Tipo do exame
   - Data
   - Usuário responsável
   - Status
4. Usuário pode selecionar exame para visualizar detalhes

## Fluxos Alternativos

### 2A – Nenhum exame registrado
- Sistema exibe mensagem informativa

### 1A – Usuário sem permissão
- Sistema bloqueia operação

## Pós-condições
- Nenhuma alteração nos dados