# UC-07 – Registrar Alimentação

## Atores
- Veterinário  
- Estagiário  

## Descrição
Permite registrar a alimentação diária de um paciente internado. Cada registro corresponde a um **dia de internamento**, incluindo tipo de alimento, volume, calorias e observações.  
O sistema registra automaticamente o horário do lançamento e o usuário responsável.

## Pré-condições
- Paciente com internamento ativo  
- Usuário com permissão para registrar alimentação  
- Dia de internamento ativo disponível para registro  

## Fluxo Principal
1. Usuário acessa o internamento do paciente  
2. Sistema exibe histórico de alimentação diária já registrada  
3. Usuário seleciona o dia de internamento a ser registrado  
4. Usuário informa os detalhes da alimentação:
   - Tipo de alimento  
   - Volume fornecido  
   - Red, kcal/dia ou observações adicionais  
5. Sistema grava o registro, incluindo automaticamente:
   - Horário do registro  
   - Usuário responsável  
6. Sistema atualiza histórico de alimentação diária do paciente  

## Fluxos Alternativos

### 6A – Valor inconsistente ou incompleto
- Sistema alerta sobre campos faltantes ou valores fora do padrão  
- Usuário pode corrigir antes de salvar  

## Pós-condições
- Registro de alimentação diária adicionado ou atualizado  
- Histórico diário atualizado e visível para consulta  

## Regras de Negócio
- Cada dia de internamento possui no máximo **um registro de alimentação**  
- Veterinário pode registrar alimentação a qualquer momento  
- Estagiário deve respeitar limites de registro definidos pelo sistema  
- Histórico de alimentação nunca é perdido, apenas atualizado com novos registros ou correções  