# MODELO DE DADOS

## 1. Objetivo

Este documento apresenta as principais entidades do domínio e seus relacionamentos conceituais.

Neste estágio, o foco é compreender o domínio antes de escolher ORM ou banco definitivo.

## 2. Árvore Geral de Entidades e Relacionamentos

```text
Plataforma
│
├── Usuario
│   ├── Perfil
│   │   ├── Tecnologia
│   │   ├── AreaInteresse
│   │   └── LinkProfissional
│   │
│   ├── PreferenciaNotificacao
│   ├── Notificacao
│   ├── SeguimentoUsuario
│   ├── SeguimentoEmpresa
│   ├── InscricaoEvento
│   ├── InscricaoAtividade
│   ├── CheckInEvento
│   ├── CheckInAtividade
│   ├── MembroEquipe
│   ├── ConviteEquipe
│   ├── SolicitacaoEntradaEquipe
│   ├── Avaliacao
│   ├── EmblemaConcedido
│   └── Certificado
│
├── Empresa
│   ├── VerificacaoEmpresa
│   ├── EventoOrganizador
│   ├── Patrocinio
│   ├── Estande
│   └── Oferta
│
├── Evento
│   ├── EventoOrganizador
│   ├── InscricaoEvento
│   ├── CheckInEvento
│   ├── Trilha
│   │   └── Atividade
│   │
│   ├── Atividade
│   │   ├── InscricaoAtividade
│   │   └── CheckInAtividade
│   │
│   ├── Comunicado
│   ├── Patrocinio
│   ├── Emblema
│   ├── Certificado
│   └── Hackathon
│       ├── FaseHackathon
│       ├── Desafio
│       │   └── Patrocinador opcional
│       │
│       ├── Equipe
│       │   ├── MembroEquipe
│       │   ├── ConviteEquipe
│       │   └── SolicitacaoEntradaEquipe
│       │
│       ├── Submissao
│       │   └── VersaoSubmissao
│       │
│       ├── CriterioAvaliacao
│       ├── Jurado
│       ├── Avaliacao
│       ├── Resultado
│       └── Ranking
│
└── Administrador
    ├── Aprova VerificacaoEmpresa
    └── Aprova Evento
```

## 3. Entidades Principais

### Usuario

Representa a pessoa que utiliza a plataforma.

Relacionamentos principais:

- 1:1 com Perfil;
- 1:N com InscricaoEvento;
- 1:N com InscricaoAtividade;
- N:N com Equipe por MembroEquipe;
- 1:N com EmblemaConcedido;
- 1:N com Certificado.

### Perfil

Representa os dados públicos do usuário.

Pode conter:

- nome público;
- foto;
- bio;
- localização;
- GitHub;
- LinkedIn;
- portfólio.

### Empresa

Representa uma organização cadastrada.

Pode atuar como:

- organizadora;
- coorganizadora;
- patrocinadora.

### VerificacaoEmpresa

Representa o processo de análise da empresa.

Estados sugeridos:

- PENDENTE;
- APROVADA;
- REJEITADA.

### Evento

Representa um evento tecnológico.

Tipos de modalidade:

- PRESENCIAL;
- ONLINE;
- HIBRIDO.

Tipos financeiros:

- GRATUITO;
- PAGO.

Estados sugeridos:

- RASCUNHO;
- AGUARDANDO_APROVACAO;
- APROVADO;
- PUBLICADO;
- INSCRICOES_ABERTAS;
- INSCRICOES_ENCERRADAS;
- EM_ANDAMENTO;
- ENCERRADO;
- REJEITADO;
- CANCELADO.

### EventoOrganizador

Entidade associativa entre Evento e Empresa.

Permite múltiplos organizadores.

### InscricaoEvento

Relaciona Usuario e Evento.

Estados sugeridos:

- SOLICITADA;
- AGUARDANDO_APROVACAO;
- AGUARDANDO_PAGAMENTO;
- INSCRITA;
- LISTA_ESPERA;
- VAGA_OFERECIDA;
- CONFIRMADA;
- CANCELADA;
- REJEITADA.

### Trilha

Agrupa atividades de uma mesma área temática.

### Atividade

Representa palestra, workshop, minicurso, cerimônia, networking ou atividade personalizada.

### InscricaoAtividade

Relaciona Usuario e Atividade.

### CheckInEvento

Registra presença do usuário em um evento.

### CheckInAtividade

Registra presença em uma atividade específica.

### Hackathon

Representa características específicas de um evento do tipo hackathon.

### FaseHackathon

Representa etapas do hackathon.

Exemplos:

- inscrição;
- formação de equipes;
- desenvolvimento;
- submissão;
- avaliação;
- final;
- premiação;
- personalizada.

### Desafio

Representa um problema ou objetivo apresentado no hackathon.

### Equipe

Representa um grupo de participantes.

Estados sugeridos:

- EM_FORMACAO;
- APTA;
- COMPETINDO;
- FINALIZADA;
- DESCLASSIFICADA.

### MembroEquipe

Relaciona Usuario e Equipe.

Pode armazenar:

- papel;
- data de entrada;
- situação.

### ConviteEquipe

Representa convite de entrada em equipe.

### SolicitacaoEntradaEquipe

Representa pedido de um usuário para entrar em equipe.

### Submissao

Representa o projeto submetido ao hackathon.

### VersaoSubmissao

Preserva o histórico de versões enviadas.

### CriterioAvaliacao

Representa critérios utilizados na avaliação.

### Jurado

Representa um avaliador associado ao hackathon.

### Avaliacao

Relaciona jurado, equipe ou participante e critérios.

### Resultado

Representa resultado final oficial.

### Ranking

Representa a classificação exibida pela plataforma.

### Emblema

Representa uma conquista criada pelo evento.

### EmblemaConcedido

Representa a concessão de um emblema a um usuário.

### Certificado

Representa certificado emitido pelo evento.

### Patrocinio

Relaciona Empresa e Evento.

### Estande

Representa a presença física ou virtual de patrocinador em determinado evento.

### Oferta

Representa promoção ou benefício fornecido por patrocinador.

### Comunicado

Representa mensagem enviada pelo organizador.

### Notificacao

Representa notificações individuais exibidas ao usuário.

### PreferenciaNotificacao

Armazena escolhas de categorias de notificações do usuário.

## 4. Cardinalidades Principais

```text
Usuario 1:1 Perfil

Usuario N:N Usuario
por SeguimentoUsuario

Usuario N:N Empresa
por SeguimentoEmpresa

Empresa N:N Evento
por EventoOrganizador

Usuario N:N Evento
por InscricaoEvento

Evento 1:N Trilha

Evento 1:N Atividade

Trilha 1:N Atividade

Usuario N:N Atividade
por InscricaoAtividade

Evento 1:0..1 Hackathon

Hackathon 1:N FaseHackathon

Hackathon 1:N Desafio

Hackathon 1:N Equipe

Usuario N:N Equipe
por MembroEquipe

Equipe 1:N Submissao

Submissao 1:N VersaoSubmissao

Hackathon 1:N CriterioAvaliacao

Hackathon N:N Usuario
por Jurado

Hackathon 1:N Avaliacao

Hackathon 1:N Resultado

Evento 1:N Emblema

Usuario N:N Emblema
por EmblemaConcedido

Evento 1:N Certificado

Empresa N:N Evento
por Patrocinio
```

## 5. Observações

Este modelo ainda poderá ser refinado quando o banco e o ORM forem definidos.

Nem todo item conceitual precisa obrigatoriamente se transformar em tabela isolada.
