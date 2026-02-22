# DOCUMENTO DE REGRAS DE NEGÓCIO (DRN)
# PetVita :dog:

Versão: 1.0  
Status: Em definição  
Escopo: Core clínico de internamentos

---

# 1. REGRAS GERAIS DO SISTEMA

RN-01 – O sistema deve operar com controle de acesso baseado em perfis.

RN-02 – Todo registro clínico deve possuir rastreabilidade de:
- Usuário responsável
- Data e hora da operação

RN-03 – Exclusões devem ser lógicas (soft delete), preservando histórico.

RN-04 – O sistema não deve permitir sobrescrita destrutiva de dados clínicos já registrados.

RN-05 – Auditoria deve ser obrigatória para alterações fora da janela permitida.

---

# 2. REGRAS RELACIONADAS AO ANIMAL

RN-06 – Um animal pode possuir múltiplos tutores.

RN-07 – Deve existir um tutor principal por animal.

RN-08 – Alterações cadastrais do animal não devem afetar historicamente internamentos encerrados.

RN-09 – Animal deve ser cadastrado junto com a abertura do internamento.

---

# 3. REGRAS DE INTERNAMENTO

RN-10 – Cada internamento representa um evento clínico independente.

RN-11 – Reinternações devem gerar um novo internamento.

RN-12 – Não é permitido abrir mais de um internamento ativo para o mesmo animal.

RN-13 – Ao abrir um internamento, o sistema deve criar automaticamente o primeiro dia de internamento.

RN-14 – Internamento deve possuir pelo menos um veterinário vinculado.

RN-15 – Encerramento de internamento deve ser lógico (alteração de status).

---

# 4. REGRAS DE PARÂMETROS CLÍNICOS

RN-16 – Parâmetros clínicos devem ser configuráveis em tempo de execução.

RN-17 – Parâmetros podem possuir:
- Tipo numérico
- Texto
- Booleano
- Data/Hora
- Lista de opções (combobox)

RN-18 – Parâmetros podem possuir limites mínimos e máximos configuráveis.

RN-19 – Cada medição deve registrar:
- Valor
- Horário real da medição
- Usuário responsável

RN-20 – Não haverá agendamento fixo de horários para parâmetros.

---

# 5. REGRAS DE FARMACOS E PRESCRIÇÕES

RN-21 – Prescrição define como o medicamento deve ser administrado (dose, via, frequência).

RN-22 – Aplicação do fármaco deve ser registrada individualmente.

RN-23 – Cada aplicação deve registrar:
- Horário programado
- Horário real
- Usuário que aplicou

RN-24 – Sistema deve identificar automaticamente aplicações:
- Atrasadas
- Próximas do horário

RN-25 – Alertas devem ser exibidos no painel dos usuários autorizados.

---

# 6. REGRAS DE ALIMENTAÇÃO

RN-26 – Cada dia de internamento possui um único registro de alimentação.

RN-27 – Alimentação deve registrar:
- Tipo de alimento
- Volume
- RED
- Kcal/dia

---

# 7. REGRAS DE EXAMES COMPLEMENTARES

RN-28 – Exames devem estar vinculados a um internamento.

RN-29 – Arquivos de exames não devem ser armazenados no banco de dados.

RN-30 – Arquivos devem ser armazenados em repositório externo seguro.

RN-31 – Sistema deve manter registro do usuário responsável pelo upload.

RN-32 – Exclusão de exame deve ser lógica.

---

# 8. REGRAS DE EXPORTAÇÃO

RN-33 – Sistema deve permitir geração de ficha clínica em PDF.

RN-34 – Documento exportado deve refletir dados consolidados do internamento.

RN-35 – Exportação não deve alterar estado do sistema.

---

# 9. REGRAS DE SEGURANÇA E PERFIS

RN-36 – Administrador possui acesso total.

RN-37 – Veterinário pode:
- Gerenciar internamentos
- Prescrever
- Registrar parâmetros
- Visualizar exames
- Acompanhar estagiários

RN-38 – Estagiário pode:
- Registrar parâmetros
- Registrar aplicações
- Visualizar internamentos ativos
- Editar dentro do limite temporal

RN-39 – Recepcionista pode:
- Visualizar internamentos ativos
- Gerar PDF da ficha
- Gerenciar cadastro básico

---

# 10. REGRAS DE AUDITORIA

RN-40 – Sistema deve manter trilha de auditoria para:
- Alterações clínicas
- Exclusões lógicas
- Substituição de arquivos
- Aplicações atrasadas

RN-41 – Auditoria não pode ser removida manualmente.

---