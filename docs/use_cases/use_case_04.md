# UC-04 – Registrar Retorno de Paciente

## Atores
- Veterinário
- Administrador

## Descrição
Permite iniciar um novo internamento para um animal que retorna à clínica após alta de internamento anterior, mantendo o histórico completo e criando um novo evento clínico independente.

## Pré-condições
- Animal deve estar cadastrado
- Usuário deve possuir permissão de abertura de internamento
- Histórico de internamentos anteriores disponível para consulta

## Fluxo Principal
1. Usuário busca o animal que retorna
2. Sistema exibe histórico de internamentos anteriores
3. Usuário seleciona “Novo Internamento”
4. Sistema cria novo registro de INTERNAMENTO independente
5. Sistema inicializa automaticamente o DIA_INTERNAMENTO com data atual
6. Sistema vincula veterinários e tutores conforme regras
7. Sistema disponibiliza os parâmetros clínicos padrão para preenchimento

## Fluxos Alternativos

### 3A – Paciente retorna no mesmo dia de internamento ativo
- Sistema informa que já existe internamento ativo
- Usuário pode optar por continuar no internamento existente
- Operação de criar novo internamento é bloqueada

### 4A – Tentativa de reabrir internamento antigo
- Sistema bloqueia operação
- Exibe mensagem orientando criar um novo internamento

### 2A – Usuário sem permissão
- Sistema bloqueia operação
- Exibe mensagem de acesso negado

## Pós-condições
- Novo internamento ativo criado
- Histórico anterior permanece intacto
- Sistema pronto para registrar novos parâmetros clínicos, prescrições e alimentação

## Regras de Negócio
- Cada internamento é um evento clínico fechado e independente
- Histórico anterior não pode ser sobrescrito
- Reinternações sempre devem criar um novo internamento
- Permissões de abertura devem ser respeitadas