# Matriz de Permissões – PetVita

| Funcionalidade | Administrador | Veterinário | Estagiário | Recepcionista |
|----------------|--------------|------------|------------|---------------|
| Login | ✅ | ✅ | ✅ | ✅ |
| Visualizar Internamentos Abertos | ✅ | ✅ | ✅ | ✅ |
| Visualizar Internamentos Encerrados | ✅ | ✅ | ❌ | ❌ |
| Criar Novo Internamento | ✅ | ✅ | ❌ | ❌ |
| Encerrar Internamento | ✅ | ✅ | ❌ | ❌ |
| Reabrir Internamento | ✅ | ❌ | ❌ | ❌ |
| Registrar Parâmetro Clínico | ✅ | ✅ | ✅* | ❌ |
| Editar Parâmetro Clínico | ✅ | ✅ | ✅* | ❌ |
| Prescrever Fármaco | ✅ | ✅ | ❌ | ❌ |
| Registrar Aplicação de Fármaco | ✅ | ✅ | ✅* | ❌ |
| Registrar Alimentação | ✅ | ✅ | ✅* | ❌ |
| Gerar PDF da Ficha | ✅ | ✅ | ❌ | ✅ |
| Gerenciar Usuários | ✅ | ❌ | ❌ | ❌ |
| Alterar Permissões | ✅ | ❌ | ❌ | ❌ |
| Criar/Editar Parâmetros Clínicos | ✅ | ✅ | ❌ | ❌ |
| Visualizar Auditorias | ✅ | ✅ | ❌ | ❌ |

---

## Observações

### Estagiário (*)
O estagiário pode:
- Registrar parâmetros clínicos  
- Registrar aplicação de fármacos  
- Registrar alimentação  

Restrições:
- Possui limite de tempo para registro  
- Registros fora do limite geram auditoria  
- Não pode encerrar ou reabrir internamentos  
- Não pode alterar estrutura clínica ou permissões  

---

## Regras Gerais

- Todas as ações exigem autenticação.
- A visualização e edição são controladas pelo perfil do usuário.
- Auditorias são registradas automaticamente quando aplicável.
- O acesso às funcionalidades deve ser validado tanto na interface quanto no backend.