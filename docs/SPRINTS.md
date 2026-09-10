# SPRINTS

## 1. Objetivo do Documento

Este documento organiza a ordem de desenvolvimento da plataforma de eventos e hackathons de tecnologia.

Cada Sprint possui:

* objetivo;
* funcionalidades principais;
* dependências;
* checklist obrigatório de conclusão.

A equipe só deve avançar para a Sprint seguinte quando os itens obrigatórios da Sprint atual estiverem funcionando e validados.

---

# 2. Regra Geral das Sprints

Antes de avançar para a próxima Sprint:

```text id="4aw1ep"
[ ] Funcionalidades obrigatórias concluídas

[ ] Endpoints funcionando

[ ] Regras de negócio respeitadas

[ ] Dados persistidos corretamente

[ ] Testes correspondentes executados no Postman

[ ] Erros bloqueadores corrigidos

[ ] Documentação atualizada quando necessário
```

---

# SPRINT 0 — Preparação Técnica

## Objetivo

Preparar a base do projeto antes do desenvolvimento funcional.

## Funcionalidades / tarefas

```text id="1nzyom"
[ ] Criar projeto Next.js

[ ] Configurar JavaScript

[ ] Definir estrutura inicial de diretórios

[ ] Definir banco de dados

[ ] Definir ORM

[ ] Configurar conexão com banco

[ ] Configurar migrations

[ ] Definir biblioteca de validação

[ ] Definir estratégia de autenticação

[ ] Definir padrão de respostas da API

[ ] Definir padrão de tratamento de erros

[ ] Configurar variáveis de ambiente

[ ] Criar .env.example

[ ] Criar ambiente no Postman

[ ] Criar Collection principal no Postman
```

## Antes de avançar

```text id="zjc1vx"
[ ] Projeto inicia sem erro

[ ] Banco conecta corretamente

[ ] Migration inicial funciona

[ ] Estrutura de pastas está criada

[ ] Postman consegue acessar a API local

[ ] Padrões técnicos básicos estão definidos
```

---

# SPRINT 1 — Usuários e Autenticação

## Objetivo

Construir a base de identidade dos usuários.

## Funcionalidades

```text id="elz2gc"
[ ] Cadastro de usuário

[ ] Validação de cadastro

[ ] Impedir e-mail duplicado

[ ] Login

[ ] Logout

[ ] Consulta da própria conta

[ ] Atualização de dados da conta
```

## Antes de avançar

```text id="f7ztf5"
[ ] Usuário pode ser cadastrado

[ ] Cadastro inválido é rejeitado

[ ] E-mail duplicado é impedido

[ ] Login funciona

[ ] Login inválido é rejeitado

[ ] Logout funciona

[ ] Usuário autenticado consegue consultar a própria conta

[ ] Usuário consegue atualizar campos permitidos

[ ] Dados sensíveis não aparecem nas respostas

[ ] Testes do módulo de usuários passaram no Postman
```

---

# SPRINT 2 — Perfil Público

## Objetivo

Permitir que cada usuário possua uma identidade pública na plataforma.

## Funcionalidades

```text id="1snq8j"
[ ] Criar perfil associado ao usuário

[ ] Consultar perfil

[ ] Editar perfil

[ ] Adicionar bio

[ ] Adicionar localização

[ ] Adicionar GitHub

[ ] Adicionar LinkedIn

[ ] Adicionar portfólio

[ ] Cadastrar tecnologias

[ ] Remover tecnologias

[ ] Cadastrar áreas de interesse

[ ] Remover áreas de interesse
```

## Antes de avançar

```text id="f6y5ux"
[ ] Todo usuário possui perfil

[ ] Perfil público pode ser consultado

[ ] Usuário edita apenas o próprio perfil

[ ] Links inválidos são rejeitados

[ ] Tecnologias podem ser adicionadas e removidas

[ ] Áreas de interesse podem ser adicionadas e removidas

[ ] Duplicidades são impedidas

[ ] Testes de perfil passaram no Postman
```

---

# SPRINT 3 — Empresas

## Objetivo

Criar o módulo básico de empresas.

## Funcionalidades

```text id="090aao"
[ ] Cadastro de empresa

[ ] Página pública da empresa

[ ] Consulta de empresa

[ ] Edição de empresa

[ ] Exibição de informações institucionais
```

## Antes de avançar

```text id="5cvolr"
[ ] Empresa pode ser cadastrada

[ ] Empresa pode ser consultada

[ ] Responsável autorizado consegue editar

[ ] Usuário sem permissão não consegue editar

[ ] Página pública funciona

[ ] Testes do módulo de empresas passaram no Postman
```

---

# SPRINT 4 — Verificação de Empresas

## Objetivo

Permitir que empresas sejam analisadas e verificadas pela plataforma.

## Funcionalidades

```text id="7g3v3l"
[ ] Solicitar verificação

[ ] Consultar status da verificação

[ ] Listar solicitações pendentes

[ ] Aprovar empresa

[ ] Rejeitar empresa

[ ] Registrar motivo de rejeição

[ ] Exibir selo de verificação
```

## Antes de avançar

```text id="3m8hox"
[ ] Empresa consegue solicitar verificação

[ ] Solicitação duplicada pendente é impedida

[ ] Administrador consegue listar solicitações

[ ] Administrador consegue aprovar

[ ] Administrador consegue rejeitar

[ ] Rejeição possui motivo

[ ] Empresa aprovada fica identificada como verificada

[ ] Usuário comum não executa operação administrativa

[ ] Testes de verificação passaram no Postman
```

---

# SPRINT 5 — Eventos

## Objetivo

Criar o núcleo de eventos da aplicação.

## Funcionalidades

```text id="v5jhfn"
[ ] Criar evento

[ ] Criar evento como rascunho

[ ] Editar rascunho

[ ] Definir modalidade

[ ] Definir data e horário

[ ] Definir localização

[ ] Definir acesso online

[ ] Definir evento gratuito ou pago

[ ] Definir capacidade

[ ] Associar empresas organizadoras

[ ] Enviar evento para aprovação
```

## Antes de avançar

```text id="z0e5k8"
[ ] Empresa verificada consegue criar evento

[ ] Empresa não verificada não consegue enviar evento para aprovação

[ ] Evento começa como rascunho

[ ] Datas inválidas são rejeitadas

[ ] Modalidade é validada

[ ] Evento presencial exige localização quando aplicável

[ ] Evento pode possuir mais de um organizador

[ ] Evento pode ser enviado para aprovação

[ ] Testes básicos de evento passaram no Postman
```

---

# SPRINT 6 — Aprovação e Publicação de Eventos

## Objetivo

Completar o ciclo administrativo do evento.

## Funcionalidades

```text id="hn27qo"
[ ] Listar eventos pendentes

[ ] Aprovar evento

[ ] Rejeitar evento

[ ] Registrar motivo da rejeição

[ ] Publicar evento aprovado

[ ] Editar evento publicado

[ ] Cancelar evento

[ ] Encerrar evento
```

## Antes de avançar

```text id="ecsh7j"
[ ] Administrador consegue aprovar evento

[ ] Administrador consegue rejeitar evento

[ ] Evento rejeitado mantém motivo

[ ] Somente evento aprovado pode ser publicado

[ ] Evento publicado pode ser editado

[ ] Evento cancelado continua no histórico

[ ] Evento encerrado possui estado correto

[ ] Usuário sem permissão não aprova eventos

[ ] Testes do ciclo do evento passaram no Postman
```

---

# SPRINT 7 — Busca e Descoberta

## Objetivo

Permitir que usuários encontrem eventos.

## Funcionalidades

```text id="bh4cgq"
[ ] Listar eventos

[ ] Buscar por nome

[ ] Filtrar por modalidade

[ ] Filtrar por período

[ ] Filtrar por categoria

[ ] Filtrar gratuito/pago

[ ] Filtrar por localização

[ ] Paginação

[ ] Ordenação
```

## Antes de avançar

```text id="lpkxqz"
[ ] Eventos públicos são listados

[ ] Busca por texto funciona

[ ] Filtros funcionam individualmente

[ ] Filtros podem ser combinados

[ ] Paginação funciona

[ ] Ordenação funciona

[ ] Eventos online não dependem de proximidade física

[ ] Testes de busca passaram no Postman
```

---

# SPRINT 8 — Inscrições em Eventos

## Objetivo

Permitir participação nos eventos.

## Funcionalidades

```text id="y8ef31"
[ ] Inscrever usuário

[ ] Consultar inscrição

[ ] Listar participantes

[ ] Inscrição automática

[ ] Aprovação manual

[ ] Aprovar inscrição

[ ] Rejeitar inscrição

[ ] Cancelar inscrição

[ ] Confirmar participação

[ ] Controlar limite de vagas
```

## Antes de avançar

```text id="mbf4dt"
[ ] Usuário consegue se inscrever

[ ] Inscrição duplicada é impedida

[ ] Evento lotado não ultrapassa capacidade

[ ] Aprovação manual funciona

[ ] Rejeição funciona

[ ] Usuário consegue cancelar própria inscrição

[ ] Usuário não cancela inscrição de terceiro

[ ] Confirmação funciona

[ ] Contagem de vagas permanece correta

[ ] Testes de inscrição passaram no Postman
```

---

# SPRINT 9 — Lista de Espera

## Objetivo

Completar o controle de vagas do evento.

## Funcionalidades

```text id="5s7k5x"
[ ] Habilitar lista de espera

[ ] Adicionar usuário à lista de espera

[ ] Consultar lista de espera

[ ] Liberar vaga

[ ] Oferecer vaga ao próximo participante

[ ] Confirmar vaga oferecida
```

## Antes de avançar

```text id="1z6f7d"
[ ] Lista existe apenas quando habilitada

[ ] Evento lotado adiciona usuário à espera quando permitido

[ ] Usuário em espera não é contado como confirmado

[ ] Vaga liberada pode ser oferecida

[ ] Vaga oferecida não confirma automaticamente o usuário

[ ] Capacidade nunca é ultrapassada

[ ] Testes da lista de espera passaram no Postman
```

---

# SPRINT 10 — Programação e Trilhas

## Objetivo

Criar a estrutura de programação dos eventos.

## Funcionalidades

```text id="af3x0x"
[ ] Criar trilha

[ ] Editar trilha

[ ] Consultar trilhas

[ ] Remover trilha

[ ] Criar programação do evento
```

## Antes de avançar

```text id="ppktjc"
[ ] Evento pode possuir múltiplas trilhas

[ ] Trilhas podem ser editadas

[ ] Trilhas podem ser consultadas

[ ] Remoção não deixa relacionamentos inválidos

[ ] Testes de trilhas passaram no Postman
```

---

# SPRINT 11 — Atividades

## Objetivo

Completar a programação com atividades e inscrições específicas.

## Funcionalidades

```text id="037nou"
[ ] Criar atividade

[ ] Editar atividade

[ ] Associar atividade a trilha

[ ] Criar atividade sem trilha

[ ] Definir tipo de atividade

[ ] Definir horário

[ ] Definir local

[ ] Definir capacidade própria

[ ] Exigir inscrição separada

[ ] Inscrever usuário em atividade

[ ] Cancelar inscrição em atividade

[ ] Listar inscritos
```

## Antes de avançar

```text id="hizlvh"
[ ] Atividade pertence ao evento

[ ] Atividade pode existir com ou sem trilha

[ ] Horários inválidos são rejeitados

[ ] Capacidade da atividade é respeitada

[ ] Inscrição duplicada é impedida

[ ] Cancelamento funciona

[ ] Programação completa pode ser consultada

[ ] Testes de atividades passaram no Postman
```

---

# SPRINT 12 — Check-in

## Objetivo

Permitir registro de presença.

## Funcionalidades

```text id="xd1n7u"
[ ] Habilitar check-in no evento

[ ] Registrar check-in no evento

[ ] Listar check-ins

[ ] Habilitar check-in em atividade

[ ] Registrar check-in em atividade

[ ] Consultar presença
```

## Antes de avançar

```text id="g5si3x"
[ ] Check-in do evento funciona

[ ] Check-in duplicado é impedido

[ ] Check-in em atividade funciona

[ ] Registros de presença podem ser consultados

[ ] Check-in não cria inscrição automaticamente

[ ] Testes de check-in passaram no Postman
```

---

# SPRINT 13 — Base de Hackathons

## Objetivo

Adicionar funcionalidades específicas de hackathon ao evento.

## Funcionalidades

```text id="m8w66r"
[ ] Configurar evento como hackathon

[ ] Definir participação individual

[ ] Definir participação por equipe

[ ] Permitir ambos os formatos

[ ] Definir mínimo de integrantes

[ ] Definir máximo de integrantes

[ ] Exibir regras do hackathon
```

## Antes de avançar

```text id="eqd0gx"
[ ] Evento pode receber configuração de hackathon

[ ] Não existem duas configurações principais para o mesmo evento

[ ] Tipo de participação funciona

[ ] Mínimo e máximo são validados

[ ] Regras podem ser consultadas

[ ] Testes da configuração passaram no Postman
```

---

# SPRINT 14 — Fases do Hackathon

## Objetivo

Permitir ciclos configuráveis para cada hackathon.

## Funcionalidades

```text id="qva5yu"
[ ] Criar fase

[ ] Editar fase

[ ] Criar fase personalizada

[ ] Ordenar fases

[ ] Definir início e fim

[ ] Identificar fase atual

[ ] Exibir próximas fases
```

## Antes de avançar

```text id="zbl053"
[ ] Fases pertencem ao hackathon correto

[ ] Ordem funciona

[ ] Datas são coerentes

[ ] Fase personalizada funciona

[ ] Fase atual pode ser identificada

[ ] Próximas fases podem ser consultadas

[ ] Testes de fases passaram no Postman
```

---

# SPRINT 15 — Desafios

## Objetivo

Permitir publicação e acompanhamento dos desafios do hackathon.

## Funcionalidades

```text id="zi6rhh"
[ ] Criar desafio

[ ] Editar desafio

[ ] Consultar desafio

[ ] Listar desafios

[ ] Associar patrocinador quando aplicável
```

## Antes de avançar

```text id="ylmhz6"
[ ] Desafio pertence ao hackathon

[ ] Título e descrição são obrigatórios

[ ] Participantes conseguem consultar desafio

[ ] Patrocinador é opcional

[ ] Testes de desafios passaram no Postman
```

---

# SPRINT 16 — Equipes

## Objetivo

Implementar formação e administração de equipes.

## Funcionalidades

```text id="vp932z"
[ ] Criar equipe

[ ] Definir líder

[ ] Consultar equipe

[ ] Enviar convite

[ ] Aceitar convite

[ ] Rejeitar convite

[ ] Solicitar entrada

[ ] Aprovar solicitação

[ ] Rejeitar solicitação

[ ] Adicionar integrante pelo organizador

[ ] Validar mínimo de integrantes

[ ] Validar máximo de integrantes

[ ] Alterar estado da equipe

[ ] Desclassificar equipe

[ ] Registrar motivo de desclassificação
```

## Antes de avançar

```text id="yoktw4"
[ ] Apenas hackathon com equipes permite criação

[ ] Criador pode ser definido como líder

[ ] Líder pertence à equipe

[ ] Convites funcionam

[ ] Solicitações funcionam

[ ] Equipe nunca ultrapassa limite máximo

[ ] Equipe abaixo do mínimo não é considerada apta

[ ] Desclassificação exige motivo

[ ] Equipe desclassificada permanece no histórico

[ ] Testes de equipe passaram no Postman
```

---

# SPRINT 17 — Submissões

## Objetivo

Implementar entrega e versionamento dos projetos.

## Funcionalidades

```text id="y9hoph"
[ ] Criar submissão

[ ] Submissão individual

[ ] Submissão por equipe

[ ] Enviar versão

[ ] Registrar data e horário

[ ] Manter histórico de versões

[ ] Bloquear antes da abertura

[ ] Bloquear após o prazo

[ ] Identificar versão oficial

[ ] Consultar submissões
```

## Antes de avançar

```text id="p05b3t"
[ ] Apenas participante elegível consegue enviar

[ ] Período de submissão é respeitado

[ ] Nova versão não apaga a anterior

[ ] Histórico pode ser consultado

[ ] Versão oficial pode ser identificada

[ ] Testes de submissão passaram no Postman
```

---

# SPRINT 18 — Avaliação

## Objetivo

Permitir registro de critérios, jurados e avaliações.

## Funcionalidades

```text id="1y5anl"
[ ] Criar critérios

[ ] Editar critérios

[ ] Definir peso opcional

[ ] Associar jurados

[ ] Remover jurados

[ ] Registrar avaliação

[ ] Registrar observação

[ ] Permitir múltiplos jurados
```

## Antes de avançar

```text id="sq5z59"
[ ] Critérios podem ser cadastrados

[ ] Pesos são opcionais

[ ] Jurados podem ser associados

[ ] Usuário não associado não avalia

[ ] Múltiplos jurados podem avaliar a mesma equipe

[ ] Avaliações permanecem independentes

[ ] Testes de avaliação passaram no Postman
```

---

# SPRINT 19 — Resultados e Ranking

## Objetivo

Publicar a classificação final dos hackathons.

## Funcionalidades

```text id="kt1v7q"
[ ] Registrar resultado

[ ] Atualizar resultado

[ ] Criar ranking

[ ] Manter ranking oculto

[ ] Publicar ranking

[ ] Permitir empate

[ ] Registrar desempate quando necessário

[ ] Exibir colocação
```

## Antes de avançar

```text id="nzhzyl"
[ ] Resultado pode ser cadastrado sem cálculo automático obrigatório

[ ] Ranking pode permanecer oculto

[ ] Ranking pode ser publicado

[ ] Empates são suportados

[ ] Plataforma não inventa desempate

[ ] Colocação oficial pode ser consultada

[ ] Testes de resultado e ranking passaram no Postman
```

---

# SPRINT 20 — Emblemas

## Objetivo

Adicionar conquistas visuais ao histórico do usuário.

## Funcionalidades

```text id="g9a2f9"
[ ] Criar emblema

[ ] Definir nome

[ ] Definir descrição

[ ] Definir imagem

[ ] Conceder emblema

[ ] Exibir no perfil

[ ] Preservar histórico
```

## Antes de avançar

```text id="yhxshm"
[ ] Emblema pertence ao evento

[ ] Concessão fica associada ao usuário

[ ] Usuário não concede emblema a si próprio

[ ] Emblema aparece no perfil

[ ] Histórico permanece após encerramento do evento

[ ] Testes de emblemas passaram no Postman
```

---

# SPRINT 21 — Certificados

## Objetivo

Permitir emissão e consulta de certificados.

## Funcionalidades

```text id="0v4wft"
[ ] Criar tipo de certificado

[ ] Emitir certificado

[ ] Associar certificado ao evento

[ ] Associar certificado ao usuário

[ ] Consultar certificados

[ ] Exibir certificados no perfil
```

## Antes de avançar

```text id="rs0pyu"
[ ] Certificado possui evento de origem

[ ] Certificado possui usuário destinatário

[ ] Certificado pode ser consultado

[ ] Certificado permanece após encerramento do evento

[ ] Testes de certificados passaram no Postman
```

---

# SPRINT 22 — Histórico Público

## Objetivo

Consolidar o perfil como histórico de participação e conquistas.

## Funcionalidades

```text id="p8s4ft"
[ ] Exibir eventos participados

[ ] Exibir hackathons participados

[ ] Exibir colocações

[ ] Exibir emblemas

[ ] Exibir certificados
```

## Antes de avançar

```text id="30arqe"
[ ] Histórico do usuário está consistente

[ ] Evento cancelado continua identificado corretamente

[ ] Resultados oficiais aparecem corretamente

[ ] Emblemas permanecem registrados

[ ] Certificados permanecem registrados

[ ] Testes do histórico passaram no Postman
```

---

# SPRINT 23 — Seguidores

## Objetivo

Adicionar a camada social básica da plataforma.

## Funcionalidades

```text id="fb3h31"
[ ] Seguir usuário

[ ] Deixar de seguir usuário

[ ] Listar seguidores

[ ] Listar usuários seguidos

[ ] Seguir empresa

[ ] Deixar de seguir empresa

[ ] Listar empresas seguidas
```

## Antes de avançar

```text id="4xh9ku"
[ ] Usuário não segue a si próprio

[ ] Seguimento duplicado é impedido

[ ] Follow e unfollow funcionam

[ ] Seguidores podem ser consultados

[ ] Empresas podem ser seguidas

[ ] Testes sociais passaram no Postman
```

---

# SPRINT 24 — Patrocinadores

## Objetivo

Permitir representação dos patrocinadores dentro dos eventos.

## Funcionalidades

```text id="frr6pd"
[ ] Vincular patrocinador

[ ] Remover patrocinador

[ ] Listar patrocinadores

[ ] Permitir múltiplos patrocinadores

[ ] Permitir múltiplos eventos por patrocinador

[ ] Configurar categoria de patrocínio quando aplicável

[ ] Associar patrocinador a desafio
```

## Antes de avançar

```text id="0l4ajz"
[ ] Patrocinador pertence a uma empresa existente

[ ] Evento aceita múltiplos patrocinadores

[ ] Empresa pode patrocinar múltiplos eventos

[ ] Relação duplicada é impedida

[ ] Patrocinadores aparecem no evento

[ ] Testes de patrocínio passaram no Postman
```

---

# SPRINT 25 — Estandes e Ofertas

## Objetivo

Completar a presença dos patrocinadores no evento.

## Funcionalidades

```text id="6gcjfo"
[ ] Criar estande

[ ] Editar estande

[ ] Consultar estande

[ ] Definir estande físico

[ ] Definir estande virtual

[ ] Definir estande híbrido

[ ] Criar oferta

[ ] Consultar oferta

[ ] Definir período da oferta
```

## Antes de avançar

```text id="dk9doz"
[ ] Estande pertence ao evento

[ ] Empresa relacionada existe

[ ] Localização ou acesso virtual funciona quando aplicável

[ ] Oferta possui período coerente

[ ] Oferta pode ser consultada

[ ] Testes passaram no Postman
```

---

# SPRINT 26 — Comunicação

## Objetivo

Permitir que organizadores se comuniquem com participantes.

## Funcionalidades

```text id="1m0enw"
[ ] Criar comunicado

[ ] Comunicado geral

[ ] Comunicado para atividade

[ ] Comunicado para hackathon

[ ] Comunicado para equipe

[ ] Comunicado para lista de espera

[ ] Consultar comunicados
```

## Antes de avançar

```text id="gt2vg4"
[ ] Organizador consegue criar comunicado

[ ] Público correto recebe o comunicado

[ ] Usuário sem permissão não cria comunicado

[ ] Recursos destinatários inexistentes são rejeitados

[ ] Comunicados podem ser consultados

[ ] Testes de comunicação passaram no Postman
```

---

# SPRINT 27 — Notificações

## Objetivo

Adicionar a central de notificações e preferências.

## Funcionalidades

```text id="zuvkpy"
[ ] Criar central de notificações

[ ] Listar notificações

[ ] Diferenciar lidas e não lidas

[ ] Marcar como lida

[ ] Marcar todas como lidas

[ ] Configurar preferências

[ ] Notificações essenciais

[ ] Notificar alteração de evento

[ ] Notificar convite de equipe

[ ] Notificar solicitação de equipe

[ ] Notificar vaga da lista de espera

[ ] Notificar mudança de fase

[ ] Notificar resultado

[ ] Notificar emblema

[ ] Notificar certificado

[ ] Notificar novo evento de empresa seguida
```

## Antes de avançar

```text id="kg7xgb"
[ ] Central funciona

[ ] Lida/não lida funciona

[ ] Preferências são persistidas

[ ] Promoções podem ser desativadas

[ ] Notificações essenciais respeitam regra própria

[ ] Eventos importantes geram notificações corretamente

[ ] Equipes geram notificações corretamente

[ ] Resultados e conquistas geram notificações

[ ] Testes de notificações passaram no Postman
```

---

# SPRINT 28 — Revisão Integrada

## Objetivo

Validar todos os módulos funcionando em conjunto.

## Fluxo completo a testar

```text id="6q089a"
Criar usuário
        ↓
Login
        ↓
Criar empresa
        ↓
Solicitar verificação
        ↓
Administrador aprova empresa
        ↓
Criar evento
        ↓
Administrador aprova evento
        ↓
Publicar evento
        ↓
Usuário encontra evento
        ↓
Usuário se inscreve
        ↓
Consulta programação
        ↓
Participa de atividade
        ↓
Participa do hackathon
        ↓
Cria/entra em equipe
        ↓
Envia submissão
        ↓
Recebe avaliação
        ↓
Resultado publicado
        ↓
Ranking exibido
        ↓
Recebe emblema
        ↓
Recebe certificado
        ↓
Perfil exibe histórico
```

## Antes de considerar a fase concluída

```text id="b3spmt"
[ ] Fluxo completo funciona

[ ] Não existem dependências quebradas

[ ] Estados permanecem coerentes

[ ] Relacionamentos permanecem íntegros

[ ] Paginação foi validada

[ ] Filtros foram validados

[ ] Permissões foram validadas

[ ] Histórico foi validado

[ ] Collection do Postman está organizada

[ ] Todos os testes críticos passaram

[ ] Documentação está sincronizada
```

---

# 3. Resumo das Sprints

```text id="w57fzf"
Sprint 0  — Preparação Técnica

Sprint 1  — Usuários e Autenticação

Sprint 2  — Perfil Público

Sprint 3  — Empresas

Sprint 4  — Verificação de Empresas

Sprint 5  — Eventos

Sprint 6  — Aprovação e Publicação

Sprint 7  — Busca e Descoberta

Sprint 8  — Inscrições

Sprint 9  — Lista de Espera

Sprint 10 — Programação e Trilhas

Sprint 11 — Atividades

Sprint 12 — Check-in

Sprint 13 — Base de Hackathons

Sprint 14 — Fases

Sprint 15 — Desafios

Sprint 16 — Equipes

Sprint 17 — Submissões

Sprint 18 — Avaliação

Sprint 19 — Resultados e Ranking

Sprint 20 — Emblemas

Sprint 21 — Certificados

Sprint 22 — Histórico Público

Sprint 23 — Seguidores

Sprint 24 — Patrocinadores

Sprint 25 — Estandes e Ofertas

Sprint 26 — Comunicação

Sprint 27 — Notificações

Sprint 28 — Revisão Integrada
```

---

# 4. Dependência Macro

```text id="w75dwe"
BASE TÉCNICA
    ↓
USUÁRIOS
    ↓
EMPRESAS
    ↓
VERIFICAÇÃO
    ↓
EVENTOS
    ↓
INSCRIÇÕES
    ↓
PROGRAMAÇÃO
    ↓
HACKATHONS
    ↓
EQUIPES
    ↓
SUBMISSÕES
    ↓
AVALIAÇÃO
    ↓
RESULTADOS
    ↓
CONQUISTAS
```

Recursos complementares:

```text id="p9g20v"
SOCIAL

PATROCINADORES

COMUNICAÇÃO

NOTIFICAÇÕES
```

são adicionados após a estabilidade do núcleo principal.

---

# 5. Regra de Bloqueio

Se uma funcionalidade obrigatória da Sprint atual estiver quebrada, a equipe não deve simplesmente ignorá-la para iniciar funcionalidades dependentes.

Exemplo:

```text id="h14725"
Cadastro de evento não funciona
        ↓
não iniciar
        ↓
Inscrição em evento
```

Outro exemplo:

```text id="0to1fn"
Equipe não funciona
        ↓
não iniciar
        ↓
Submissão por equipe
```

---

# 6. Exceção para Trabalho Paralelo

A regra de avanço não impede que membros diferentes trabalhem em paralelo quando não houver dependência direta.

Exemplo:

Enquanto parte da equipe trabalha em:

```text id="vvxd66"
backend de perfil
```

outro integrante pode trabalhar em:

```text id="f6g6iu"
interface visual do perfil
```

desde que ambos utilizem o mesmo contrato definido na documentação.

---

# 7. Pull Request / Entrega da Sprint

Quando a equipe utilizar versionamento com branches, uma funcionalidade deve ser integrada somente após:

```text id="ifwaux"
[ ] código revisado

[ ] endpoint executado

[ ] teste Postman realizado

[ ] critérios de aceitação atendidos

[ ] conflito com outras funcionalidades verificado
```

---

# 8. Definition of Done

Para todas as Sprints:

```text id="54y0f5"
FUNCIONALIDADE PRONTA

=

IMPLEMENTADA
+
INTEGRADA
+
FUNCIONANDO
+
TESTADA
+
SEM ERRO BLOQUEADOR
+
DOCUMENTAÇÃO COERENTE
```

---

# 9. Funcionalidades Futuras

Não pertencem às Sprints atuais:

```text id="s5cvlz"
Carteira interna

Créditos do evento

Saldo

Transações

Compras

Estornos

Pagamento interno

Recomendação inteligente de eventos

Analytics avançado
```

Quando alguma delas entrar no escopo, deverá receber uma nova Sprint ou ser incorporada formalmente ao planejamento.

---

# 10. Regra de Manutenção

Caso uma funcionalidade seja:

```text id="knw52c"
adicionada

removida

alterada

adiada
```

deve-se revisar:

```text id="vsc3op"
BACKLOG.md
+
SPRINTS.md
```

O `BACKLOG.md` define **o que precisa ser feito**.

O `SPRINTS.md` define **em qual ordem o trabalho será realizado**.
