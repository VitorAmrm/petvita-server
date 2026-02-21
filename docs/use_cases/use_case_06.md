# UC-06 – Registrar Aplicação de Fármaco

## Atores
- Veterinário  
- Estagiário  

## Descrição
Permite registrar a administração de medicamentos prescritos a um paciente internado, incluindo horário da aplicação e usuário responsável.  
O sistema realiza auditoria automática se o registro for feito fora do tempo permitido.

## Pré-condições
- O paciente deve ter um internamento ativo  
- O medicamento deve estar prescrito para o paciente  
- Usuário deve ter permissão de registrar aplicações  

## Fluxo Principal
1. Usuário acessa o internamento do paciente  
2. Sistema mostra a lista de medicamentos prescritos e histórico de aplicações  
3. Usuário seleciona o medicamento a ser administrado  
4. Usuário confirma a aplicação do medicamento no horário atual  
5. Sistema registra a aplicação e atualiza o histórico de forma visível para todos os usuários autorizados  
6. Sistema verifica se a aplicação foi realizada dentro do tempo permitido:
   - Se sim, tudo ocorre normalmente  
   - Se não, sistema registra auditoria para revisão posterior  

## Fluxos Alternativos

### 6A – Aplicação fora do tempo recomendado
- Sistema registra aplicação normalmente  
- Marca registro como auditado  
- Gera alerta para revisão  

### 6B – Medicamento não prescrito
- Sistema impede aplicação  

## Pós-condições
- Aplicação do medicamento registrada  
- Histórico atualizado com informações de horário e usuário responsável  
- Auditoria gerada se necessário  

## Regras de Negócio
- Cada prescrição pode ter múltiplas aplicações durante o internamento  
- Veterinário pode aplicar medicamentos a qualquer momento  
- Estagiário só pode aplicar dentro do tempo permitido  
- Auditoria automática para aplicações fora do limite pelo estagiário  