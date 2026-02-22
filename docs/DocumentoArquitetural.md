# DOCUMENTO DE ARQUITETURA
# PetVita – petvita-server & petvita-front

Versão: 1.0  
Status: Em definição  
Escopo: Sistema de gestão de internamentos veterinários

---

# 1. VISÃO GERAL

O PetVita é um sistema clínico voltado para gerenciamento de internamentos veterinários 24h.

O sistema é composto por duas aplicações independentes:

- **petvita-server** — Backend REST em Java (Micronaut)
- **petvita-front** — Frontend SPA em Angular

Objetivos arquiteturais:

- Robustez
- Rastreabilidade
- Segurança
- Baixo custo inicial
- Evolução futura para SaaS

---

# 2. ARQUITETURA GERAL

Modelo cliente-servidor.

Fluxo:

1. Navegador acessa o petvita-front.
2. O frontend consome a API REST do petvita-server.
3. O backend persiste dados no PostgreSQL.
4. Arquivos são armazenados no Amazon S3.

---

# 3. PETVITA-SERVER (BACKEND)

## 3.1 Tecnologias

- Java 24
- Micronaut
- JPA / Hibernate
- PostgreSQL
- JWT
- Amazon S3 SDK
- Bean Validation
- OpenAPI
- Hibernate Envers
- Jeyzer Report
- OpenTelemetry
- Build Nativo
- Jib
- Micrometer

## 3.2 Estilo Arquitetural

Arquitetura em camadas:

- Controller
- Service
- Repository
- Database

Princípios:

- API stateless
- Separação de responsabilidades
- DTO pattern
- Soft delete
- Auditoria obrigatória
- RBAC (Role-Based Access Control)

## 3.3 Controle de Acesso

Perfis:

- ADMIN
- VETERINARIO
- ESTAGIARIO
- RECEPCIONISTA

Autenticação via JWT.

Header padrão:

Authorization: Bearer <token>

## 3.4 Regras Críticas

- Apenas um internamento ativo por animal.
- Reinternações geram novo registro.
- Aplicações atrasadas devem gerar alerta.
- Todo registro clínico deve armazenar:
  - Usuário responsável
  - Data/hora
- Exclusão é sempre lógica.

## 3.5 Persistência

Banco: PostgreSQL

Ambientes:

Produção:
- Amazon RDS PostgreSQL

Desenvolvimento:
- PostgreSQL (Supabase)

## 3.6 Armazenamento de Arquivos

Arquivos clínicos:

- Armazenados no Amazon S3
- Banco armazena apenas metadados:
  - Nome
  - URL
  - Tipo
  - Usuário responsável
  - Data de upload

Arquivos não são armazenados como BLOB.

## 3.7 Estrutura de Pacotes

- controller
- service
- repository
- entity
- dto
- mapper
- security
- config
- exception
- audit

---

# 4. PETVITA-FRONT (FRONTEND)

## 4.1 Tecnologias

- Angular
- TypeScript
- Angular Router
- HttpClient
- JWT Interceptor

## 4.2 Arquitetura

SPA (Single Page Application).

Estrutura:

- core
- shared
- features
  - internamentos
  - animais
  - exames
  - administracao

## 4.3 Responsabilidades

Frontend é responsável por:

- Interface do usuário
- Navegação
- Controle visual por perfil
- Exibição de alertas
- Consumo da API REST

Regra de negócio crítica permanece no backend.

---

# 5. AMBIENTES

## 5.1 Desenvolvimento

- Frontend: localhost:4200
- Backend: localhost:8080
- Banco: PostgreSQL (Supabase)
- Armazenamento: MinIO (opcional)

## 5.2 Produção

- Frontend: hospedagem estática ou S3
- Backend: EC2
- Banco: RDS PostgreSQL
- Arquivos: Amazon S3

---

# 6. ESCALABILIDADE FUTURA

Possíveis evoluções:

- Dockerização
- Kubernetes
- CI/CD
- Monitoramento
- Versionamento de API
- Logs centralizados

---

# 7. DECISÕES ARQUITETURAIS

- Soft delete obrigatório
- Backend centraliza regras críticas
- Arquivos externos ao banco
- Auditoria imutável
- Separação total entre frontend e backend

---

# 8. CONSIDERAÇÕES FINAIS

O PetVita foi projetado para uso interno inicial, com arquitetura preparada para futura comercialização.

A estrutura garante:

- Segurança
- Rastreabilidade
- Evolução controlada
- Manutenção simplificada

---

# 9. Auditoria e Versionamento de Dados

## 9.1 Objetivo

Garantir rastreabilidade completa das alterações realizadas em entidades clínicas estratégicas do sistema, assegurando:

- Histórico imutável  
- Identificação do usuário responsável  
- Registro de data e hora da operação  
- Preservação do histórico clínico  

A auditoria será implementada exclusivamente através do **Hibernate Envers**.

---

## 9.2 Estratégia Adotada

O sistema utilizará Hibernate Envers para:

- Versionar automaticamente entidades selecionadas  
- Registrar INSERT, UPDATE e DELETE  
- Permitir consulta histórica de estados anteriores  
- Garantir rastreabilidade sem sobrescrita destrutiva  

Não haverá mecanismo paralelo de auditoria.

---

## 9.3 Escopo da Auditoria

A auditoria será aplicada apenas às entidades estratégicas do domínio clínico:

- INTERNAMENTO  
- DIA_INTERNAMENTO  
- REGISTRO_CLINICO  
- VALOR_PARAMETRO  
- PRESCRICAO_FARMACO  
- APLICACAO_FARMACO  
- EXAMES_ADICIONAIS  

Entidades meramente cadastrais (ex: FARMACO, PARAMETRO_CLINICO, USUARIO) não serão versionadas.

---

## 9.4 Estrutura Técnica

Para cada entidade anotada com `@Audited`, o Envers criará automaticamente:

- Tabela `<ENTIDADE>_AUD`  
- Campo `REV` (identificador da revisão)  
- Campo `REVTYPE`:  
  - 0 = INSERT  
  - 1 = UPDATE  
  - 2 = DELETE  

---

## 9.5 Registro do Usuário da Revisão

Será implementado um `RevisionListener` customizado para capturar:

- ID do usuário autenticado (via contexto de segurança)  
- Timestamp da operação  

Será criada uma entidade de revisão personalizada contendo:

- revision_id  
- timestamp  
- usuario_id  

Isso garante rastreabilidade de quem realizou a alteração.

---

## 9.6 Exclusões

Mesmo utilizando Envers, o sistema continuará adotando:

- Soft delete para entidades clínicas  
- Campo de status para encerramento de internamento  

Envers registrará o evento de alteração normalmente.

---

## 9.7 Consulta de Histórico

O backend disponibilizará endpoints administrativos para:

- Consultar histórico de uma entidade específica  
- Recuperar versões anteriores  
- Visualizar alterações realizadas  

A visualização será restrita a perfis autorizados.

---

## 9.8 Considerações de Armazenamento

- O volume de dados crescerá proporcionalmente ao número de alterações  
- Apenas entidades estratégicas serão auditadas  
- Futuramente poderá ser aplicada política de arquivamento  

---

## 9.9 Segurança

- Registros de auditoria não poderão ser alterados manualmente  
- Apenas Administrador poderá acessar histórico completo  
- A auditoria não será exposta publicamente via API  

---

# Conclusão

A utilização do Hibernate Envers apenas em entidades estratégicas garante:

- Controle clínico robusto  
- Histórico confiável  
- Arquitetura limpa e previsível  
- Baixo acoplamento com regras de negócio  