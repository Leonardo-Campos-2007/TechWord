# BACKLOG

## 1. Objetivo do Documento

Este documento organiza o trabalho necessário para implementar a plataforma de eventos e hackathons de tecnologia.

O backlog é dividido em:

* épicos;
* histórias de usuário;
* prioridades;
* dependências;
* critérios de aceitação;
* tarefas técnicas gerais.

A distribuição das histórias entre Sprints será realizada exclusivamente no documento:

```text
SPRINTS.md
```

---

# 2. Prioridades

As prioridades utilizadas são:

```text
P0 = Crítica
P1 = Alta
P2 = Média
P3 = Futura
```

### P0 — Crítica

Funcionalidade essencial para o funcionamento básico do sistema.

### P1 — Alta

Funcionalidade importante para completar o fluxo principal.

### P2 — Média

Funcionalidade relevante, mas que pode ser implementada depois da base principal.

### P3 — Futura

Funcionalidade complementar ou de evolução.

---

# 3. Regras de Dependência

Uma história somente deve ser iniciada quando suas dependências obrigatórias estiverem disponíveis.

Exemplo:

```text
US-030 — Inscrever usuário em evento

depende de:

US-001 — Cadastrar usuário
US-020 — Criar evento
```

Prioridade e dependência são conceitos diferentes.

Uma história P0 ainda pode depender de outra história.

---

# EP-001 — Contas de Usuário

Objetivo:

Permitir que usuários criem e utilizem suas contas na plataforma.

---

## US-001 — Cadastrar usuário

**Como** visitante,
**quero** criar uma conta,
**para** utilizar os recursos da plataforma.

Prioridade:

```text
P0
```

Dependências:

```text
Nenhuma funcional.
```

Critérios de aceitação:

```text
[ ] Deve ser possível informar nome, e-mail e senha.

[ ] O cadastro deve rejeitar dados obrigatórios ausentes.

[ ] O sistema deve impedir e-mail já cadastrado.

[ ] O usuário criado deve possuir identificador próprio.

[ ] Dados internos de senha não devem aparecer na resposta.
```

---

## US-002 — Realizar login

**Como** usuário cadastrado,
**quero** realizar login,
**para** acessar os recursos associados à minha conta.

Prioridade:

```text
P0
```

Dependências:

```text
US-001
```

Critérios de aceitação:

```text
[ ] Credenciais válidas devem permitir acesso.

[ ] E-mail inexistente deve ser rejeitado.

[ ] Senha incorreta deve ser rejeitada.

[ ] O usuário autenticado deve ser identificável pelo sistema.
```

---

## US-003 — Encerrar sessão

**Como** usuário autenticado,
**quero** encerrar minha sessão,
**para** finalizar meu acesso atual.

Prioridade:

```text
P1
```

Dependências:

```text
US-002
```

Critérios:

```text
[ ] Usuário autenticado deve conseguir encerrar sessão.

[ ] A sessão encerrada não deve continuar válida.
```

---

## US-004 — Consultar minha conta

**Como** usuário autenticado,
**quero** consultar meus dados,
**para** verificar minhas informações cadastradas.

Prioridade:

```text
P1
```

Dependências:

```text
US-001
US-002
```

Critérios:

```text
[ ] O usuário deve visualizar seus dados permitidos.

[ ] Dados internos não devem ser exibidos.
```

---

## US-005 — Atualizar dados da conta

**Como** usuário,
**quero** alterar informações permitidas da minha conta,
**para** mantê-las atualizadas.

Prioridade:

```text
P1
```

Dependências:

```text
US-004
```

Critérios:

```text
[ ] O usuário deve alterar somente campos permitidos.

[ ] Alterações inválidas devem ser rejeitadas.

[ ] O usuário não deve editar a conta de outra pessoa.
```

---

# EP-002 — Perfil Público

Objetivo:

Criar a identidade pública e profissional dos participantes.

---

## US-006 — Visualizar meu perfil

**Como** usuário,
**quero** possuir um perfil,
**para** apresentar minhas informações na plataforma.

Prioridade:

```text
P0
```

Dependências:

```text
US-001
```

Critérios:

```text
[ ] Todo usuário deve possuir perfil associado.

[ ] O perfil deve possuir identificação do usuário.
```

---

## US-007 — Editar perfil

**Como** usuário,
**quero** editar meu perfil,
**para** personalizar minha apresentação.

Prioridade:

```text
P1
```

Dependências:

```text
US-006
```

Critérios:

```text
[ ] Deve ser possível alterar bio.

[ ] Deve ser possível alterar localização.

[ ] Deve ser possível alterar informações públicas permitidas.

[ ] Somente o proprietário deve editar seu perfil.
```

---

## US-008 — Adicionar foto de perfil

**Como** usuário,
**quero** adicionar uma foto,
**para** personalizar meu perfil.

Prioridade:

```text
P2
```

Dependências:

```text
US-006
```

Critérios:

```text
[ ] O perfil deve aceitar referência para imagem.

[ ] A imagem deve aparecer no perfil quando cadastrada.
```

---

## US-009 — Adicionar links profissionais

**Como** usuário,
**quero** adicionar meus links profissionais,
**para** divulgar meu trabalho.

Prioridade:

```text
P1
```

Dependências:

```text
US-006
```

Critérios:

```text
[ ] Deve ser possível informar GitHub.

[ ] Deve ser possível informar LinkedIn.

[ ] Deve ser possível informar portfólio.

[ ] URLs inválidas devem ser rejeitadas.
```

---

## US-010 — Adicionar tecnologias

**Como** usuário,
**quero** informar minhas tecnologias,
**para** demonstrar meus conhecimentos e interesses.

Prioridade:

```text
P2
```

Dependências:

```text
US-006
```

Critérios:

```text
[ ] Deve ser possível associar múltiplas tecnologias.

[ ] A mesma tecnologia não deve ser repetida no perfil.

[ ] Deve ser possível remover uma tecnologia.
```

---

## US-011 — Adicionar áreas de interesse

**Como** usuário,
**quero** informar minhas áreas de interesse,
**para** caracterizar meu perfil profissional.

Prioridade:

```text
P2
```

Dependências:

```text
US-006
```

Critérios:

```text
[ ] Deve ser possível selecionar múltiplas áreas.

[ ] Não deve haver duplicidade.

[ ] Deve ser possível remover uma área.
```

---

## US-012 — Visualizar perfil de outro usuário

**Como** usuário,
**quero** visualizar o perfil público de outras pessoas,
**para** conhecer participantes da comunidade.

Prioridade:

```text
P1
```

Dependências:

```text
US-006
```

Critérios:

```text
[ ] O perfil público deve ser consultável.

[ ] Apenas informações públicas devem aparecer.
```

---

# EP-003 — Recursos Sociais

---

## US-013 — Seguir usuário

**Como** usuário,
**quero** seguir outro participante,
**para** acompanhar pessoas de meu interesse.

Prioridade:

```text
P2
```

Dependências:

```text
US-012
```

Critérios:

```text
[ ] Deve ser possível seguir outro usuário.

[ ] Um usuário não pode seguir a si próprio.

[ ] O mesmo usuário não deve ser seguido duas vezes.
```

---

## US-014 — Deixar de seguir usuário

Prioridade:

```text
P2
```

Dependências:

```text
US-013
```

Critérios:

```text
[ ] Deve ser possível remover a relação de seguimento.
```

---

## US-015 — Consultar seguidores

Prioridade:

```text
P2
```

Dependências:

```text
US-013
```

Critérios:

```text
[ ] Deve ser possível visualizar seguidores.

[ ] Deve ser possível visualizar usuários seguidos.
```

---

# EP-004 — Empresas

---

## US-016 — Cadastrar empresa

**Como** responsável por uma organização,
**quero** cadastrar minha empresa,
**para** utilizar recursos empresariais da plataforma.

Prioridade:

```text
P0
```

Dependências:

```text
US-001
```

Critérios:

```text
[ ] Deve ser possível criar empresa.

[ ] Informações obrigatórias devem ser validadas.

[ ] A empresa deve possuir identificador próprio.
```

---

## US-017 — Criar página pública da empresa

Prioridade:

```text
P1
```

Dependências:

```text
US-016
```

Critérios:

```text
[ ] A empresa deve possuir página própria.

[ ] Nome e descrição devem ser exibidos.

[ ] Eventos relacionados poderão aparecer na página.
```

---

## US-018 — Editar empresa

Prioridade:

```text
P1
```

Dependências:

```text
US-016
```

Critérios:

```text
[ ] Responsável autorizado deve alterar dados.

[ ] Usuário sem vínculo não deve editar a empresa.
```

---

## US-019 — Seguir empresa

Prioridade:

```text
P2
```

Dependências:

```text
US-017
```

Critérios:

```text
[ ] Usuário deve poder seguir empresa.

[ ] Não deve existir seguimento duplicado.

[ ] Deve ser possível deixar de seguir.
```

---

# EP-005 — Verificação de Empresas

---

## US-020 — Solicitar verificação

**Como** empresa,
**quero** solicitar verificação,
**para** poder organizar eventos oficiais.

Prioridade:

```text
P0
```

Dependências:

```text
US-016
```

Critérios:

```text
[ ] Empresa deve conseguir solicitar análise.

[ ] Solicitação deve ficar pendente.

[ ] Solicitação pendente duplicada deve ser impedida.
```

---

## US-021 — Consultar status da verificação

Prioridade:

```text
P1
```

Dependências:

```text
US-020
```

Critérios:

```text
[ ] Empresa deve visualizar o status atual.

[ ] Motivo de rejeição deve ser apresentado quando aplicável.
```

---

## US-022 — Listar verificações pendentes

**Como** administrador,
**quero** visualizar solicitações pendentes,
**para** analisá-las.

Prioridade:

```text
P0
```

Dependências:

```text
US-020
```

Critérios:

```text
[ ] Apenas administrador deve acessar a listagem.

[ ] Solicitações pendentes devem ser identificáveis.
```

---

## US-023 — Aprovar empresa

Prioridade:

```text
P0
```

Dependências:

```text
US-022
```

Critérios:

```text
[ ] Administrador deve conseguir aprovar solicitação.

[ ] Empresa aprovada deve receber status de verificada.

[ ] Selo de verificação deve ficar disponível.
```

---

## US-024 — Rejeitar empresa

Prioridade:

```text
P0
```

Dependências:

```text
US-022
```

Critérios:

```text
[ ] Administrador deve conseguir rejeitar.

[ ] Motivo deve ser registrado.

[ ] Empresa deve conseguir consultar o resultado.
```

---

# EP-006 — Eventos

---

## US-025 — Criar evento

**Como** empresa verificada,
**quero** criar um evento,
**para** divulgá-lo e administrá-lo pela plataforma.

Prioridade:

```text
P0
```

Dependências:

```text
US-023
```

Critérios:

```text
[ ] Empresa verificada deve criar evento.

[ ] Evento deve iniciar como rascunho.

[ ] Nome e período devem ser definidos.

[ ] Modalidade deve ser definida.
```

---

## US-026 — Editar evento em rascunho

Prioridade:

```text
P0
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Organizador deve alterar informações do rascunho.

[ ] Datas inválidas devem ser rejeitadas.
```

---

## US-027 — Definir modalidade do evento

Prioridade:

```text
P0
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Deve aceitar PRESENCIAL.

[ ] Deve aceitar ONLINE.

[ ] Deve aceitar HIBRIDO.
```

---

## US-028 — Definir evento gratuito ou pago

Prioridade:

```text
P1
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Evento pode ser GRATUITO.

[ ] Evento pode ser PAGO.
```

---

## US-029 — Definir capacidade

Prioridade:

```text
P0
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Organizador deve definir limite quando aplicável.

[ ] Capacidade inválida deve ser rejeitada.
```

---

## US-030 — Associar coorganizador

Prioridade:

```text
P1
```

Dependências:

```text
US-025
US-016
```

Critérios:

```text
[ ] Evento pode possuir várias empresas organizadoras.

[ ] Relação duplicada deve ser impedida.
```

---

## US-031 — Enviar evento para aprovação

Prioridade:

```text
P0
```

Dependências:

```text
US-025
US-026
```

Critérios:

```text
[ ] Evento deve mudar para aguardando aprovação.

[ ] Apenas evento válido deve ser enviado.
```

---

## US-032 — Aprovar evento

**Como** administrador,
**quero** aprovar eventos,
**para** permitir sua publicação.

Prioridade:

```text
P0
```

Dependências:

```text
US-031
```

Critérios:

```text
[ ] Administrador deve aprovar evento pendente.

[ ] Evento aprovado deve ficar elegível para publicação.
```

---

## US-033 — Rejeitar evento

Prioridade:

```text
P0
```

Dependências:

```text
US-031
```

Critérios:

```text
[ ] Administrador deve rejeitar evento.

[ ] Motivo deve ser registrado.
```

---

## US-034 — Publicar evento

Prioridade:

```text
P0
```

Dependências:

```text
US-032
```

Critérios:

```text
[ ] Apenas evento aprovado deve ser publicado.

[ ] Evento publicado deve ser consultável pelos usuários.
```

---

## US-035 — Editar evento publicado

Prioridade:

```text
P1
```

Dependências:

```text
US-034
```

Critérios:

```text
[ ] Organizador deve alterar evento publicado.

[ ] Alteração não deve exigir automaticamente nova aprovação.
```

---

## US-036 — Cancelar evento

Prioridade:

```text
P1
```

Dependências:

```text
US-034
```

Critérios:

```text
[ ] Organizador deve cancelar evento.

[ ] Evento deve continuar registrado.

[ ] Estado CANCELADO deve ser visível.
```

---

# EP-007 — Descoberta de Eventos

---

## US-037 — Listar eventos

**Como** usuário,
**quero** visualizar eventos disponíveis,
**para** encontrar oportunidades de interesse.

Prioridade:

```text
P0
```

Dependências:

```text
US-034
```

Critérios:

```text
[ ] Eventos públicos devem ser listados.

[ ] Listagem deve suportar paginação.
```

---

## US-038 — Buscar evento por nome

Prioridade:

```text
P1
```

Dependências:

```text
US-037
```

Critérios:

```text
[ ] Usuário deve pesquisar por texto.

[ ] Resultado deve refletir o termo informado.
```

---

## US-039 — Buscar eventos próximos

Prioridade:

```text
P1
```

Dependências:

```text
US-037
```

Critérios:

```text
[ ] Eventos devem poder ser encontrados por localização.

[ ] Eventos online não devem depender de proximidade física.
```

---

## US-040 — Filtrar eventos

Prioridade:

```text
P1
```

Dependências:

```text
US-037
```

Critérios:

```text
[ ] Filtrar modalidade.

[ ] Filtrar período.

[ ] Filtrar categoria.

[ ] Filtrar gratuito/pago.

[ ] Permitir combinação de filtros.
```

---

# EP-008 — Inscrições em Eventos

---

## US-041 — Inscrever-se em evento

**Como** usuário,
**quero** me inscrever em um evento,
**para** participar dele.

Prioridade:

```text
P0
```

Dependências:

```text
US-001
US-034
```

Critérios:

```text
[ ] Usuário autenticado deve conseguir se inscrever.

[ ] Inscrição duplicada ativa deve ser impedida.

[ ] Evento deve estar aceitando inscrições.
```

---

## US-042 — Consultar minha inscrição

Prioridade:

```text
P1
```

Dependências:

```text
US-041
```

Critérios:

```text
[ ] Usuário deve visualizar status da inscrição.
```

---

## US-043 — Listar participantes

**Como** organizador,
**quero** consultar os inscritos,
**para** acompanhar a participação.

Prioridade:

```text
P1
```

Dependências:

```text
US-041
```

Critérios:

```text
[ ] Organizador deve visualizar inscrições.

[ ] Deve ser possível filtrar por status.
```

---

## US-044 — Configurar aprovação manual

Prioridade:

```text
P1
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Evento deve poder exigir aprovação.

[ ] Nova inscrição deve assumir estado correspondente.
```

---

## US-045 — Aprovar inscrição

Prioridade:

```text
P1
```

Dependências:

```text
US-044
US-041
```

Critérios:

```text
[ ] Organizador deve aprovar solicitação válida.

[ ] Capacidade deve continuar sendo respeitada.
```

---

## US-046 — Rejeitar inscrição

Prioridade:

```text
P1
```

Dependências:

```text
US-044
US-041
```

Critérios:

```text
[ ] Organizador deve rejeitar solicitação.

[ ] Inscrição deve assumir estado REJEITADA.
```

---

## US-047 — Cancelar inscrição

Prioridade:

```text
P1
```

Dependências:

```text
US-041
```

Critérios:

```text
[ ] Participante deve cancelar sua inscrição.

[ ] Inscrição cancelada não deve ocupar vaga ativa.
```

---

## US-048 — Confirmar participação

Prioridade:

```text
P1
```

Dependências:

```text
US-041
```

Critérios:

```text
[ ] Participante deve poder confirmar presença quando solicitado.

[ ] Estado deve refletir a confirmação.
```

---

## US-049 — Controlar limite de vagas

Prioridade:

```text
P0
```

Dependências:

```text
US-029
US-041
```

Critérios:

```text
[ ] Número de confirmados não pode superar capacidade.

[ ] Deve ser possível consultar vagas disponíveis.
```

---

## US-050 — Habilitar lista de espera

Prioridade:

```text
P1
```

Dependências:

```text
US-049
```

Critérios:

```text
[ ] Organizador deve ativar ou não lista de espera.

[ ] Evento lotado com lista ativa deve aceitar interessados na espera.
```

---

## US-051 — Oferecer vaga da lista de espera

Prioridade:

```text
P1
```

Dependências:

```text
US-050
US-047
```

Critérios:

```text
[ ] Vaga liberada pode ser oferecida a usuário da espera.

[ ] Oferta não deve confirmar automaticamente o usuário.
```

---

# EP-009 — Programação e Trilhas

---

## US-052 — Criar trilha

Prioridade:

```text
P1
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Organizador deve criar trilha.

[ ] Trilha deve pertencer ao evento.
```

---

## US-053 — Editar trilha

Prioridade:

```text
P1
```

Dependências:

```text
US-052
```

---

## US-054 — Consultar trilhas

Prioridade:

```text
P1
```

Dependências:

```text
US-052
```

---

## US-055 — Remover trilha

Prioridade:

```text
P2
```

Dependências:

```text
US-052
```

Critérios:

```text
[ ] Remoção não deve deixar relações inválidas.
```

---

# EP-010 — Atividades

---

## US-056 — Criar atividade

**Como** organizador,
**quero** cadastrar atividades,
**para** construir a programação do evento.

Prioridade:

```text
P0
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Atividade deve possuir nome.

[ ] Deve permitir horário.

[ ] Deve permitir local físico ou virtual.

[ ] Pode ou não pertencer a trilha.
```

---

## US-057 — Editar atividade

Prioridade:

```text
P1
```

Dependências:

```text
US-056
```

---

## US-058 — Definir capacidade da atividade

Prioridade:

```text
P1
```

Dependências:

```text
US-056
```

Critérios:

```text
[ ] Atividade pode possuir limite próprio.
```

---

## US-059 — Exigir inscrição em atividade

Prioridade:

```text
P1
```

Dependências:

```text
US-056
```

---

## US-060 — Inscrever-se em atividade

Prioridade:

```text
P1
```

Dependências:

```text
US-041
US-059
```

Critérios:

```text
[ ] Participante deve poder solicitar vaga.

[ ] Capacidade da atividade deve ser respeitada.

[ ] Inscrição duplicada deve ser impedida.
```

---

## US-061 — Cancelar inscrição em atividade

Prioridade:

```text
P2
```

Dependências:

```text
US-060
```

---

## US-062 — Consultar programação

**Como** participante,
**quero** consultar horários e atividades,
**para** acompanhar o evento.

Prioridade:

```text
P0
```

Dependências:

```text
US-056
```

Critérios:

```text
[ ] Programação deve exibir atividades.

[ ] Horários devem ser apresentados.

[ ] Trilhas devem ser identificáveis quando existirem.
```

---

# EP-011 — Check-in

---

## US-063 — Habilitar check-in do evento

Prioridade:

```text
P2
```

Dependências:

```text
US-025
```

---

## US-064 — Registrar check-in no evento

Prioridade:

```text
P2
```

Dependências:

```text
US-041
US-063
```

Critérios:

```text
[ ] Presença deve ser registrada.

[ ] Check-in duplicado deve ser impedido.
```

---

## US-065 — Habilitar check-in de atividade

Prioridade:

```text
P2
```

Dependências:

```text
US-056
```

---

## US-066 — Registrar check-in em atividade

Prioridade:

```text
P2
```

Dependências:

```text
US-060
US-065
```

---

# EP-012 — Hackathons

---

## US-067 — Configurar evento como hackathon

**Como** organizador,
**quero** adicionar configuração de hackathon,
**para** utilizar funcionalidades competitivas.

Prioridade:

```text
P0
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Um evento deve possuir no máximo uma configuração principal de hackathon.

[ ] Tipo de participação deve ser definido.
```

---

## US-068 — Definir participação individual

Prioridade:

```text
P0
```

Dependências:

```text
US-067
```

---

## US-069 — Definir participação em equipe

Prioridade:

```text
P0
```

Dependências:

```text
US-067
```

---

## US-070 — Definir tamanho das equipes

Prioridade:

```text
P0
```

Dependências:

```text
US-069
```

Critérios:

```text
[ ] Deve possuir mínimo quando configurado.

[ ] Deve possuir máximo.

[ ] Mínimo não pode ser maior que máximo.
```

---

# EP-013 — Fases do Hackathon

---

## US-071 — Criar fase

Prioridade:

```text
P0
```

Dependências:

```text
US-067
```

Critérios:

```text
[ ] Organizador deve cadastrar fase.

[ ] Deve permitir nome e período.
```

---

## US-072 — Criar fase personalizada

Prioridade:

```text
P1
```

Dependências:

```text
US-071
```

---

## US-073 — Ordenar fases

Prioridade:

```text
P0
```

Dependências:

```text
US-071
```

Critérios:

```text
[ ] Fases devem possuir sequência clara.
```

---

## US-074 — Visualizar fase atual

Prioridade:

```text
P0
```

Dependências:

```text
US-071
US-073
```

---

## US-075 — Visualizar próximas fases

Prioridade:

```text
P1
```

Dependências:

```text
US-074
```

---

# EP-014 — Desafios

---

## US-076 — Criar desafio

**Como** organizador,
**quero** cadastrar um desafio,
**para** informar o problema que será resolvido.

Prioridade:

```text
P0
```

Dependências:

```text
US-067
```

Critérios:

```text
[ ] Desafio deve possuir título.

[ ] Desafio deve possuir descrição.

[ ] Deve pertencer ao hackathon.
```

---

## US-077 — Editar desafio

Prioridade:

```text
P1
```

Dependências:

```text
US-076
```

---

## US-078 — Consultar desafio

Prioridade:

```text
P0
```

Dependências:

```text
US-076
```

---

## US-079 — Associar patrocinador ao desafio

Prioridade:

```text
P2
```

Dependências:

```text
US-076
US-119
```

---

# EP-015 — Equipes

---

## US-080 — Criar equipe

**Como** participante,
**quero** criar uma equipe,
**para** competir em um hackathon.

Prioridade:

```text
P0
```

Dependências:

```text
US-069
US-041
```

Critérios:

```text
[ ] Hackathon deve permitir equipes.

[ ] Criador deve fazer parte da equipe.

[ ] Equipe deve possuir estado inicial.
```

---

## US-081 — Definir líder da equipe

Prioridade:

```text
P0
```

Dependências:

```text
US-080
```

Critérios:

```text
[ ] Líder deve ser membro da equipe.
```

---

## US-082 — Convidar usuário

Prioridade:

```text
P1
```

Dependências:

```text
US-080
```

---

## US-083 — Aceitar convite

Prioridade:

```text
P1
```

Dependências:

```text
US-082
```

Critérios:

```text
[ ] Convite deve passar para ACEITO.

[ ] Usuário deve ser adicionado à equipe.

[ ] Limite máximo deve ser respeitado.
```

---

## US-084 — Rejeitar convite

Prioridade:

```text
P1
```

Dependências:

```text
US-082
```

---

## US-085 — Solicitar entrada em equipe

Prioridade:

```text
P1
```

Dependências:

```text
US-080
```

---

## US-086 — Aprovar solicitação de entrada

Prioridade:

```text
P1
```

Dependências:

```text
US-085
```

Critérios:

```text
[ ] Usuário deve ser incluído quando aprovado.

[ ] Limite da equipe deve ser respeitado.
```

---

## US-087 — Rejeitar solicitação

Prioridade:

```text
P1
```

Dependências:

```text
US-085
```

---

## US-088 — Montar equipe pelo organizador

Prioridade:

```text
P1
```

Dependências:

```text
US-080
```

---

## US-089 — Validar equipe apta

Prioridade:

```text
P0
```

Dependências:

```text
US-070
US-080
```

Critérios:

```text
[ ] Equipe abaixo do mínimo não deve ser considerada apta.

[ ] Equipe dentro dos limites deve poder se tornar apta.
```

---

## US-090 — Desclassificar equipe

Prioridade:

```text
P1
```

Dependências:

```text
US-080
```

Critérios:

```text
[ ] Organizador deve informar motivo.

[ ] Equipe deve permanecer no histórico.

[ ] Estado deve mudar para DESCLASSIFICADA.
```

---

# EP-016 — Submissões

---

## US-091 — Criar submissão

**Como** participante,
**quero** registrar meu projeto,
**para** entregá-lo ao hackathon.

Prioridade:

```text
P0
```

Dependências:

```text
US-067
US-076
```

Critérios:

```text
[ ] Deve permitir submissão por equipe quando aplicável.

[ ] Deve permitir submissão individual quando aplicável.

[ ] Somente participante elegível deve submeter.
```

---

## US-092 — Enviar versão da submissão

Prioridade:

```text
P0
```

Dependências:

```text
US-091
```

Critérios:

```text
[ ] Deve registrar data e horário.

[ ] Deve preservar versões anteriores.
```

---

## US-093 — Bloquear submissão antes do período

Prioridade:

```text
P0
```

Dependências:

```text
US-071
US-092
```

---

## US-094 — Bloquear submissão após prazo

Prioridade:

```text
P0
```

Dependências:

```text
US-071
US-092
```

---

## US-095 — Consultar histórico de versões

Prioridade:

```text
P1
```

Dependências:

```text
US-092
```

---

## US-096 — Identificar versão oficial

Prioridade:

```text
P0
```

Dependências:

```text
US-092
```

Critérios:

```text
[ ] Uma versão deve ser identificável como oficial.

[ ] Histórico anterior deve permanecer disponível.
```

---

# EP-017 — Avaliação

---

## US-097 — Criar critério de avaliação

Prioridade:

```text
P1
```

Dependências:

```text
US-067
```

---

## US-098 — Definir peso do critério

Prioridade:

```text
P2
```

Dependências:

```text
US-097
```

---

## US-099 — Associar jurado

Prioridade:

```text
P1
```

Dependências:

```text
US-067
US-001
```

---

## US-100 — Registrar avaliação

**Como** jurado,
**quero** registrar uma avaliação,
**para** avaliar uma equipe ou participante.

Prioridade:

```text
P1
```

Dependências:

```text
US-097
US-099
US-091
```

Critérios:

```text
[ ] Apenas jurado autorizado deve avaliar.

[ ] Deve ser possível indicar critério.

[ ] Observação pode ser registrada.
```

---

## US-101 — Permitir múltiplos jurados

Prioridade:

```text
P1
```

Dependências:

```text
US-099
US-100
```

Critérios:

```text
[ ] Avaliações de jurados diferentes devem permanecer independentes.
```

---

# EP-018 — Resultados e Ranking

---

## US-102 — Registrar resultado final

**Como** organizador,
**quero** registrar o resultado oficial,
**para** publicar a classificação.

Prioridade:

```text
P0
```

Dependências:

```text
US-091
```

Critérios:

```text
[ ] Resultado deve poder ser registrado sem exigir cálculo automático.

[ ] Deve permitir posição.

[ ] Pontuação pode ser opcional.
```

---

## US-103 — Criar ranking

Prioridade:

```text
P0
```

Dependências:

```text
US-102
```

---

## US-104 — Manter ranking oculto

Prioridade:

```text
P1
```

Dependências:

```text
US-103
```

---

## US-105 — Publicar ranking

Prioridade:

```text
P0
```

Dependências:

```text
US-103
```

Critérios:

```text
[ ] Ranking deve ficar visível quando publicado.
```

---

## US-106 — Permitir empate

Prioridade:

```text
P1
```

Dependências:

```text
US-102
```

---

## US-107 — Registrar critério de desempate

Prioridade:

```text
P1
```

Dependências:

```text
US-102
```

---

## US-108 — Exibir colocação no perfil

Prioridade:

```text
P1
```

Dependências:

```text
US-102
US-006
```

---

# EP-019 — Emblemas

---

## US-109 — Criar emblema

**Como** organizador,
**quero** criar um emblema exclusivo,
**para** reconhecer conquistas no evento.

Prioridade:

```text
P1
```

Dependências:

```text
US-025
```

Critérios:

```text
[ ] Emblema deve possuir nome.

[ ] Pode possuir descrição.

[ ] Pode possuir imagem.
```

---

## US-110 — Conceder emblema

Prioridade:

```text
P1
```

Dependências:

```text
US-109
US-001
```

Critérios:

```text
[ ] Deve ser possível associar emblema ao usuário.

[ ] Origem do evento deve ser preservada.
```

---

## US-111 — Exibir emblema no perfil

Prioridade:

```text
P1
```

Dependências:

```text
US-110
US-006
```

---

## US-112 — Preservar histórico de emblema

Prioridade:

```text
P1
```

Dependências:

```text
US-110
```

Critérios:

```text
[ ] Emblema deve continuar registrado após encerramento do evento.
```

---

# EP-020 — Certificados

---

## US-113 — Criar tipo de certificado

Prioridade:

```text
P1
```

Dependências:

```text
US-025
```

---

## US-114 — Emitir certificado

Prioridade:

```text
P1
```

Dependências:

```text
US-113
US-001
```

Critérios:

```text
[ ] Certificado deve estar associado ao usuário.

[ ] Evento de origem deve ser identificável.
```

---

## US-115 — Consultar certificados

Prioridade:

```text
P1
```

Dependências:

```text
US-114
```

---

## US-116 — Exibir certificado no perfil

Prioridade:

```text
P1
```

Dependências:

```text
US-114
US-006
```

---

# EP-021 — Histórico do Perfil

---

## US-117 — Exibir eventos participados

Prioridade:

```text
P1
```

Dependências:

```text
US-041
US-006
```

---

## US-118 — Exibir hackathons e resultados

Prioridade:

```text
P1
```

Dependências:

```text
US-067
US-102
US-006
```

Critérios:

```text
[ ] Hackathons participados devem ser exibidos.

[ ] Colocações oficiais devem aparecer quando existentes.
```

---

# EP-022 — Patrocínios

---

## US-119 — Associar patrocinador

**Como** organizador,
**quero** vincular empresas patrocinadoras,
**para** apresentar os apoiadores do evento.

Prioridade:

```text
P2
```

Dependências:

```text
US-016
US-025
```

Critérios:

```text
[ ] Evento pode possuir múltiplos patrocinadores.

[ ] Empresa pode patrocinar múltiplos eventos.
```

---

## US-120 — Exibir patrocinadores

Prioridade:

```text
P2
```

Dependências:

```text
US-119
```

---

## US-121 — Definir categoria de patrocínio

Prioridade:

```text
P3
```

Dependências:

```text
US-119
```

---

# EP-023 — Estandes

---

## US-122 — Criar estande

Prioridade:

```text
P2
```

Dependências:

```text
US-119
```

Critérios:

```text
[ ] Deve estar relacionado ao evento.

[ ] Pode possuir empresa associada.

[ ] Pode ser físico, virtual ou híbrido.
```

---

## US-123 — Consultar estandes

Prioridade:

```text
P2
```

Dependências:

```text
US-122
```

---

# EP-024 — Ofertas

---

## US-124 — Criar oferta

Prioridade:

```text
P3
```

Dependências:

```text
US-119
```

---

## US-125 — Consultar ofertas

Prioridade:

```text
P3
```

Dependências:

```text
US-124
```

---

# EP-025 — Comunicação

---

## US-126 — Criar comunicado geral

**Como** organizador,
**quero** enviar um comunicado,
**para** informar os participantes.

Prioridade:

```text
P1
```

Dependências:

```text
US-025
```

---

## US-127 — Comunicar participantes de atividade

Prioridade:

```text
P2
```

Dependências:

```text
US-060
US-126
```

---

## US-128 — Comunicar participantes do hackathon

Prioridade:

```text
P2
```

Dependências:

```text
US-067
US-126
```

---

## US-129 — Comunicar equipe

Prioridade:

```text
P2
```

Dependências:

```text
US-080
US-126
```

---

## US-130 — Comunicar lista de espera

Prioridade:

```text
P2
```

Dependências:

```text
US-050
US-126
```

---

# EP-026 — Notificações

---

## US-131 — Visualizar central de notificações

Prioridade:

```text
P1
```

Dependências:

```text
US-001
```

Critérios:

```text
[ ] Usuário deve visualizar suas notificações.

[ ] Deve ser possível distinguir lidas e não lidas.
```

---

## US-132 — Marcar notificação como lida

Prioridade:

```text
P1
```

Dependências:

```text
US-131
```

---

## US-133 — Configurar preferências

Prioridade:

```text
P2
```

Dependências:

```text
US-131
```

Critérios:

```text
[ ] Usuário deve habilitar/desabilitar categorias opcionais.

[ ] Notificações essenciais devem respeitar regra própria.
```

---

## US-134 — Notificar alteração do evento

Prioridade:

```text
P1
```

Dependências:

```text
US-035
US-131
```

Inclui:

```text
horário
local
cancelamento
```

---

## US-135 — Notificar convite de equipe

Prioridade:

```text
P1
```

Dependências:

```text
US-082
US-131
```

---

## US-136 — Notificar solicitação de equipe

Prioridade:

```text
P2
```

Dependências:

```text
US-085
US-131
```

---

## US-137 — Notificar vaga da lista de espera

Prioridade:

```text
P1
```

Dependências:

```text
US-051
US-131
```

---

## US-138 — Notificar mudança de fase

Prioridade:

```text
P1
```

Dependências:

```text
US-071
US-131
```

---

## US-139 — Notificar resultado

Prioridade:

```text
P1
```

Dependências:

```text
US-105
US-131
```

---

## US-140 — Notificar emblema

Prioridade:

```text
P2
```

Dependências:

```text
US-110
US-131
```

---

## US-141 — Notificar certificado

Prioridade:

```text
P2
```

Dependências:

```text
US-114
US-131
```

---

## US-142 — Notificar evento de empresa seguida

Prioridade:

```text
P2
```

Dependências:

```text
US-019
US-034
US-131
```

---

# EP-027 — Administração

---

## US-143 — Visualizar painel administrativo

**Como** administrador,
**quero** acessar recursos administrativos,
**para** gerenciar operações da plataforma.

Prioridade:

```text
P0
```

Dependências:

```text
US-002
```

Critérios:

```text
[ ] Somente administrador deve acessar operações administrativas.
```

---

## US-144 — Consultar empresas pendentes

Prioridade:

```text
P0
```

Dependências:

```text
US-143
US-020
```

---

## US-145 — Consultar eventos pendentes

Prioridade:

```text
P0
```

Dependências:

```text
US-143
US-031
```

---

# 4. Tarefas Técnicas Gerais

As tarefas abaixo não representam funcionalidades diretamente percebidas pelo usuário.

---

## TEC-001 — Configurar projeto Next.js

Prioridade:

```text
P0
```

Descrição:

```text
Criar estrutura inicial do projeto Next.js utilizando JavaScript.
```

---

## TEC-002 — Configurar organização de diretórios

Prioridade:

```text
P0
```

Dependências:

```text
TEC-001
```

Estrutura esperada:

```text
app
services
repositories
models
dto
validators
config
utils
```

---

## TEC-003 — Definir banco de dados

Prioridade:

```text
P0
```

Status:

```text
PENDENTE DE DECISÃO
```

---

## TEC-004 — Definir ORM

Prioridade:

```text
P0
```

Dependências:

```text
TEC-003
```

---

## TEC-005 — Configurar conexão com banco

Prioridade:

```text
P0
```

Dependências:

```text
TEC-003
TEC-004
```

---

## TEC-006 — Implementar migrations

Prioridade:

```text
P0
```

Dependências:

```text
TEC-005
```

---

## TEC-007 — Definir estratégia de autenticação

Prioridade:

```text
P0
```

Status:

```text
PENDENTE DE DECISÃO
```

---

## TEC-008 — Implementar autenticação

Prioridade:

```text
P0
```

Dependências:

```text
TEC-007
US-001
```

---

## TEC-009 — Definir padrão de respostas da API

Prioridade:

```text
P0
```

Critérios:

```text
[ ] padrão de sucesso definido

[ ] padrão de erro definido
```

---

## TEC-010 — Implementar tratamento comum de erros

Prioridade:

```text
P0
```

Dependências:

```text
TEC-009
```

---

## TEC-011 — Definir biblioteca de validação

Prioridade:

```text
P0
```

Status:

```text
PENDENTE DE DECISÃO
```

---

## TEC-012 — Implementar paginação padrão

Prioridade:

```text
P1
```

---

## TEC-013 — Criar ambiente Postman

Prioridade:

```text
P0
```

Critérios:

```text
[ ] baseUrl configurada

[ ] variáveis principais configuradas
```

---

## TEC-014 — Criar Collection do Postman

Prioridade:

```text
P0
```

Dependências:

```text
TEC-013
```

---

## TEC-015 — Organizar testes por domínio

Prioridade:

```text
P1
```

Dependências:

```text
TEC-014
```

---

## TEC-016 — Configurar variáveis de ambiente do projeto

Prioridade:

```text
P0
```

Critérios:

```text
[ ] .env utilizado

[ ] .env.example documentado
```

---

## TEC-017 — Definir armazenamento de imagens

Prioridade:

```text
P2
```

Necessário para:

```text
foto de usuário
imagem de empresa
emblemas
```

---

## TEC-018 — Padronizar nomenclatura

Prioridade:

```text
P0
```

Definir padrão para:

```text
arquivos
funções
services
repositories
DTOs
validators
rotas
```

---

## TEC-019 — Revisar dependências do backlog

Prioridade:

```text
P0
```

Executar antes da distribuição definitiva das Sprints.

Validar:

```text
[ ] dependências inexistentes

[ ] ciclos

[ ] dependências invertidas

[ ] histórias bloqueadas
```

---

## TEC-020 — Validar documentação antes da implementação

Prioridade:

```text
P0
```

Documentos:

```text
REQUISITOS.md
REGRAS-DE-NEGOCIO.md
MODELO-DE-DADOS.md
ARQUITETURA.md
API.md
BACKLOG.md
```

---

# 5. Dependências Principais do Projeto

Visão simplificada:

```text
US-001 Cadastro de usuário
│
├── US-002 Login
├── US-006 Perfil
├── US-016 Empresa
└── US-041 Inscrição
```

```text
US-016 Empresa
↓
US-020 Solicitar verificação
↓
US-023 Aprovar empresa
↓
US-025 Criar evento
```

```text
US-025 Criar evento
↓
US-031 Enviar para aprovação
↓
US-032 Aprovar
↓
US-034 Publicar
```

```text
US-034 Evento publicado
│
├── US-037 Descoberta
├── US-041 Inscrição
├── US-052 Trilhas
├── US-056 Atividades
└── US-067 Hackathon
```

```text
US-067 Hackathon
│
├── US-071 Fases
├── US-076 Desafios
├── US-080 Equipes
├── US-091 Submissões
└── US-097 Avaliação
```

```text
US-091 Submissões
↓
US-102 Resultado
↓
US-103 Ranking
↓
US-105 Publicação
↓
US-108 Histórico
```

---

# 6. Ordem Lógica de Implementação

Este bloco não representa Sprints.

Representa apenas dependência lógica.

```text
1. Base técnica

2. Usuários

3. Autenticação

4. Perfis

5. Empresas

6. Verificação de empresas

7. Eventos

8. Aprovação dos eventos

9. Busca

10. Inscrições

11. Programação

12. Atividades

13. Hackathons

14. Fases

15. Desafios

16. Equipes

17. Submissões

18. Avaliações

19. Resultados

20. Ranking

21. Emblemas

22. Certificados

23. Social

24. Patrocinadores

25. Comunicação

26. Notificações
```

A distribuição real será definida em:

```text
SPRINTS.md
```

---

# 7. Funcionalidades Futuras

Não fazem parte do backlog de implementação atual:

```text
Carteira interna

Créditos do evento

Saldo

Compras internas

Transações

Estornos

Sistema privado de pagamento
```

Quando essas funcionalidades entrarem no escopo, deverão receber:

```text
novo épico

novas histórias

novas regras de negócio

novas entidades

novos endpoints

novos testes
```

---

# 8. Resumo do Backlog

O backlog atual possui:

```text
27 Épicos

145 Histórias de Usuário

20 Tarefas Técnicas
```

Total de itens principais:

```text
165
```

---

# 9. Regra de Conclusão de História

Uma história somente poderá ser considerada concluída quando:

```text
[ ] funcionalidade implementada

[ ] critérios de aceitação atendidos

[ ] regras de negócio respeitadas

[ ] endpoint correspondente funcionando quando aplicável

[ ] dados persistidos corretamente

[ ] testes definidos em TESTES-POSTMAN.md executados

[ ] erros bloqueadores corrigidos
```

---

# 10. Definition of Done

Para este projeto acadêmico, uma funcionalidade será considerada pronta quando:

```text
IMPLEMENTADA
+
FUNCIONANDO
+
TESTADA NO POSTMAN
+
COERENTE COM AS REGRAS
+
DOCUMENTADA
```

Não considerar uma história concluída apenas porque:

```text
"o endpoint respondeu 200"
```

A operação deve produzir o comportamento esperado.

---

# 11. Manutenção do Backlog

Quando houver alteração em:

```text
requisito

regra de negócio

entidade

endpoint

escopo
```

deve ser verificado se alguma história precisa ser:

```text
adicionada

alterada

removida

repriorizada

ter dependências alteradas
```

O backlog deve permanecer consistente com os demais documentos do projeto.
