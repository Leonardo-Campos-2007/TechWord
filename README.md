# Plataforma de Eventos e Hackathons de Tecnologia

## 1. Sobre o Projeto

Este projeto consiste no desenvolvimento de uma plataforma voltada à centralização, descoberta, organização e participação em eventos de tecnologia e hackathons.

A proposta é reunir, em um único ambiente, funcionalidades que normalmente ficam distribuídas entre diferentes sites, formulários, redes sociais e ferramentas externas.

A plataforma deverá permitir que usuários encontrem eventos, realizem inscrições, acompanhem programações, participem de hackathons, formem equipes, enviem projetos, consultem resultados e mantenham um histórico de participação e conquistas.

Empresas também poderão utilizar a plataforma para organizar eventos, publicar hackathons, administrar participantes, configurar atividades, divulgar patrocinadores e se comunicar com o público.

---

# 2. Problema

Atualmente, informações sobre eventos de tecnologia e hackathons costumam ficar espalhadas entre diferentes canais.

Um participante pode precisar utilizar:

* redes sociais para descobrir o evento;
* formulários externos para se inscrever;
* grupos de mensagens para receber atualizações;
* páginas separadas para consultar programação;
* outras plataformas para formar equipes;
* links externos para enviar projetos;
* diferentes canais para acompanhar resultados.

Essa fragmentação dificulta a experiência do participante e também aumenta a complexidade de gerenciamento para os organizadores.

---

# 3. Solução

A plataforma busca centralizar todo o ciclo de um evento tecnológico.

O usuário poderá utilizar um único ambiente para:

```text
descobrir evento
        ↓
consultar informações
        ↓
realizar inscrição
        ↓
acompanhar programação
        ↓
participar de atividades
        ↓
participar de hackathon
        ↓
formar equipe
        ↓
enviar projeto
        ↓
acompanhar resultado
        ↓
receber conquistas
        ↓
manter histórico no perfil
```

Para empresas e organizadores, a plataforma deverá permitir:

```text
cadastrar empresa
        ↓
obter verificação
        ↓
criar evento
        ↓
enviar para aprovação
        ↓
publicar evento
        ↓
gerenciar inscrições
        ↓
organizar programação
        ↓
configurar hackathon
        ↓
administrar resultados
        ↓
emitir conquistas
        ↓
comunicar participantes
```

---

# 4. Objetivo Geral

Desenvolver uma plataforma centralizada para eventos e hackathons de tecnologia, facilitando a conexão entre participantes, empresas, organizadores e patrocinadores.

---

# 5. Objetivos Específicos

O projeto busca permitir:

* cadastro e autenticação de usuários;
* criação de perfis públicos;
* cadastro e verificação de empresas;
* criação e aprovação de eventos;
* descoberta e busca de eventos;
* inscrição de participantes;
* controle de vagas;
* lista de espera;
* programação de eventos;
* trilhas e atividades;
* check-in;
* criação de hackathons;
* definição de fases;
* publicação de desafios;
* formação de equipes;
* submissão de projetos;
* versionamento de submissões;
* avaliações;
* resultados;
* rankings;
* emblemas;
* certificados;
* páginas de empresas;
* patrocinadores;
* estandes;
* ofertas;
* comunicados;
* notificações.

---

# 6. Público-Alvo

A plataforma possui três grupos principais de usuários.

## 6.1 Participantes

Pessoas interessadas em:

* tecnologia;
* hackathons;
* palestras;
* workshops;
* networking;
* competições;
* desenvolvimento profissional.

---

## 6.2 Empresas e Organizadores

Organizações interessadas em:

* publicar eventos;
* organizar hackathons;
* administrar participantes;
* divulgar atividades;
* formar comunidades;
* atrair talentos;
* apresentar produtos;
* promover desafios.

---

## 6.3 Administradores da Plataforma

Responsáveis por:

* analisar empresas;
* aprovar ou rejeitar verificações;
* analisar eventos;
* aprovar ou rejeitar eventos;
* manter a integridade operacional da plataforma.

---

# 7. Escopo Atual

A primeira fase contempla os módulos principais da plataforma.

## Usuários

* cadastro;
* login;
* logout;
* edição de conta;
* perfil público;
* tecnologias;
* áreas de interesse;
* links profissionais.

## Empresas

* cadastro;
* página pública;
* edição;
* verificação;
* selo de empresa verificada.

## Eventos

* criação;
* rascunho;
* aprovação;
* publicação;
* edição;
* cancelamento;
* capacidade;
* modalidade;
* busca e filtros.

## Inscrições

* inscrição;
* aprovação manual;
* rejeição;
* cancelamento;
* confirmação;
* controle de vagas;
* lista de espera.

## Programação

* trilhas;
* atividades;
* horários;
* capacidade das atividades;
* inscrição específica;
* check-in.

## Hackathons

* configuração;
* participação individual;
* participação por equipe;
* fases;
* desafios;
* equipes;
* convites;
* solicitações de entrada;
* submissões;
* versões;
* avaliações;
* resultados;
* rankings.

## Conquistas

* emblemas;
* certificados;
* colocações;
* histórico no perfil.

## Empresas e Patrocinadores

* patrocinadores;
* categorias de patrocínio;
* estandes;
* ofertas;
* desafios patrocinados.

## Comunicação

* comunicados;
* notificações;
* preferências de notificação.

---

# 8. Funcionalidades Futuras

Algumas funcionalidades fazem parte da visão do produto, mas não pertencem ao escopo inicial.

Entre elas:

```text
Carteira interna do evento

Créditos

Saldo

Compras internas

Transações

Estornos

Sistema interno de pagamentos

Recomendações inteligentes

Analytics avançado
```

Essas funcionalidades somente deverão ser incorporadas após definição formal de requisitos, regras de negócio, entidades, endpoints e testes próprios.

---

# 9. Tecnologias

A stack inicial definida para o projeto é:

## Linguagem

```text
JavaScript
```

## Runtime

```text
Node.js
```

## Framework

```text
Next.js
```

## Frontend

```text
Next.js
React
HTML
CSS
JavaScript
```

## Backend

```text
Next.js
Route Handlers
Node.js
```

---

# 10. Arquitetura

A aplicação utilizará inicialmente uma arquitetura:

```text
Full-stack monolítica
```

Frontend e backend permanecerão no mesmo projeto Next.js.

Fluxo conceitual principal:

```text
Cliente
   ↓
Route Handler
   ↓
DTO
   ↓
Validator
   ↓
Service
   ↓
Repository
   ↓
Persistência
```

Retorno:

```text
Persistência
   ↓
Repository
   ↓
Service
   ↓
Route Handler
   ↓
Resposta HTTP
   ↓
Cliente
```

A arquitetura foi escolhida para manter o projeto simples, organizado e adequado ao contexto acadêmico.

---

# 11. Tecnologias Ainda Não Definidas

Algumas decisões serão tomadas antes da implementação dos módulos que dependem delas.

```text
Banco de dados

ORM

Biblioteca de validação

Estratégia de autenticação

Estratégia de autorização

Armazenamento de imagens

Hospedagem

Deploy
```

Essas tecnologias não devem ser presumidas antes da decisão da equipe.

---

# 12. Estrutura da Documentação

A documentação do projeto está organizada da seguinte forma:

```text
docs/
│
├── REQUISITOS.md
├── REGRAS-DE-NEGOCIO.md
├── MODELO-DE-DADOS.md
├── ARQUITETURA.md
├── GUIA-CICLO-ENDPOINT.md
├── API.md
├── TESTES-POSTMAN.md
├── BACKLOG.md
├── SPRINTS.md
└── MAPA-FASE-1.md
```

---

# 13. Função de Cada Documento

## `REQUISITOS.md`

Define:

```text
o que o sistema precisa oferecer
```

Contém:

* requisitos funcionais;
* requisitos não funcionais.

---

## `REGRAS-DE-NEGOCIO.md`

Define:

```text
como o domínio deve se comportar
```

Contém:

* restrições;
* permissões;
* condições;
* estados;
* comportamentos esperados.

---

## `MODELO-DE-DADOS.md`

Define:

```text
quais informações existem e como se relacionam
```

Contém:

* entidades;
* atributos;
* relacionamentos;
* cardinalidades;
* estados.

---

## `ARQUITETURA.md`

Define:

```text
como a aplicação será organizada tecnicamente
```

Contém:

* camadas;
* responsabilidades;
* módulos;
* fluxo de requisição;
* persistência;
* dependências.

---

## `GUIA-CICLO-ENDPOINT.md`

Funciona como guia prático para a equipe.

Explica:

```text
Route Handler

DTO

Validator

Service

Repository

Model / Entity
```

e demonstra o ciclo completo de um endpoint.

---

## `API.md`

Define:

```text
o contrato HTTP da aplicação
```

Contém:

* métodos;
* rotas;
* parâmetros;
* bodies;
* respostas;
* códigos HTTP.

---

## `TESTES-POSTMAN.md`

Define:

```text
como validar os endpoints
```

Contém:

* cenários de sucesso;
* entradas inválidas;
* duplicidades;
* recursos inexistentes;
* regras de negócio;
* permissões;
* concorrência;
* estados.

---

## `BACKLOG.md`

Define:

```text
o trabalho que precisa ser realizado
```

Contém:

* épicos;
* histórias de usuário;
* prioridades;
* dependências;
* critérios de aceitação;
* tarefas técnicas.

---

## `SPRINTS.md`

Define:

```text
a ordem de implementação
```

Cada Sprint informa quais funcionalidades devem estar funcionando antes que a equipe avance.

---

## `MAPA-FASE-1.md`

Define:

```text
onde cada parte do projeto deverá ficar
```

Apresenta:

* pastas;
* arquivos;
* módulos;
* estrutura planejada de implementação.

---

# 14. Ordem Recomendada de Leitura

Para quem está entrando no projeto, a ordem recomendada é:

```text
README.md
        ↓
REQUISITOS.md
        ↓
REGRAS-DE-NEGOCIO.md
        ↓
MODELO-DE-DADOS.md
        ↓
ARQUITETURA.md
        ↓
GUIA-CICLO-ENDPOINT.md
        ↓
API.md
        ↓
TESTES-POSTMAN.md
        ↓
BACKLOG.md
        ↓
SPRINTS.md
        ↓
MAPA-FASE-1.md
```

---

# 15. Fluxo de Desenvolvimento

Antes de implementar uma funcionalidade:

```text
1. Consultar a Sprint atual

2. Localizar a história no BACKLOG.md

3. Consultar o requisito correspondente

4. Consultar as regras de negócio

5. Identificar as entidades envolvidas

6. Consultar o endpoint em API.md

7. Consultar o GUIA-CICLO-ENDPOINT.md

8. Criar apenas os arquivos necessários

9. Implementar

10. Testar no Postman

11. Corrigir problemas

12. Atualizar documentação caso necessário
```

---

# 16. Exemplo de Fluxo de Implementação

Para implementar:

```text
Cadastrar usuário
```

a equipe deve consultar:

```text
BACKLOG.md
↓
US-001
```

Depois:

```text
REQUISITOS.md
↓
requisitos de cadastro
```

Depois:

```text
REGRAS-DE-NEGOCIO.md
↓
regras de usuário
```

Depois:

```text
MODELO-DE-DADOS.md
↓
Usuario
```

Depois:

```text
API.md
↓
POST /api/usuarios
```

E implementar:

```text
Route Handler
↓
DTO
↓
Validator
↓
Service
↓
Repository
↓
Banco
```

Por último:

```text
TESTES-POSTMAN.md
```

---

# 17. Estrutura Inicial do Projeto

A estrutura inicial planejada é:

```text
projeto-eventos-hackathons/
│
├── docs/
├── public/
│
└── src/
    │
    ├── app/
    │   └── api/
    │
    ├── components/
    ├── services/
    ├── repositories/
    ├── models/
    ├── dto/
    ├── validators/
    ├── config/
    └── utils/
```

A estrutura detalhada está documentada em:

```text
MAPA-FASE-1.md
```

---

# 18. Padrão de Desenvolvimento

A aplicação deve priorizar:

```text
clareza
+
simplicidade
+
separação de responsabilidades
+
consistência
+
facilidade de manutenção
```

O projeto não deve adicionar complexidade técnica sem necessidade concreta.

---

# 19. Regra para Criação de Arquivos

Não devem ser criados antecipadamente:

* Services vazios;
* Repositories sem uso;
* Models de funcionalidades futuras;
* DTOs sem finalidade;
* Validators não utilizados;
* endpoints que ainda não pertencem à Sprint.

Os arquivos devem surgir conforme as funcionalidades forem implementadas.

---

# 20. Banco de Dados

O banco de dados ainda será definido pela equipe.

Até essa decisão:

```text
Banco:
A DEFINIR
```

---

# 21. ORM

O ORM também será definido posteriormente.

```text
ORM:
A DEFINIR
```

Após a decisão, os documentos técnicos que dependerem dessa escolha deverão ser atualizados.

---

# 22. Autenticação

O sistema deverá possuir autenticação para operações relacionadas a:

* conta;
* perfil;
* empresas;
* organização de eventos;
* inscrições;
* equipes;
* submissões;
* avaliações;
* administração.

A tecnologia definitiva será escolhida posteriormente.

```text
Autenticação:
A DEFINIR
```

---

# 23. Testes

Os testes de API serão realizados utilizando:

```text
Postman
```

Cada endpoint deverá possuir, quando aplicável:

```text
teste de sucesso

teste de validação

teste de recurso inexistente

teste de duplicidade

teste de permissão

teste de regra de negócio
```

Os cenários estão detalhados em:

```text
TESTES-POSTMAN.md
```

---

# 24. Critério de Funcionalidade Concluída

Uma funcionalidade somente deve ser considerada pronta quando estiver:

```text
IMPLEMENTADA
+
FUNCIONANDO
+
INTEGRADA
+
TESTADA
+
COERENTE COM AS REGRAS
+
DOCUMENTADA
```

Um endpoint que simplesmente retorna:

```text
200 OK
```

não é suficiente para considerar a funcionalidade concluída.

O resultado produzido também precisa estar correto.

---

# 25. Organização das Sprints

O desenvolvimento será dividido em blocos incrementais.

Ordem macro:

```text
Base técnica
        ↓
Usuários
        ↓
Perfis
        ↓
Empresas
        ↓
Verificação
        ↓
Eventos
        ↓
Inscrições
        ↓
Programação
        ↓
Hackathons
        ↓
Equipes
        ↓
Submissões
        ↓
Avaliações
        ↓
Resultados
        ↓
Conquistas
        ↓
Recursos complementares
```

O planejamento completo está em:

```text
SPRINTS.md
```

---

# 26. Trabalho em Equipe

Integrantes podem trabalhar em funcionalidades diferentes em paralelo desde que não exista dependência bloqueadora.

Exemplo:

```text
Integrante A
→ backend de perfil

Integrante B
→ interface de perfil
```

Ambos devem seguir:

```text
mesmo requisito
+
mesma regra
+
mesmo contrato
```

---

# 27. Controle de Versão

A equipe deverá utilizar Git para controle de versão.

Boas práticas recomendadas:

* trabalhar em branches;
* realizar commits pequenos e claros;
* evitar commits com múltiplas funcionalidades sem relação;
* revisar mudanças antes da integração;
* evitar enviar arquivos de configuração sensíveis.

Exemplo de nomes de branches:

```text
feature/cadastro-usuario

feature/criacao-evento

fix/validacao-email

docs/atualizar-api
```

---

# 28. Commits

Exemplos:

```text
feat: adiciona cadastro de usuário

feat: adiciona criação de evento

fix: corrige validação de capacidade

docs: atualiza regras de inscrição

test: adiciona testes de usuário no Postman
```

A equipe pode adotar outra convenção desde que mantenha consistência.

---

# 29. Variáveis de Ambiente

Informações dependentes do ambiente deverão utilizar configuração apropriada.

Exemplo:

```text
.env
```

Um arquivo de referência deverá ser mantido:

```text
.env.example
```

O `.env` real não deve ser versionado quando possuir informações sensíveis.

---

# 30. Execução Local

A execução definitiva dependerá das tecnologias escolhidas durante a Sprint de preparação.

Para a aplicação Next.js, o fluxo esperado será semelhante a:

```bash
npm install
```

Depois:

```bash
npm run dev
```

A aplicação ficará disponível localmente de acordo com a configuração do projeto.

Exemplo comum:

```text
http://localhost:3000
```

As instruções deverão ser atualizadas caso a configuração real seja diferente.

---

# 31. Postman

Após iniciar a aplicação, configurar:

```text
baseUrl = http://localhost:3000
```

Exemplo de requisição:

```text
{{baseUrl}}/api/usuarios
```

A estrutura completa está em:

```text
TESTES-POSTMAN.md
```

---

# 32. Estado Atual do Projeto

Atualmente, o projeto encontra-se na etapa de:

```text
modelagem
+
documentação
+
planejamento da implementação
```

Já foram definidos conceitualmente:

* problema;
* solução;
* público-alvo;
* requisitos;
* regras de negócio;
* entidades;
* relacionamentos;
* arquitetura;
* contratos da API;
* testes;
* backlog;
* Sprints;
* mapa estrutural.

Algumas decisões técnicas ainda precisam ser tomadas antes da implementação completa.

---

# 33. Documentação como Fonte de Referência

Durante o desenvolvimento, a equipe deve evitar implementar funcionalidades apenas com base em interpretação individual.

Quando houver dúvida, consultar a documentação correspondente.

Exemplo:

```text
"O usuário pode fazer isso?"
→ REGRAS-DE-NEGOCIO.md

"Esse campo existe?"
→ MODELO-DE-DADOS.md

"Qual endpoint devemos criar?"
→ API.md

"Onde coloco esse código?"
→ ARQUITETURA.md / MAPA-FASE-1.md

"O que temos que implementar agora?"
→ SPRINTS.md

"Como testar?"
→ TESTES-POSTMAN.md
```

---

# 34. Divergência entre Código e Documentação

Caso durante a implementação seja identificada necessidade de alterar uma decisão documentada, a equipe deve atualizar os documentos relacionados.

Não é recomendado manter:

```text
documentação dizendo A
```

enquanto:

```text
código executa B
```

A documentação deve acompanhar a evolução real do projeto.

---

# 35. Princípio do Projeto

O objetivo não é construir a arquitetura mais complexa possível.

O objetivo é construir uma aplicação:

```text
compreensível
+
organizada
+
funcional
+
testável
+
evolutiva
```

A complexidade deve existir apenas quando houver necessidade real.

---

# 36. Resumo

A plataforma busca centralizar todo o ciclo de participação em eventos e hackathons de tecnologia.

Fluxo principal:

```text
USUÁRIO
    ↓
DESCOBRE EVENTO
    ↓
SE INSCREVE
    ↓
ACOMPANHA PROGRAMAÇÃO
    ↓
PARTICIPA
    ↓
ENTRA EM HACKATHON
    ↓
FORMA EQUIPE
    ↓
ENVIA PROJETO
    ↓
ACOMPANHA RESULTADO
    ↓
RECEBE CONQUISTAS
    ↓
CONSTRÓI HISTÓRICO
```

Ao mesmo tempo:

```text
EMPRESA
    ↓
É VERIFICADA
    ↓
CRIA EVENTO
    ↓
PUBLICA
    ↓
ORGANIZA
    ↓
GERENCIA PARTICIPANTES
    ↓
CONFIGURA HACKATHON
    ↓
PUBLICA RESULTADOS
    ↓
MANTÉM RELAÇÃO COM A COMUNIDADE
```

Esse é o núcleo da proposta da plataforma.
