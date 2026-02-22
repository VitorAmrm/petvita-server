# UC-12 – Acessar Painel do Estagiário

## Ator
- Estagiário

## Descrição
Permite ao estagiário acessar internamentos ativos e registrar informações clínicas conforme permissões.

## Funcionalidades Disponíveis
- Visualizar internamentos ativos
- Registrar parâmetros clínicos
- Registrar aplicações de fármacos
- Registrar alimentação (se permitido)
- Consultar histórico do internamento

## Restrições
- Não pode encerrar ou reabrir internamentos
- Não pode alterar permissões
- Registros fora do tempo permitido geram auditoria

## Regras de Negócio
- Só pode visualizar internamentos abertos
- Registros podem ser auditados automaticamente