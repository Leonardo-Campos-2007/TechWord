# ARQUITETURA

## 1. Objetivo do Documento

Este documento descreve a arquitetura inicial da plataforma de eventos e hackathons de tecnologia.

O objetivo é definir:

* organização geral da aplicação;
* responsabilidades das camadas;
* fluxo das requisições;
* divisão dos módulos;
* comunicação entre componentes;
* organização do backend;
* organização do frontend;
* estratégia inicial de persistência;
* limites entre responsabilidades;
* estratégia de evolução do projeto.

Este documento não define os endpoints individualmente.

Os endpoints serão documentados em `API.md`.

As regras de negócio permanecerão em `REGRAS-DE-NEGOCIO.md`.

As entidades e relacionamentos permanecerão em `MODELO-DE-DADOS.md`.

---

# 2. Tecnologias Definidas

## 2.1 Linguagem

A linguagem principal do projeto será:

```text
JavaScript
```

---

## 2.2 Runtime

O ambiente de execução utilizado no backend será:

```text
Node.js
```

---

## 2.3 Framework

O framework principal será:

```text
Next.js
```

---

## 2.4 Frontend

A camada de interface será construída utilizando:

```text
Next.js
React
HTML
CSS
JavaScript
```

---

## 2.5 Backend

O backend será implementado dentro do próprio projeto Next.js.

Serão utilizados os recursos disponibilizados pelo framework para criação das rotas da API.

Estrutura conceitual:

```text
Next.js
│
├── Frontend
│
└── Backend
    └── API
```

---

# 3. Tipo de Arquitetura

A primeira versão utilizará uma arquitetura:

```text
FULL-STACK MONOLÍTICA
```

Isso significa que frontend e backend permanecerão dentro do mesmo projeto.

Estrutura conceitual:

```text
Aplicação Next.js
│
├── Interface
├── API
├── Regras de aplicação
├── Acesso aos dados
└── Persistência
```

---

# 4. Justificativa da Arquitetura

A escolha de uma aplicação única foi feita considerando o contexto acadêmico e o estágio inicial do projeto.

As principais vantagens são:

* menor complexidade de configuração;
* menor quantidade de projetos separados;
* desenvolvimento mais simples;
* deploy mais simples;
* facilidade de entendimento pela equipe;
* compartilhamento facilitado de código;
* menor necessidade de infraestrutura;
* facilidade de evolução do MVP.

Não existe atualmente uma necessidade que justifique uma arquitetura distribuída.

Portanto:

```text
Microservices não fazem parte da arquitetura inicial.
```

---

# 5. Princípio Arquitetural Principal

Apesar de frontend e backend estarem no mesmo projeto, o código não deverá ser desenvolvido como um único bloco.

A aplicação deverá manter separação clara entre responsabilidades.

Estrutura conceitual:

```text
REQUISIÇÃO
    ↓
ROTA
    ↓
VALIDAÇÃO
    ↓
SERVICE
    ↓
REPOSITORY
    ↓
BANCO
```

E no retorno:

```text
BANCO
    ↓
REPOSITORY
    ↓
SERVICE
    ↓
ROTA
    ↓
RESPOSTA HTTP
```

---

# 6. Visão Geral da Arquitetura

```text
┌─────────────────────────────────┐
│             USUÁRIO             │
└────────────────┬────────────────┘
                 │
                 ↓
┌─────────────────────────────────┐
│        INTERFACE NEXT.JS        │
│                                 │
│  páginas                        │
│  componentes                    │
│  formulários                    │
│  navegação                      │
└────────────────┬────────────────┘
                 │
                 ↓
┌─────────────────────────────────┐
│        ROUTE HANDLERS           │
│                                 │
│        /api/...                 │
└────────────────┬────────────────┘
                 │
                 ↓
┌─────────────────────────────────┐
│        DTO / VALIDATOR          │
└────────────────┬────────────────┘
                 │
                 ↓
┌─────────────────────────────────┐
│            SERVICE              │
│                                 │
│ casos de uso                    │
│ regras de aplicação             │
└────────────────┬────────────────┘
                 │
                 ↓
┌─────────────────────────────────┐
│          REPOSITORY             │
│                                 │
│ acesso aos dados                │
└────────────────┬────────────────┘
                 │
                 ↓
┌─────────────────────────────────┐
│        BANCO DE DADOS           │
└─────────────────────────────────┘
```

---

# 7. Camada de Interface

A camada de interface será responsável pela interação direta com o usuário.

Ela deverá cuidar de:

* páginas;
* componentes;
* formulários;
* navegação;
* exibição de informações;
* estados visuais;
* feedback das ações;
* apresentação de erros;
* apresentação dos dados recebidos do backend.

Exemplo:

```text
Página de cadastro
        ↓
Usuário preenche formulário
        ↓
Frontend envia solicitação
        ↓
API processa
        ↓
Frontend recebe resposta
        ↓
Interface apresenta resultado
```

---

# 8. Componentes

Componentes devem representar partes reutilizáveis da interface.

Exemplos:

```text
EventCard
ProfileCard
BadgeCard
CompanyCard
ActivityCard
RankingTable
NotificationItem
```

Os nomes definitivos serão definidos durante a implementação.

Componentes de interface não devem possuir diretamente regras complexas do domínio.

---

# 9. Route Handler

No Next.js, a camada responsável por receber requisições da API será formada por Route Handlers.

Conceitualmente, essa camada desempenha papel semelhante ao `Controller` encontrado em outras arquiteturas.

Exemplo:

```text
POST /api/usuarios
```

Fluxo:

```text
Route Handler
    ↓
recebe requisição
    ↓
obtém dados
    ↓
valida entrada
    ↓
chama Service
    ↓
recebe resultado
    ↓
retorna HTTP
```

---

# 10. Responsabilidades do Route Handler

O Route Handler poderá:

* receber a requisição;
* ler parâmetros;
* ler query parameters;
* ler body;
* acionar validação;
* chamar o Service;
* converter resultados para resposta HTTP;
* definir o código HTTP adequado.

Exemplo conceitual:

```text
POST /api/usuarios

↓ recebe body

↓ valida

↓ UsuarioService.cadastrar()

↓ retorna

201 Created
```

---

# 11. O que o Route Handler não deve fazer

Evitar concentrar dentro da rota:

```text
validação complexa
+
regra de negócio
+
consulta de banco
+
persistência
+
formatação de dados
+
controle de toda a aplicação
```

Exemplo inadequado:

```text
Route Handler
├── verifica e-mail
├── busca banco
├── cria usuário
├── valida regras
├── salva
├── manipula perfil
└── responde
```

Preferível:

```text
Route Handler
        ↓
Service
        ↓
Repository
```

---

# 12. DTO

DTO significa:

```text
Data Transfer Object
```

Sua função é representar os dados transferidos durante determinada operação.

Exemplo:

```text
CreateUsuarioDTO

nome
email
senha
```

O DTO não deve ser confundido com uma entidade.

---

# 13. DTO de Entrada

Representa dados recebidos.

Exemplo:

```text
CreateEventoDTO

nome
descricao
modalidade
dataInicio
dataFim
capacidade
```

---

# 14. DTO de Saída

Representa informações que serão devolvidas.

Exemplo:

```text
UsuarioResponseDTO

id
nome
email
```

Um DTO de saída não precisa possuir todos os campos existentes na entidade.

---

# 15. Validator

A camada de validação será responsável por verificar o formato dos dados recebidos.

Exemplo:

```text
CreateUsuarioDTO
        ↓
Validator
        ↓
nome obrigatório
email obrigatório
email válido
senha obrigatória
```

A validação estrutural deve ocorrer antes da execução principal do caso de uso.

---

# 16. Validação Estrutural e Regra de Negócio

Esses conceitos não devem ser confundidos.

### Validação estrutural

Exemplo:

```text
email está vazio?
email possui formato válido?
nome foi informado?
```

### Regra de negócio

Exemplo:

```text
já existe usuário com esse email?
empresa está verificada?
evento possui vaga?
equipe atingiu limite máximo?
```

Portanto:

```text
VALIDATOR
≠
REGRA DE NEGÓCIO
```

---

# 17. Service

A camada `Service` será responsável pelos casos de uso e pela coordenação das regras da aplicação.

Exemplos:

```text
UsuarioService

EmpresaService

EventoService

InscricaoService

HackathonService

EquipeService

SubmissaoService
```

---

# 18. Responsabilidades do Service

O Service poderá:

* aplicar regras de negócio;
* coordenar operações;
* consultar repositories;
* verificar condições;
* atualizar entidades;
* iniciar operações relacionadas ao caso de uso;
* devolver o resultado da operação.

Exemplo:

```text
EventoService.inscreverUsuario()

↓
buscar evento

↓
verificar estado do evento

↓
verificar vagas

↓
verificar inscrição existente

↓
determinar estado da inscrição

↓
salvar inscrição
```

---

# 19. O que o Service não deve fazer

O Service não deve ficar diretamente responsável por detalhes HTTP.

Evitar:

```text
return Response.json(...)
```

dentro do Service.

Também deve evitar depender diretamente de componentes de interface.

Portanto:

```text
SERVICE
não conhece
BOTÃO
PÁGINA
HTML
```

E:

```text
SERVICE
não deve decidir diretamente
HTTP 201
HTTP 404
HTTP 409
```

A camada HTTP deve traduzir o resultado para esses códigos.

---

# 20. Repository

O Repository será responsável pela comunicação com a persistência.

Exemplos:

```text
UsuarioRepository

EmpresaRepository

EventoRepository

InscricaoRepository

EquipeRepository
```

---

# 21. Responsabilidades do Repository

O Repository poderá realizar operações como:

```text
buscarPorId()

buscarPorEmail()

listar()

salvar()

atualizar()

buscarInscricao()

buscarEquipesDoHackathon()
```

Conceitualmente:

```text
Service
   ↓
Repository
   ↓
Banco
```

---

# 22. O que o Repository não deve fazer

O Repository não deve concentrar regras do domínio.

Exemplo inadequado:

```text
UsuarioRepository
↓
decidir se usuário pode participar do evento
```

Essa decisão pertence à lógica da aplicação.

O Repository deve principalmente responder:

```text
quais dados existem?
```

e:

```text
quais dados precisam ser persistidos?
```

---

# 23. Model / Entity

Models ou Entities representam os dados centrais da aplicação.

Exemplo:

```text
Usuario

id
nome
email
senha
```

Outro exemplo:

```text
Evento

id
nome
descricao
modalidade
status
dataInicio
dataFim
```

As entidades conceituais estão documentadas detalhadamente em:

```text
MODELO-DE-DADOS.md
```

---

# 24. Fluxo Completo de uma Requisição

Exemplo conceitual:

```text
Usuário
   ↓
Frontend
   ↓
POST /api/eventos
   ↓
Route Handler
   ↓
CreateEventoDTO
   ↓
Validator
   ↓
EventoService
   ↓
EventoRepository
   ↓
Banco
```

Retorno:

```text
Banco
   ↓
EventoRepository
   ↓
EventoService
   ↓
Route Handler
   ↓
HTTP Response
   ↓
Frontend
   ↓
Usuário
```

---

# 25. Exemplo: Cadastro de Usuário

O fluxo arquitetural será:

```text
Frontend
        ↓
POST /api/usuarios
        ↓
Route Handler
        ↓
CreateUsuarioDTO
        ↓
UsuarioValidator
        ↓
UsuarioService
        ↓
UsuarioRepository
        ↓
Banco de dados
```

Detalhamento completo desse exemplo ficará em:

```text
GUIA-CICLO-ENDPOINT.md
```

---

# 26. Organização por Domínio

Para evitar que o projeto se transforme em uma coleção desorganizada de arquivos, as funcionalidades devem ser identificadas por domínio.

Domínios principais:

```text
usuarios

empresas

eventos

inscricoes

programacao

atividades

hackathons

equipes

submissoes

avaliacoes

ranking

emblemas

certificados

patrocinadores

comunicacao

notificacoes
```

---

# 27. Módulo de Usuários

Responsabilidades principais:

```text
cadastro
perfil
consulta
edição
seguidores
tecnologias
áreas de interesse
links profissionais
```

Componentes conceituais:

```text
Usuario
Perfil
Tecnologia
AreaInteresse
SeguimentoUsuario
```

---

# 28. Módulo de Empresas

Responsabilidades:

```text
cadastro de empresa
perfil público
verificação
seguidores
```

Entidades principais:

```text
Empresa
VerificacaoEmpresa
SeguimentoEmpresa
```

---

# 29. Módulo de Eventos

Responsabilidades:

```text
criação
edição
aprovação
publicação
cancelamento
consulta
descoberta
organização
```

Entidades:

```text
Evento
EventoOrganizador
```

---

# 30. Módulo de Inscrições

Responsabilidades:

```text
inscrição
aprovação
rejeição
cancelamento
confirmação
controle de vagas
lista de espera
```

Entidade principal:

```text
InscricaoEvento
```

---

# 31. Módulo de Programação

Responsabilidades:

```text
trilhas
atividades
horários
locais
inscrições em atividades
check-in
```

Entidades principais:

```text
Trilha
Atividade
InscricaoAtividade
CheckInEvento
CheckInAtividade
```

---

# 32. Módulo de Hackathons

Responsabilidades:

```text
configuração
regras de participação
fases
desafios
```

Entidades:

```text
Hackathon
FaseHackathon
Desafio
```

---

# 33. Módulo de Equipes

Responsabilidades:

```text
criação
formação
convites
solicitações
membros
liderança
desclassificação
```

Entidades:

```text
Equipe
MembroEquipe
ConviteEquipe
SolicitacaoEntradaEquipe
```

---

# 34. Módulo de Submissões

Responsabilidades:

```text
projeto
envio
versionamento
prazo
histórico
```

Entidades:

```text
Submissao
VersaoSubmissao
```

---

# 35. Módulo de Avaliações

Responsabilidades:

```text
critérios
jurados
avaliações
resultado final
```

Entidades:

```text
CriterioAvaliacao
JuradoHackathon
Avaliacao
Resultado
```

---

# 36. Módulo de Ranking

Responsabilidades:

```text
classificação
visibilidade
publicação
resultados
```

Entidade principal:

```text
Ranking
```

---

# 37. Módulo de Conquistas

Responsabilidades:

```text
emblemas
concessões
certificados
histórico
```

Entidades:

```text
Emblema
EmblemaConcedido
Certificado
CertificadoEmitido
```

---

# 38. Módulo de Patrocínio

Responsabilidades:

```text
patrocinadores
estandes
ofertas
desafios patrocinados
```

Entidades:

```text
Patrocinio
Estande
Oferta
```

---

# 39. Módulo de Comunicação

Responsabilidades:

```text
comunicados
segmentação de público
mensagens relacionadas ao evento
```

Entidade:

```text
Comunicado
```

---

# 40. Módulo de Notificações

Responsabilidades:

```text
central de notificações
preferências
notificações essenciais
notificações operacionais
notificações sociais
notificações promocionais
```

Entidades:

```text
Notificacao
PreferenciaNotificacao
```

---

# 41. Dependência entre Módulos

Os módulos não devem depender uns dos outros sem necessidade.

Exemplo de fluxo aceitável:

```text
InscricaoService
        ↓
EventoRepository
```

porque uma inscrição precisa consultar informações do evento.

Mas deve ser evitado:

```text
EventoService
   ↓
InscricaoService
   ↓
EventoService
```

Isso cria dependência circular.

---

# 42. Direção das Dependências

Sempre que possível:

```text
Route Handler
     ↓
Service
     ↓
Repository
```

Não:

```text
Repository
     ↓
Service
```

E não:

```text
Repository
     ↓
Route Handler
```

---

# 43. Acesso entre Módulos

Quando um domínio precisar de informações pertencentes a outro domínio, a dependência deve ser explícita.

Exemplo:

```text
InscricaoService

precisa saber:

evento existe?
evento possui vagas?
evento aceita inscrições?
```

Então pode utilizar:

```text
EventoRepository
```

ou uma operação apropriada fornecida pelo módulo de eventos.

Evitar duplicar regras.

---

# 44. Persistência

A tecnologia de banco ainda não foi definida.

Portanto, neste momento:

```text
Banco:
A DEFINIR

ORM:
A DEFINIR
```

A arquitetura deve permitir a escolha posterior sem exigir alteração completa dos casos de uso.

---

# 45. Estratégia para Persistência

O Service não deve depender diretamente de detalhes específicos do banco sempre que for viável.

Preferível:

```text
Service
   ↓
Repository
   ↓
ORM
   ↓
Banco
```

Assim, detalhes de persistência permanecem concentrados em uma região específica da aplicação.

---

# 46. Transações

A estratégia técnica de transações será definida após a escolha do banco e da tecnologia de persistência.

Entretanto, operações que alterem múltiplos dados relacionados devem ser identificadas como candidatas a execução atômica.

Exemplo conceitual:

```text
Aceitar convite
        ↓
alterar convite
        +
criar membro da equipe
```

Essas duas alterações representam uma única operação lógica.

---

# 47. Operações que Merecem Atenção Transacional

Exemplos:

```text
aprovar inscrição + ocupar vaga

cancelar inscrição + liberar vaga

aceitar convite + adicionar membro

conceder emblema + registrar histórico

emitir certificado + registrar emissão

desclassificar equipe + registrar motivo
```

A implementação técnica será definida posteriormente.

---

# 48. Concorrência

Algumas operações podem ocorrer simultaneamente.

Exemplo:

```text
Evento possui 1 vaga

Usuário A tenta se inscrever
Usuário B tenta se inscrever
```

A aplicação não deve permitir:

```text
capacidade = 100
participantes confirmados = 101
```

Outro exemplo:

```text
Equipe possui 1 vaga restante

dois convites são aceitos simultaneamente
```

Esse cenário também deverá respeitar o limite da equipe.

---

# 49. Áreas Sensíveis à Concorrência

Devem receber atenção especial:

```text
limite de vagas do evento

limite de vagas da atividade

limite de integrantes da equipe

lista de espera

aceitação de convites

submissão próxima ao prazo final

concessão de emblemas

emissão de certificados
```

---

# 50. Integrações Externas

No momento, nenhuma integração externa obrigatória foi consolidada.

Possíveis integrações futuras incluem:

```text
mapas/geolocalização

e-mail

notificações push

armazenamento de imagens

pagamentos

carteira interna

serviços de autenticação
```

Essas integrações não devem ser adicionadas antes de haver necessidade real.

---

# 51. Sistema de Pagamentos

O sistema de créditos internos do evento não faz parte da primeira fase.

Portanto:

```text
Carteira
Saldo
Transação
Compra
Estorno
```

não serão implementados inicialmente.

A arquitetura deverá permitir que esse módulo seja adicionado futuramente sem contaminar os módulos principais.

---

# 52. Autenticação

O sistema precisará possuir autenticação porque existem operações específicas por usuário, empresa e administrador.

Entretanto, a tecnologia de autenticação ainda não foi definida.

Portanto:

```text
Estratégia de autenticação:
A DEFINIR
```

Possibilidades técnicas serão avaliadas posteriormente.

---

# 53. Autorização

A aplicação possuirá diferentes responsabilidades associadas a:

```text
USUARIO

EMPRESA

ADMINISTRADOR

ORGANIZADOR

JURADO
```

A estratégia técnica definitiva para representar essas permissões ainda será definida.

Este documento não deve antecipar uma tecnologia específica antes dessa decisão.

---

# 54. Tratamento de Erros

Os erros da aplicação devem ser controlados.

Fluxo esperado:

```text
Repository
    ↓
Service
    ↓
Route Handler
    ↓
Resposta HTTP adequada
```

Exemplos conceituais:

```text
usuário não encontrado

evento não encontrado

email já cadastrado

evento sem vagas

equipe lotada

submissão fora do prazo
```

---

# 55. Tipos Conceituais de Erro

A aplicação pode distinguir conceitualmente:

```text
erro de validação

recurso inexistente

conflito

regra de negócio violada

erro interno
```

A tradução para códigos HTTP será definida no documento `API.md`.

---

# 56. Configuração

Configurações dependentes do ambiente não devem ficar espalhadas pelo código.

Exemplos:

```text
URL do banco

segredos

URLs externas

configuração de serviços
```

Esses valores deverão ser fornecidos por configuração apropriada do ambiente.

---

# 57. Variáveis de Ambiente

O projeto deverá utilizar arquivos ou mecanismos de ambiente apropriados ao Next.js.

Estrutura esperada:

```text
.env
.env.example
```

Valores reais sensíveis não devem ser colocados no arquivo de exemplo.

---

# 58. Organização Inicial do Projeto

Uma estrutura inicial possível será:

```text
src/
│
├── app/
│   │
│   ├── api/
│   │
│   └── páginas da aplicação
│
├── components/
│
├── services/
│
├── repositories/
│
├── models/
│
├── dto/
│
├── validators/
│
├── utils/
│
└── config/
```

Essa é uma estrutura inicial e poderá ser refinada no `MAPA-FASE-1.md`.

---

# 59. Estrutura das Rotas da API

As rotas serão organizadas inicialmente dentro:

```text
src/app/api/
```

Exemplo conceitual:

```text
src/app/api/
│
├── usuarios/
├── empresas/
├── eventos/
├── inscricoes/
├── atividades/
├── hackathons/
├── equipes/
├── submissoes/
└── notificacoes/
```

Os endpoints definitivos serão especificados em `API.md`.

---

# 60. Estrutura de Services

Estrutura inicial:

```text
src/services/
│
├── usuario/
├── empresa/
├── evento/
├── inscricao/
├── atividade/
├── hackathon/
├── equipe/
├── submissao/
├── avaliacao/
└── notificacao/
```

A forma definitiva poderá ser simplificada durante a implementação.

---

# 61. Estrutura de Repositories

Estrutura conceitual:

```text
src/repositories/
│
├── usuarioRepository
├── empresaRepository
├── eventoRepository
├── inscricaoRepository
├── atividadeRepository
├── hackathonRepository
├── equipeRepository
└── submissaoRepository
```

A nomenclatura definitiva seguirá o padrão adotado pela equipe.

---

# 62. Estrutura de DTOs

Os DTOs poderão ser organizados por domínio.

Exemplo:

```text
src/dto/
│
├── usuario/
│   ├── createUsuario
│   └── updateUsuario
│
├── evento/
│   ├── createEvento
│   └── updateEvento
│
└── equipe/
```

---

# 63. Estrutura de Validators

Conceitualmente:

```text
src/validators/
│
├── usuario/
├── empresa/
├── evento/
├── inscricao/
└── equipe/
```

A biblioteca de validação ainda não foi definida.

---

# 64. Reutilização de Código

Código compartilhado deve possuir uma responsabilidade clara.

Exemplos:

```text
formatação de data

paginação

tratamento comum de respostas

conversões

funções auxiliares
```

Evitar criar um arquivo genérico gigantesco contendo funções sem relação entre si.

---

# 65. Regra sobre Utils

O diretório `utils` não deve virar um local para armazenar qualquer código sem classificação.

Preferível:

```text
utils/date
utils/pagination
```

em vez de:

```text
utils/tudo.js
```

---

# 66. Frontend e Backend no Mesmo Projeto

Apesar de compartilharem o mesmo projeto:

```text
frontend
≠
backend
```

A camada de interface não deve acessar diretamente a persistência.

Fluxo esperado:

```text
Interface
   ↓
API / camada servidor
   ↓
Service
   ↓
Repository
   ↓
Banco
```

---

# 67. Estratégia de Desenvolvimento

A implementação será realizada de forma incremental.

Não devem ser criados todos os módulos antecipadamente apenas porque estão previstos na arquitetura.

O fluxo será:

```text
Sprint
   ↓
implementar funcionalidades da Sprint
   ↓
testar
   ↓
corrigir
   ↓
concluir
   ↓
próxima Sprint
```

---

# 68. Estratégia de Evolução

A arquitetura deve permitir que funcionalidades futuras sejam adicionadas progressivamente.

Exemplos:

```text
carteira interna

pagamentos

recomendações de eventos

analytics

integrações externas
```

Esses recursos não devem exigir reescrita completa do sistema.

---

# 69. Possível Separação Futura

Caso o projeto cresça significativamente, alguns componentes poderão futuramente ser separados.

Exemplo:

```text
Aplicação atual

Next.js
├── frontend
└── backend
```

Poderia futuramente evoluir para:

```text
Frontend
        ↓
API independente
        ↓
serviços especializados
```

Entretanto, isso não faz parte da arquitetura atual.

A separação somente deverá ocorrer se houver justificativa real.

---

# 70. Arquitetura Não Deve Antecipar Complexidade

Não serão adicionados inicialmente apenas por padrão:

```text
microservices

message broker

event sourcing

CQRS

Kubernetes

múltiplos bancos

cache distribuído
```

Qualquer recurso desse tipo deverá possuir uma necessidade concreta antes de ser incorporado.

---

# 71. Fluxo Arquitetural Resumido

```text
USUÁRIO
   ↓
INTERFACE
   ↓
ROUTE HANDLER
   ↓
DTO
   ↓
VALIDATOR
   ↓
SERVICE
   ↓
REPOSITORY
   ↓
PERSISTÊNCIA
```

Retorno:

```text
PERSISTÊNCIA
   ↓
REPOSITORY
   ↓
SERVICE
   ↓
ROUTE HANDLER
   ↓
HTTP RESPONSE
   ↓
INTERFACE
   ↓
USUÁRIO
```

---

# 72. Regra de Dependência

A direção padrão deve ser:

```text
Route Handler
        ↓
Service
        ↓
Repository
        ↓
Persistência
```

Evitar:

```text
Repository → Route Handler

Repository → Interface

Model → Route Handler

Service → Página React
```

---

# 73. Responsabilidade Resumida das Camadas

| Elemento       | Responsabilidade principal                  |
| -------------- | ------------------------------------------- |
| Página         | Apresentar uma tela                         |
| Componente     | Representar parte reutilizável da interface |
| Route Handler  | Receber e responder requisições HTTP        |
| DTO            | Representar dados transferidos              |
| Validator      | Validar estrutura dos dados                 |
| Service        | Executar casos de uso e regras              |
| Repository     | Consultar e persistir dados                 |
| Model / Entity | Representar os dados do domínio             |
| Config         | Centralizar configurações                   |
| Utils          | Funções auxiliares reutilizáveis            |

---

# 74. Exemplo Resumido por Responsabilidade

Para cadastrar um usuário:

```text
Route Handler
"Recebi uma solicitação de cadastro."
```

```text
DTO
"Estes são os dados permitidos."
```

```text
Validator
"Os dados possuem formato válido?"
```

```text
Service
"O usuário pode ser cadastrado?"
```

```text
Repository
"Já existe esse e-mail? Salve o usuário."
```

```text
Model / Entity
"Esta é a representação do usuário."
```

```text
Route Handler
"Retorne o resultado ao cliente."
```

---

# 75. Decisões Arquiteturais Consolidadas

Até o momento estão definidas:

```text
Linguagem:
JavaScript

Runtime:
Node.js

Framework:
Next.js

Frontend:
Next.js + React + HTML + CSS

Backend:
Next.js

Formato:
Full-stack

Distribuição:
Aplicação única

Estilo:
Monolítico organizado por responsabilidades
```

---

# 76. Decisões Técnicas Pendentes

Ainda deverão ser decididos:

```text
Banco de dados

ORM

Biblioteca de validação

Estratégia de autenticação

Estratégia de autorização

Estratégia definitiva de IDs

Sistema de armazenamento de imagens

Serviço de notificações externas

Hospedagem

Deploy

CI/CD
```

Nenhuma dessas tecnologias deve ser presumida neste documento antes da decisão da equipe.

---

# 77. Documentos Relacionados

```text
REQUISITOS.md
→ o que o sistema precisa oferecer

REGRAS-DE-NEGOCIO.md
→ condições e restrições do domínio

MODELO-DE-DADOS.md
→ entidades e relacionamentos

ARQUITETURA.md
→ organização técnica da aplicação

GUIA-CICLO-ENDPOINT.md
→ como implementar um endpoint seguindo a arquitetura

API.md
→ contratos HTTP

TESTES-POSTMAN.md
→ validação dos endpoints

BACKLOG.md
→ trabalho necessário

SPRINTS.md
→ ordem de implementação

MAPA-FASE-1.md
→ estrutura prevista do projeto
```

---

# 78. Regra de Evolução da Arquitetura

Sempre que uma decisão modificar:

* organização de módulos;
* responsabilidades;
* persistência;
* comunicação;
* framework;
* dependências;
* fluxo das requisições;
* estrutura principal do projeto;

este documento deverá ser revisado.

A arquitetura deve servir para simplificar o desenvolvimento e orientar a equipe.

Ela não deve introduzir complexidade apenas para seguir padrões.
