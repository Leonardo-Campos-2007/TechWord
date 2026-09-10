# REQUISITOS

## 1. Objetivo do Documento

Este documento descreve os requisitos funcionais e não funcionais da plataforma de eventos e hackathons de tecnologia.

Os requisitos funcionais representam capacidades que o sistema deverá oferecer aos usuários, empresas, organizadores e administradores.

Os requisitos não funcionais representam características de qualidade, organização, compatibilidade, desempenho e comportamento técnico esperado da aplicação.

As regras detalhadas que determinam como cada funcionalidade deve se comportar serão mantidas separadamente no documento `REGRAS-DE-NEGOCIO.md`.

---

# 2. Requisitos Funcionais

## 2.1 Usuários

### RF-001 — Cadastro de usuário

O sistema deve permitir o cadastro de novos usuários.

### RF-002 — Login

O sistema deve permitir que usuários cadastrados realizem login.

### RF-003 — Logout

O sistema deve permitir que usuários autenticados encerrem sua sessão.

### RF-004 — Consulta da própria conta

O sistema deve permitir que o usuário consulte os dados de sua própria conta.

### RF-005 — Atualização da conta

O sistema deve permitir que o usuário altere os dados permitidos de sua conta.

### RF-006 — Identificação de tipo de usuário

O sistema deve distinguir os diferentes tipos de usuários existentes na plataforma.

Os tipos iniciais serão:

* usuário;
* empresa;
* administrador.

---

# 2.2 Perfil do Usuário

### RF-007 — Perfil público

O sistema deve disponibilizar um perfil público para os usuários.

### RF-008 — Consulta de perfil

O sistema deve permitir a visualização do perfil público de outros usuários.

### RF-009 — Edição de perfil

O sistema deve permitir que o usuário edite as informações de seu próprio perfil.

### RF-010 — Foto de perfil

O sistema deve permitir que o usuário defina uma foto de perfil.

### RF-011 — Biografia

O sistema deve permitir que o usuário adicione uma descrição pessoal ao perfil.

### RF-012 — Localização

O sistema deve permitir que o usuário informe sua localização.

### RF-013 — Tecnologias

O sistema deve permitir que o usuário informe tecnologias relacionadas aos seus interesses ou conhecimentos.

Exemplos:

* JavaScript;
* Java;
* Python;
* React;
* Inteligência Artificial;
* Segurança da Informação.

### RF-014 — Áreas de interesse

O sistema deve permitir que o usuário informe suas áreas de interesse.

Exemplos:

* Backend;
* Frontend;
* Mobile;
* Inteligência Artificial;
* Segurança;
* Dados;
* DevOps;
* Games.

### RF-015 — GitHub

O sistema deve permitir que o usuário adicione seu perfil do GitHub.

### RF-016 — LinkedIn

O sistema deve permitir que o usuário adicione seu perfil do LinkedIn.

### RF-017 — Portfólio

O sistema deve permitir que o usuário adicione um endereço para seu portfólio.

### RF-018 — Histórico de eventos

O sistema deve permitir exibir no perfil os eventos dos quais o usuário participou.

### RF-019 — Histórico de hackathons

O sistema deve permitir exibir os hackathons dos quais o usuário participou.

### RF-020 — Colocações

O sistema deve permitir exibir colocações obtidas pelo usuário em hackathons.

### RF-021 — Emblemas

O sistema deve permitir exibir no perfil os emblemas conquistados pelo usuário.

### RF-022 — Certificados

O sistema deve permitir exibir os certificados recebidos pelo usuário.

---

# 2.3 Recursos Sociais

### RF-023 — Seguir usuário

O sistema deve permitir que um usuário siga outro usuário.

### RF-024 — Deixar de seguir usuário

O sistema deve permitir que um usuário deixe de seguir outro usuário.

### RF-025 — Seguidores

O sistema deve permitir consultar os seguidores de um usuário.

### RF-026 — Usuários seguidos

O sistema deve permitir consultar os usuários seguidos por determinado usuário.

### RF-027 — Seguir empresa

O sistema deve permitir que usuários sigam empresas.

### RF-028 — Deixar de seguir empresa

O sistema deve permitir que usuários deixem de seguir empresas.

### RF-029 — Empresas seguidas

O sistema deve permitir que o usuário consulte as empresas que segue.

---

# 2.4 Empresas

### RF-030 — Cadastro de empresa

O sistema deve permitir o cadastro de empresas.

### RF-031 — Página pública da empresa

O sistema deve disponibilizar uma página pública para cada empresa cadastrada.

### RF-032 — Edição da empresa

O sistema deve permitir que uma empresa atualize as informações permitidas de sua página.

### RF-033 — Informações institucionais

O sistema deve permitir que a empresa apresente informações institucionais.

Exemplos:

* nome;
* descrição;
* imagem;
* localização;
* site;
* links externos.

### RF-034 — Eventos organizados

O sistema deve permitir exibir os eventos organizados pela empresa.

### RF-035 — Próximos eventos

O sistema deve permitir exibir os próximos eventos organizados pela empresa.

### RF-036 — Histórico de eventos

O sistema deve permitir exibir eventos anteriores organizados pela empresa.

### RF-037 — Seguidores da empresa

O sistema deve permitir consultar os seguidores da empresa.

---

# 2.5 Verificação de Empresas

### RF-038 — Solicitação de verificação

O sistema deve permitir que uma empresa solicite sua verificação.

### RF-039 — Consulta da verificação

O sistema deve permitir que a empresa consulte o estado de sua solicitação de verificação.

### RF-040 — Consulta de solicitações

O sistema deve permitir que administradores consultem solicitações de verificação pendentes.

### RF-041 — Aprovação de empresa

O sistema deve permitir que administradores aprovem uma empresa.

### RF-042 — Rejeição de empresa

O sistema deve permitir que administradores rejeitem uma solicitação de verificação.

### RF-043 — Motivo de rejeição

O sistema deve permitir registrar o motivo da rejeição de uma solicitação.

### RF-044 — Selo de verificação

O sistema deve exibir um selo de verificação para empresas aprovadas.

---

# 2.6 Eventos

### RF-045 — Criação de evento

O sistema deve permitir que empresas verificadas criem eventos.

### RF-046 — Rascunho de evento

O sistema deve permitir que um evento seja mantido como rascunho antes de sua publicação.

### RF-047 — Edição de rascunho

O sistema deve permitir que o organizador edite um evento ainda não publicado.

### RF-048 — Nome do evento

O sistema deve permitir que o organizador informe o nome do evento.

### RF-049 — Descrição do evento

O sistema deve permitir que o organizador informe a descrição do evento.

### RF-050 — Período do evento

O sistema deve permitir informar data e horário de início e término do evento.

### RF-051 — Modalidade do evento

O sistema deve permitir eventos:

* presenciais;
* online;
* híbridos.

### RF-052 — Localização física

O sistema deve permitir cadastrar localização para eventos presenciais ou híbridos.

### RF-053 — Acesso online

O sistema deve permitir cadastrar informações de acesso para eventos online ou híbridos.

### RF-054 — Evento gratuito

O sistema deve permitir a criação de eventos gratuitos.

### RF-055 — Evento pago

O sistema deve permitir a criação de eventos pagos.

### RF-056 — Capacidade do evento

O sistema deve permitir que o organizador estabeleça um limite de participantes.

### RF-057 — Múltiplos organizadores

O sistema deve permitir que um evento possua mais de uma empresa organizadora.

### RF-058 — Envio para aprovação

O sistema deve permitir que o evento seja enviado para aprovação da plataforma.

### RF-059 — Eventos pendentes

O sistema deve permitir que administradores consultem eventos aguardando aprovação.

### RF-060 — Aprovação de evento

O sistema deve permitir que administradores aprovem eventos.

### RF-061 — Rejeição de evento

O sistema deve permitir que administradores rejeitem eventos.

### RF-062 — Motivo de rejeição do evento

O sistema deve permitir que o administrador informe o motivo da rejeição.

### RF-063 — Publicação de evento

O sistema deve permitir a publicação de eventos aprovados.

### RF-064 — Edição de evento publicado

O sistema deve permitir que organizadores alterem eventos já publicados.

### RF-065 — Cancelamento de evento

O sistema deve permitir que o organizador cancele um evento.

### RF-066 — Histórico de evento cancelado

O sistema deve manter disponível o registro de um evento cancelado.

### RF-067 — Encerramento de evento

O sistema deve permitir que um evento seja identificado como encerrado.

### RF-068 — Consulta de evento

O sistema deve permitir que usuários consultem as informações de um evento.

---

# 2.7 Busca e Descoberta de Eventos

### RF-069 — Listagem de eventos

O sistema deve permitir listar eventos disponíveis.

### RF-070 — Busca por nome

O sistema deve permitir pesquisar eventos pelo nome.

### RF-071 — Busca por localização

O sistema deve permitir encontrar eventos próximos à região do usuário.

### RF-072 — Filtro por modalidade

O sistema deve permitir filtrar eventos por:

* presencial;
* online;
* híbrido.

### RF-073 — Filtro por período

O sistema deve permitir filtrar eventos por data ou período.

### RF-074 — Filtro por categoria

O sistema deve permitir filtrar eventos por categoria.

### RF-075 — Filtro por preço

O sistema deve permitir diferenciar eventos gratuitos e pagos.

### RF-076 — Ordenação

O sistema deve permitir ordenar os resultados das buscas.

---

# 2.8 Inscrição em Eventos

### RF-077 — Inscrição

O sistema deve permitir que usuários se inscrevam em eventos.

### RF-078 — Consulta de inscrição

O usuário deve poder consultar o estado de sua inscrição.

### RF-079 — Participantes inscritos

O organizador deve poder consultar os usuários inscritos no evento.

### RF-080 — Inscrição automática

O sistema deve permitir eventos com inscrição automática.

### RF-081 — Inscrição por aprovação

O sistema deve permitir eventos nos quais a inscrição dependa de aprovação do organizador.

### RF-082 — Aprovação de inscrição

O organizador deve poder aprovar uma solicitação de inscrição.

### RF-083 — Rejeição de inscrição

O organizador deve poder rejeitar uma solicitação.

### RF-084 — Cancelamento de inscrição

O usuário deve poder cancelar sua própria inscrição.

### RF-085 — Controle de vagas

O sistema deve controlar o número de participantes conforme a capacidade definida para o evento.

### RF-086 — Lista de espera

O organizador deve poder habilitar lista de espera.

### RF-087 — Entrada na lista de espera

O sistema deve permitir que usuários sejam adicionados à lista de espera quando as vagas estiverem esgotadas e essa opção estiver habilitada.

### RF-088 — Oferta de vaga

O sistema deve permitir disponibilizar uma vaga liberada para um usuário da lista de espera.

### RF-089 — Confirmação de participação

O sistema deve permitir que o usuário confirme sua participação quando necessário.

### RF-090 — Consulta de capacidade

O organizador deve poder consultar:

* vagas totais;
* vagas ocupadas;
* vagas disponíveis.

---

# 2.9 Programação do Evento

### RF-091 — Programação

O sistema deve permitir que o organizador crie uma programação para o evento.

### RF-092 — Criação de trilha

O sistema deve permitir criar trilhas dentro do evento.

### RF-093 — Edição de trilha

O sistema deve permitir editar trilhas.

### RF-094 — Exclusão de trilha

O sistema deve permitir remover uma trilha quando sua remoção for permitida.

### RF-095 — Consulta de trilhas

Usuários devem poder consultar as trilhas existentes.

### RF-096 — Atividade sem trilha

O sistema deve permitir atividades que não estejam vinculadas a nenhuma trilha.

---

# 2.10 Atividades

### RF-097 — Criação de atividade

O sistema deve permitir que o organizador crie atividades.

### RF-098 — Edição de atividade

O sistema deve permitir editar atividades.

### RF-099 — Tipo de atividade

O sistema deve permitir informar o tipo da atividade.

Exemplos:

* palestra;
* workshop;
* minicurso;
* apresentação;
* networking;
* cerimônia;
* atividade personalizada.

### RF-100 — Horário da atividade

O sistema deve permitir definir data e horário de uma atividade.

### RF-101 — Local da atividade

O sistema deve permitir informar o local físico ou virtual da atividade.

### RF-102 — Associação com trilha

O sistema deve permitir associar uma atividade a uma trilha.

### RF-103 — Capacidade da atividade

O sistema deve permitir definir uma quantidade máxima de participantes para uma atividade.

### RF-104 — Inscrição específica

O sistema deve permitir que atividades exijam inscrição separada.

### RF-105 — Inscrição em atividade

O sistema deve permitir que usuários se inscrevam em atividades.

### RF-106 — Cancelamento de inscrição em atividade

O sistema deve permitir que o usuário cancele sua inscrição em uma atividade.

### RF-107 — Participantes da atividade

O organizador deve poder consultar os usuários inscritos em uma atividade.

---

# 2.11 Check-in

### RF-108 — Check-in no evento

O sistema deve permitir que o organizador habilite check-in no evento.

### RF-109 — Registro de check-in

O sistema deve permitir registrar a presença de um participante no evento.

### RF-110 — Check-in em atividade

O sistema deve permitir habilitar check-in individual em determinadas atividades.

### RF-111 — Registro de presença em atividade

O sistema deve permitir registrar presença do participante na atividade.

### RF-112 — Consulta de presença

O organizador deve poder consultar os registros de presença.

---

# 2.12 Hackathons

### RF-113 — Hackathon

O sistema deve permitir que um evento possua funcionalidades específicas de hackathon.

### RF-114 — Participação individual

O sistema deve permitir hackathons com participação individual.

### RF-115 — Participação por equipe

O sistema deve permitir hackathons com participação em equipe.

### RF-116 — Participação híbrida

O sistema deve permitir hackathons que aceitem participantes individuais e equipes.

### RF-117 — Quantidade mínima de integrantes

O organizador deve poder definir a quantidade mínima de integrantes de uma equipe.

### RF-118 — Quantidade máxima de integrantes

O organizador deve poder definir a quantidade máxima de integrantes.

### RF-119 — Consulta das regras

Os participantes devem poder consultar as configurações e regras de participação do hackathon.

---

# 2.13 Fases do Hackathon

### RF-120 — Criação de fase

O organizador deve poder criar fases para o hackathon.

### RF-121 — Edição de fase

O organizador deve poder editar fases.

### RF-122 — Ordenação de fases

O organizador deve poder definir a ordem das fases.

### RF-123 — Período da fase

O organizador deve poder determinar data e horário de início e término de uma fase.

### RF-124 — Fase personalizada

O sistema deve permitir que o organizador crie fases personalizadas.

### RF-125 — Fase atual

O participante deve poder identificar a fase atual do hackathon.

### RF-126 — Próximas fases

O participante deve poder consultar as próximas fases.

---

# 2.14 Desafios

### RF-127 — Criação de desafio

O organizador deve poder criar desafios.

### RF-128 — Edição de desafio

O organizador deve poder editar desafios.

### RF-129 — Consulta de desafio

Os participantes devem poder consultar os detalhes de um desafio.

### RF-130 — Patrocinador do desafio

O sistema deve permitir associar um patrocinador a um desafio.

---

# 2.15 Equipes

### RF-131 — Criação de equipe

O sistema deve permitir que participantes criem equipes quando o hackathon permitir.

### RF-132 — Líder da equipe

O sistema deve permitir que uma equipe possua um líder ou responsável.

### RF-133 — Consulta de equipe

O sistema deve permitir consultar os integrantes e informações permitidas de uma equipe.

### RF-134 — Convite para equipe

O sistema deve permitir que participantes sejam convidados para uma equipe.

### RF-135 — Aceitação de convite

O usuário deve poder aceitar um convite.

### RF-136 — Rejeição de convite

O usuário deve poder rejeitar um convite.

### RF-137 — Solicitação de entrada

O sistema deve permitir que um participante solicite entrada em uma equipe.

### RF-138 — Aprovação da solicitação

O responsável pela equipe deve poder aprovar a solicitação.

### RF-139 — Rejeição da solicitação

O responsável pela equipe deve poder rejeitar a solicitação.

### RF-140 — Formação pelo organizador

O organizador deve poder formar equipes manualmente.

### RF-141 — Validação de tamanho da equipe

O sistema deve identificar se uma equipe atende ao limite mínimo e máximo de integrantes.

### RF-142 — Estado da equipe

O sistema deve permitir acompanhar o estado atual da equipe.

### RF-143 — Desclassificação

O organizador deve poder desclassificar uma equipe.

### RF-144 — Motivo da desclassificação

O sistema deve permitir registrar o motivo da desclassificação.

---

# 2.16 Submissões

### RF-145 — Criação de submissão

O sistema deve permitir que um participante ou equipe realize uma submissão.

### RF-146 — Múltiplas versões

O sistema deve permitir o envio de múltiplas versões de uma submissão.

### RF-147 — Histórico de versões

O sistema deve manter o histórico das versões enviadas.

### RF-148 — Data da submissão

O sistema deve registrar a data e o horário de cada versão enviada.

### RF-149 — Abertura das submissões

O sistema deve respeitar o período definido pelo organizador para início das submissões.

### RF-150 — Encerramento das submissões

O sistema deve impedir novas submissões após o prazo definido.

### RF-151 — Versão oficial

O sistema deve permitir identificar a versão válida para avaliação.

### RF-152 — Consulta de submissões

O organizador deve poder consultar as submissões realizadas.

---

# 2.17 Avaliação

### RF-153 — Critério de avaliação

O sistema deve permitir que o organizador cadastre critérios de avaliação.

### RF-154 — Peso do critério

O sistema deve permitir que critérios possuam pesos quando utilizados pelo evento.

### RF-155 — Edição de critério

O organizador deve poder alterar critérios enquanto a operação for permitida.

### RF-156 — Jurados

O sistema deve permitir associar jurados ao hackathon.

### RF-157 — Múltiplos jurados

O sistema deve permitir que uma equipe seja avaliada por vários jurados.

### RF-158 — Registro de avaliação

O sistema deve permitir registrar avaliações.

### RF-159 — Observações

O sistema deve permitir registrar observações relacionadas à avaliação.

### RF-160 — Resultado final

O organizador deve poder informar o resultado oficial do hackathon.

### RF-161 — Exibição de resultados

O sistema deve permitir apresentar os resultados aos participantes.

### RF-162 — Resultado externo

O sistema deve permitir registrar resultados definidos externamente ou diretamente pela organização, sem exigir um cálculo automático universal.

---

# 2.18 Ranking

### RF-163 — Ranking

O sistema deve permitir manter uma classificação dos participantes ou equipes.

### RF-164 — Atualização do ranking

O organizador deve poder atualizar o ranking.

### RF-165 — Ranking oculto

O organizador deve poder manter o ranking oculto durante o hackathon.

### RF-166 — Publicação do ranking

O organizador deve poder liberar o ranking para visualização.

### RF-167 — Empates

O sistema deve permitir empates quando as regras do evento autorizarem.

### RF-168 — Desempate

O sistema deve permitir registrar critérios de desempate definidos pelo evento.

### RF-169 — Colocação no perfil

O sistema deve permitir exibir a colocação obtida no perfil do usuário.

---

# 2.19 Emblemas e Troféus

### RF-170 — Criação de emblema

O organizador deve poder criar emblemas específicos de um evento.

### RF-171 — Informações do emblema

O sistema deve permitir definir:

* nome;
* descrição;
* imagem ou representação visual.

### RF-172 — Concessão de emblema

O sistema deve permitir conceder um emblema a um usuário.

### RF-173 — Origem do emblema

O sistema deve manter a associação entre o emblema recebido e seu evento de origem.

### RF-174 — Exibição no perfil

O usuário deve poder exibir seus emblemas no perfil público.

### RF-175 — Histórico de emblemas

O sistema deve manter o histórico de emblemas recebidos.

---

# 2.20 Certificados

### RF-176 — Configuração de certificado

O sistema deve permitir que um evento possua certificados.

### RF-177 — Emissão de certificado

O sistema deve permitir emitir certificados para usuários.

### RF-178 — Associação ao evento

O certificado deve estar associado ao evento que o originou.

### RF-179 — Consulta de certificados

O usuário deve poder consultar seus certificados.

### RF-180 — Exibição de certificados

O usuário deve poder exibir certificados no perfil.

---

# 2.21 Patrocinadores

### RF-181 — Associação de patrocinador

O organizador deve poder associar empresas patrocinadoras ao evento.

### RF-182 — Múltiplos patrocinadores

Um evento deve poder possuir vários patrocinadores.

### RF-183 — Histórico de patrocínios

Uma empresa deve poder estar associada como patrocinadora a vários eventos.

### RF-184 — Exibição de patrocinadores

O sistema deve exibir os patrocinadores relacionados ao evento.

### RF-185 — Estande

O sistema deve permitir cadastrar um estande relacionado a um patrocinador.

### RF-186 — Localização de estande

O sistema deve permitir informar localização física ou virtual do estande.

### RF-187 — Oferta

O sistema deve permitir que patrocinadores possuam ofertas relacionadas ao evento.

### RF-188 — Exibição de oferta

Usuários devem poder consultar as ofertas disponíveis.

---

# 2.22 Comunicação do Evento

### RF-189 — Criação de comunicado

O organizador deve poder criar comunicados relacionados ao evento.

### RF-190 — Comunicado geral

O sistema deve permitir enviar um comunicado para todos os participantes.

### RF-191 — Comunicado segmentado

O sistema deve permitir direcionar comunicados a grupos específicos.

### RF-192 — Comunicação por atividade

O sistema deve permitir enviar comunicados aos inscritos em determinada atividade.

### RF-193 — Comunicação de hackathon

O sistema deve permitir direcionar comunicados aos participantes de um hackathon.

### RF-194 — Comunicação por equipe

O sistema deve permitir direcionar comunicados relacionados a determinadas equipes quando aplicável.

### RF-195 — Consulta de comunicados

O usuário deve poder consultar os comunicados relacionados aos eventos dos quais participa.

---

# 2.23 Notificações

### RF-196 — Central de notificações

O sistema deve possuir uma central de notificações.

### RF-197 — Notificação lida

O usuário deve poder marcar uma notificação como lida.

### RF-198 — Notificação não lida

O sistema deve distinguir notificações ainda não visualizadas.

### RF-199 — Preferências de notificação

O usuário deve poder personalizar quais categorias de notificação deseja receber.

### RF-200 — Mudança de horário

O sistema deve poder notificar alterações de horários.

### RF-201 — Mudança de local

O sistema deve poder notificar alterações de local.

### RF-202 — Cancelamento

O sistema deve informar participantes quando um evento for cancelado.

### RF-203 — Atividade próxima

O sistema deve poder notificar o usuário sobre uma atividade próxima.

### RF-204 — Mudança de fase

O sistema deve poder informar abertura ou encerramento de fases de hackathon.

### RF-205 — Convite para equipe

O sistema deve informar o usuário quando receber convite para uma equipe.

### RF-206 — Solicitação de entrada

O sistema deve informar o responsável pela equipe sobre solicitações de entrada.

### RF-207 — Vaga disponível

O sistema deve poder informar participantes da lista de espera quando uma vaga for oferecida.

### RF-208 — Resultado publicado

O sistema deve poder informar participantes quando resultados forem publicados.

### RF-209 — Novo emblema

O sistema deve informar o usuário quando receber um emblema.

### RF-210 — Novo certificado

O sistema deve informar o usuário quando um certificado for disponibilizado.

### RF-211 — Evento de empresa seguida

O sistema deve poder informar usuários sobre novos eventos publicados por empresas que seguem.

### RF-212 — Categoria da notificação

O sistema deve permitir classificar notificações em categorias.

Categorias previstas:

* essenciais;
* operacionais;
* sociais;
* promocionais.

### RF-213 — Notificação essencial

O sistema deve permitir que determinadas notificações essenciais permaneçam ativas independentemente das preferências opcionais do usuário.

---

# 3. Requisitos Não Funcionais

## 3.1 Tecnologia

### RNF-001 — Linguagem

A aplicação deve utilizar JavaScript como linguagem principal.

### RNF-002 — Runtime

A aplicação deve utilizar Node.js como ambiente de execução do lado servidor.

### RNF-003 — Framework

A aplicação deve utilizar Next.js como framework principal.

### RNF-004 — Frontend

A interface deve ser construída utilizando Next.js/React, HTML e CSS.

### RNF-005 — Projeto único

A primeira versão deve utilizar uma aplicação full-stack única, mantendo frontend e backend no mesmo projeto Next.js.

---

# 3.2 Organização e Manutenção

### RNF-006 — Separação de responsabilidades

O código deve ser organizado de forma que responsabilidades diferentes permaneçam separadas.

### RNF-007 — Organização da camada HTTP

As rotas responsáveis por receber requisições HTTP não devem concentrar toda a lógica da aplicação.

### RNF-008 — Organização das regras

As regras e operações principais do sistema devem ser mantidas em componentes apropriados para sua responsabilidade.

### RNF-009 — Organização da persistência

O acesso aos dados deve permanecer separado da camada responsável por receber requisições.

### RNF-010 — Padronização

O projeto deve possuir padrão consistente de:

* nomes de arquivos;
* diretórios;
* funções;
* entidades;
* endpoints.

### RNF-011 — Legibilidade

O código deve ser suficientemente organizado e documentado para que os integrantes da equipe consigam compreender seu funcionamento.

### RNF-012 — Reutilização

O projeto deve evitar duplicação desnecessária de regras e funcionalidades.

### RNF-013 — Evolução incremental

A estrutura deve permitir inclusão de novas funcionalidades sem exigir reestruturação completa da aplicação.

### RNF-014 — Dependências justificadas

Novas bibliotecas devem ser adicionadas somente quando necessárias ao projeto.

---

# 3.3 API

### RNF-015 — Comunicação HTTP

Os recursos de backend disponibilizados ao frontend devem utilizar comunicação HTTP quando aplicável.

### RNF-016 — JSON

A API deve utilizar JSON como formato principal de troca de dados.

### RNF-017 — Métodos HTTP

Os endpoints devem utilizar métodos HTTP compatíveis com suas operações.

Exemplos:

* GET;
* POST;
* PATCH;
* DELETE.

### RNF-018 — Códigos HTTP

Os endpoints devem retornar códigos HTTP coerentes com o resultado da operação.

### RNF-019 — Padronização de respostas

As respostas da API devem seguir estrutura consistente.

### RNF-020 — Padronização de erros

As respostas de erro devem possuir estrutura padronizada.

### RNF-021 — Paginação

Listagens que possam apresentar grande quantidade de registros devem suportar paginação.

### RNF-022 — Filtros

Consultas de listagem devem possuir filtros quando exigidos pelo requisito funcional.

### RNF-023 — Ordenação

Listagens devem permitir ordenação quando necessária.

### RNF-024 — Documentação dos endpoints

Os endpoints implementados devem ser documentados no arquivo `API.md`.

---

# 3.4 Validação e Integridade dos Dados

### RNF-025 — Validação de entrada

Dados recebidos pela aplicação devem ser validados antes de serem processados.

### RNF-026 — Campos obrigatórios

A aplicação deve rejeitar operações nas quais informações obrigatórias estejam ausentes.

### RNF-027 — Formato de dados

Campos devem respeitar os formatos esperados.

### RNF-028 — Unicidade

O sistema deve respeitar restrições de unicidade definidas para o domínio.

### RNF-029 — Integridade dos relacionamentos

O sistema não deve permitir relacionamentos com entidades inexistentes.

### RNF-030 — Estados consistentes

Mudanças de estado devem respeitar os estados válidos existentes no domínio.

### RNF-031 — Integridade temporal

Datas de início e término devem possuir valores cronologicamente coerentes.

### RNF-032 — Limites coerentes

Valores mínimos e máximos devem ser validados quando aplicáveis.

Exemplo:

* tamanho mínimo de equipe;
* tamanho máximo de equipe;
* capacidade de atividade;
* capacidade de evento.

### RNF-033 — Preservação histórica

Dados que representem fatos históricos relevantes devem permanecer disponíveis quando necessário.

Exemplos:

* eventos cancelados;
* submissões antigas;
* certificados;
* emblemas;
* resultados.

---

# 3.5 Desempenho

### RNF-034 — Tempo de resposta

As operações comuns devem possuir tempo de resposta adequado para utilização interativa da aplicação.

### RNF-035 — Consultas eficientes

A aplicação deve evitar consultas de dados desnecessárias.

### RNF-036 — Grandes listagens

Grandes conjuntos de dados não devem ser carregados integralmente quando paginação puder ser utilizada.

### RNF-037 — Carregamento progressivo

A aplicação deve poder utilizar carregamento progressivo de informações quando necessário.

---

# 3.6 Interface e Usabilidade

### RNF-038 — Interface responsiva

A aplicação deve possuir interface adaptável a diferentes tamanhos de tela.

### RNF-039 — Desktop

A aplicação deve funcionar adequadamente em computadores.

### RNF-040 — Dispositivos móveis

As principais funcionalidades devem ser utilizáveis em dispositivos móveis.

### RNF-041 — Navegação consistente

A interface deve manter padrões consistentes de navegação.

### RNF-042 — Feedback ao usuário

A aplicação deve fornecer retorno visual para ações relevantes.

Exemplos:

* operação concluída;
* erro;
* carregamento;
* confirmação.

### RNF-043 — Estados visuais

Estados importantes devem possuir representação visual compreensível.

Exemplos:

* aprovado;
* pendente;
* rejeitado;
* cancelado;
* encerrado;
* desclassificado.

### RNF-044 — Programação legível

Datas, horários e programação devem ser apresentados de maneira clara.

### RNF-045 — Ranking legível

Classificações devem ser apresentadas de forma compreensível.

### RNF-046 — Conquistas

Emblemas, colocações e certificados devem possuir apresentação adequada no perfil.

---

# 3.7 Acessibilidade

### RNF-047 — HTML semântico

A interface deve utilizar HTML semanticamente adequado sempre que possível.

### RNF-048 — Navegação por teclado

Os principais recursos interativos devem poder ser utilizados por teclado quando aplicável.

### RNF-049 — Imagens alternativas

Imagens relevantes devem possuir texto alternativo quando aplicável.

### RNF-050 — Legibilidade

A interface deve utilizar tamanho de texto, espaçamento e contraste adequados à leitura.

---

# 3.8 Compatibilidade

### RNF-051 — Navegadores

A aplicação deve funcionar nos principais navegadores modernos suportados pelo ecossistema do Next.js.

### RNF-052 — Responsividade

O comportamento das funcionalidades principais deve permanecer consistente entre desktop e dispositivos móveis.

---

# 3.9 Testabilidade

### RNF-053 — Testes de API

Os endpoints do sistema devem possuir testes de API realizados com Postman.

### RNF-054 — Cenário de sucesso

Cada endpoint deve possuir pelo menos um cenário de teste válido.

### RNF-055 — Entrada inválida

Endpoints que recebem informações devem ser testados com dados inválidos.

### RNF-056 — Campos ausentes

Devem ser testadas situações de ausência de campos obrigatórios.

### RNF-057 — Recurso inexistente

Operações que utilizem identificadores devem possuir testes utilizando recursos inexistentes.

### RNF-058 — Duplicidade

Operações sujeitas a duplicidade devem possuir testes correspondentes.

### RNF-059 — Regras importantes

Regras de negócio relevantes devem possuir cenários de teste no Postman.

### RNF-060 — Organização dos testes

Os testes do Postman devem ser organizados por área funcional da aplicação.

Exemplo:

```text
Usuarios
Empresas
Eventos
Inscricoes
Atividades
Hackathons
Equipes
Submissoes
Resultados
```

### RNF-061 — Validação antes da próxima Sprint

As funcionalidades obrigatórias de uma Sprint devem ser validadas antes do início da Sprint seguinte.

---

# 3.10 Configuração

### RNF-062 — Variáveis de ambiente

Configurações dependentes do ambiente devem ser armazenadas de forma configurável.

### RNF-063 — Exemplo de configuração

O projeto deve possuir documentação das variáveis necessárias para sua execução.

### RNF-064 — Execução local

O projeto deve possuir instruções para execução em ambiente local.

### RNF-065 — Dependências do projeto

As dependências utilizadas devem estar registradas no gerenciador de pacotes do projeto.

---

# 3.11 Confiabilidade

### RNF-066 — Estado consistente

Falhas durante uma operação não devem deixar informações principais do sistema em estados inconsistentes.

### RNF-067 — Tratamento de falhas

Erros esperados devem ser tratados pela aplicação.

### RNF-068 — Histórico de submissões

Novas versões de uma submissão não devem apagar silenciosamente as versões anteriores.

### RNF-069 — Histórico de conquistas

A concessão de um emblema deve permanecer registrada.

### RNF-070 — Histórico de certificados

Certificados emitidos devem permanecer associados ao usuário.

### RNF-071 — Histórico de eventos cancelados

Eventos cancelados devem continuar disponíveis como registro histórico.

---

# 4. Funcionalidades Futuras

As funcionalidades abaixo fazem parte da visão do produto, mas ficam fora do escopo inicial de implementação.

## 4.1 Carteira interna do evento

A plataforma poderá futuramente permitir que o participante adicione créditos para uso dentro de determinado evento.

Possíveis funcionalidades futuras:

* adicionar créditos;
* consultar saldo;
* realizar compras;
* consultar movimentações;
* receber estornos;
* utilizar créditos em estandes e estabelecimentos participantes.

## 4.2 Sistema interno de pagamentos

A plataforma poderá futuramente possuir um sistema privado de pagamentos dentro dos eventos que optarem por utilizar essa funcionalidade.

Esse módulo deverá possuir requisitos próprios quando for incluído oficialmente no escopo.

---

# 5. Quantidade de Requisitos

A versão atual contém:

* **213 requisitos funcionais**
* **71 requisitos não funcionais**

Total:

**284 requisitos documentados.**

---

# 6. Observação

Este documento deve representar apenas **o que o sistema precisa oferecer e quais características gerais deve possuir**.

Detalhes como:

* regras específicas de aprovação;
* transições de estado;
* restrições;
* condições;
* cálculos;
* permissões específicas;
* funcionamento interno;

serão documentados em `REGRAS-DE-NEGOCIO.md`.

Detalhes relacionados a:

* Route Handler;
* Service;
* Repository;
* DTO;
* Entity;
* estrutura de diretórios;

serão tratados em `ARQUITETURA.md` e `GUIA-CICLO-ENDPOINT.md`.

Endpoints e contratos HTTP serão tratados exclusivamente em `API.md`.

Testes serão tratados exclusivamente em `TESTES-POSTMAN.md`.

Planejamento de implementação será tratado em `BACKLOG.md` e `SPRINTS.md`.
