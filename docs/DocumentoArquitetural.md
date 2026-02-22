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

- Java 21
- Micronaut
- JPA / Hibernate
- PostgreSQL
- JWT
- Amazon S3 SDK
- Bean Validation
- OpenAPI

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

- Multi-clínica (multi-tenant)
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