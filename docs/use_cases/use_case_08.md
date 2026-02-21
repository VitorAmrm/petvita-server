# UC-08 – Exportar Ficha do Paciente em PDF

## Atores
- Veterinário  
- Administrador  
- Estagiário
- Recepcionista

## Descrição
Permite gerar e baixar um relatório completo do paciente em PDF, incluindo histórico de internamentos, parâmetros clínicos, aplicações de fármacos, alimentação diária e observações.  
O PDF organiza os dados por dia de internamento, mostrando **últimas medições e registros** de forma clara e cronológica.

## Pré-condições
- Paciente com pelo menos um internamento registrado  
- Usuário deve ter permissão de acesso ao histórico e de gerar relatórios  

## Fluxo Principal
1. Usuário acessa a ficha do paciente  
2. Sistema exibe a opção “Exportar Ficha em PDF”  
3. Usuário seleciona o internamento ou período desejado para o relatório  
4. Sistema gera o PDF contendo:
   - Histórico de internamentos  
   - Últimas medições de parâmetros clínicos por dia  
   - Aplicações de fármacos com horários e doses  
   - Alimentação diária registrada  
   - Observações e alertas do sistema  
5. Sistema disponibiliza o PDF para download  
6. Usuário salva ou imprime o arquivo conforme necessidade  

## Fluxos Alternativos

### 4A – Usuário sem permissão
- Sistema bloqueia acesso  
- Exibe mensagem “Acesso negado”  

### 6A – Internamento inexistente
- Sistema informa que não existem registros para o período selecionado  


## Pós-condições
- PDF do paciente gerado e disponível para download  
- Histórico completo permanece intacto no sistema  
- Usuário pode consultar ou imprimir o relatório  

## Regras de Negócio
- Cada PDF deve refletir os dados mais atualizados do paciente  
- Usuário sem permissão não pode gerar ou baixar a ficha  
- Auditoria e histórico do sistema não são afetados durante a geração do PDF  
- Relatório deve ser legível, organizado por dia de internamento e tipo de registro  