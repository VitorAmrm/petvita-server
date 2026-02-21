# UC-05 – Registrar Parâmetros Clínicos

## Atores
- Veterinário  
- Estagiário  

## Descrição
Permite registrar os valores dos parâmetros clínicos de um paciente internado, mantendo o histórico completo de medições.  
O sistema registra automaticamente o horário da medição e o usuário responsável, gerando auditoria se necessário.

## Pré-condições
- Paciente com internamento ativo  
- Usuário com permissão para registrar parâmetros clínicos  
- Parâmetros clínicos já definidos para o internamento  

## Fluxo Principal
1. Usuário acessa o internamento do paciente  
2. Sistema exibe a lista de parâmetros clínicos e suas últimas medições  
3. Usuário seleciona os parâmetros que deseja registrar  
4. Usuário informa os valores observados  
5. Sistema grava os valores e automaticamente registra:
   - Horário da medição  
   - Usuário responsável

## Pós-condições
- Valores dos parâmetros clínicos atualizados e historicamente registrados  
- Últimas medições exibidas para consulta  
- Auditoria gerada quando aplicável  

## Regras de Negócio
- Cada parâmetro clínico pode ter múltiplas medições durante o internamento  
- Veterinário pode registrar valores a qualquer momento  
- Estagiário só pode registrar dentro do tempo permitido  
- Auditoria automática para registros fora do limite pelo estagiário  