# UC-09 – Autenticar Usuário (Login)

## Atores
- Administrador  
- Veterinário  
- Estagiário  
- Recepcionista  

## Descrição
Permite que um usuário acesse o sistema mediante credenciais válidas.  
Após autenticação, o sistema direciona o usuário para o painel correspondente ao seu perfil de acesso.

## Pré-condições
- Usuário deve estar previamente cadastrado  
- Usuário deve estar ativo no sistema  

## Fluxo Principal
1. Usuário acessa a tela de login  
2. Usuário informa e-mail e senha  
3. Sistema valida as credenciais  
4. Sistema identifica o perfil (role) do usuário  
5. Sistema redireciona o usuário para o painel correspondente  

## Fluxos Alternativos

### 3A – Credenciais inválidas
- Sistema exibe mensagem “Usuário ou senha inválidos”  
- Permite nova tentativa  

### 3B – Usuário inativo
- Sistema bloqueia acesso  
- Exibe mensagem “Usuário desativado”  

## Pós-condições
- Usuário autenticado com sessão ativa  
- Painel carregado conforme perfil  

## Regras de Negócio
- Apenas usuários ativos podem autenticar  
- O sistema deve registrar log de acesso (data, hora e usuário)  
- O acesso às funcionalidades é determinado pelo perfil do usuário  