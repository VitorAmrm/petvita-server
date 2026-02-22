# UC-01 - Abrir Internamento

## Atores
- Veterinário
- Estagiário

## Descrição
Permite abrir um novo internamento para um animal existente.

## Pré-condições
- Animal deve estar cadastrado
- Usuário deve ter permissão de abertura

## Fluxo Principal
1. Usuário seleciona animal
2. Informa dados iniciais (peso, queixa, diagnóstico inicial)
3. Sistema cria INTERNAMENTO
4. Sistema cria automaticamente DIA_INTERNAMENTO com data atual

## Fluxos Alternativos
### 3A - Animal não cadastrado
- Sistema solicita cadastro no momento e retorna para cadastro do internamento

## Pós-condições
- Internamento ativo no sistema
- Dia inicial criado

## Regras de Negócio Relacionadas
- Internamento deve possuir pelo menos um veterinário vinculado