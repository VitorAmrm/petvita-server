# UC-13 – Visualizar Exame Complementar

## Atores
- Veterinário  
- Administrador  
- Estagiário (somente visualização)

## Descrição
Permite visualizar a lista de exames vinculados a um internamento e acessar o arquivo associado.

## Pré-condições
- Internamento deve existir
- Usuário deve ter permissão de visualização

## Fluxo Principal

1. Usuário acessa o internamento
2. Sistema exibe lista de exames registrados
3. Usuário seleciona um exame
4. Sistema exibe:
   - Tipo do exame
   - Data
   - Observações
   - Usuário responsável pelo registro
5. Usuário pode clicar em “Visualizar” ou “Baixar”
6. Sistema disponibiliza o arquivo armazenado

## Fluxos Alternativos

### 2A – Nenhum exame cadastrado
- Sistema exibe mensagem informativa

### 1A – Usuário sem permissão
- Sistema bloqueia operação

## Pós-condições
- Exame permanece inalterado