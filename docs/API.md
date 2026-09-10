# ARQUITETURA

## 1. Visão Geral

O projeto será construído como uma aplicação full-stack utilizando Next.js sobre Node.js.

Frontend e backend permanecerão no mesmo projeto durante a primeira fase.

## 2. Objetivo Arquitetural

Manter o projeto simples para desenvolvimento acadêmico, mas organizado o suficiente para:

- dividir responsabilidades;
- facilitar manutenção;
- permitir trabalho em equipe;
- evitar lógica excessiva dentro das rotas;
- permitir evolução futura.

## 3. Fluxo Geral

```text
Cliente
  ↓
Interface Next.js
  ↓
Route Handler
  ↓
Validação / DTO
  ↓
Service
  ↓
Repository
  ↓
Banco de Dados
  ↓
Resposta
```

## 4. Responsabilidades

### Route Handler

Responsável por:

- receber requisição HTTP;
- ler parâmetros;
- receber body;
- chamar validação;
- chamar service;
- devolver resposta HTTP.

Não deve concentrar regra de negócio complexa.

### DTO

Representa os dados esperados para entrada ou saída.

### Validator

Valida formato e obrigatoriedade dos dados.

### Service

Concentra regras de aplicação e casos de uso.

Exemplos:

- cadastrar usuário;
- solicitar inscrição;
- formar equipe;
- cancelar evento.

### Repository

Responsável pela comunicação com a camada de persistência.

Exemplos:

- buscar usuário por e-mail;
- buscar evento por id;
- salvar equipe;
- listar inscrições.

### Model / Entity

Representa estruturas persistidas ou conceitos centrais do domínio.

## 5. Organização Inicial

```text
src/
├── app/
│   ├── api/
│   └── ...
├── services/
├── repositories/
├── models/
├── dto/
├── validators/
├── utils/
└── config/
```

A estrutura poderá ser refinada durante a implementação.

## 6. Arquitetura Monolítica

A escolha inicial é manter um único projeto.

Motivos:

- menor complexidade;
- facilidade de configuração;
- deploy mais simples;
- menor curva de aprendizado;
- melhor adequação ao contexto acadêmico.

Microservices não fazem parte da primeira fase.
