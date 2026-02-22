# UC-14 – Registrar Exame Complementar

## Atores
- Veterinário  
- Administrador  
- Estagiário

## Descrição
Permite registrar exames complementares vinculados a um internamento ativo, incluindo upload de arquivo digital (PDF) para armazenamento seguro e consulta posterior.

## Pré-condições
- Internamento deve estar ativo  
- Usuário deve possuir permissão de registro de exame  
- Arquivo deve estar em formato permitido (ex: PDF)  

## Fluxo Principal

1. Usuário acessa o internamento do paciente  
2. Usuário seleciona a opção “Adicionar Exame”  
3. Sistema solicita:
   - Tipo do exame (ex: Ultrassom, Hemograma, Bioquímica etc.)
   - Data do exame
   - Observações
   - Upload do arquivo (PDF)
4. Usuário envia o formulário
5. Sistema:
   - Valida o arquivo
   - Realiza upload para armazenamento externo
   - Registra os dados do exame
   - Associa o exame ao internamento
   - Registra o usuário responsável
6. Sistema confirma o registro com sucesso

## Fluxos Alternativos

### 4A – Arquivo inválido
- Sistema bloqueia envio
- Exibe mensagem informando formato não permitido

### 4B – Falha no upload
- Sistema informa erro de envio
- Nenhum registro parcial é salvo

### 1A – Internamento encerrado
- Sistema pode permitir registro apenas para histórico,
  conforme política da clínica

### 2A – Usuário sem permissão
- Sistema bloqueia operação
- Exibe mensagem de acesso negado

## Pós-condições
- Exame registrado no sistema
- Arquivo armazenado de forma segura
- Exame disponível para visualização e download

## Regras de Negócio
- Exames são sempre vinculados a um internamento
- Não é permitido sobrescrever exames existentes
- Exclusão deve seguir política de auditoria
- Arquivos não são armazenados diretamente no banco de dados
- Sistema deve manter rastreabilidade de quem realizou o upload