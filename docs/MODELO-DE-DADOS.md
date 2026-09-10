# MODELO DE DADOS

## 1. Objetivo do Documento

Este documento descreve o modelo conceitual de dados da plataforma de eventos e hackathons de tecnologia.

O objetivo é identificar:

* entidades;
* atributos principais;
* relacionamentos;
* cardinalidades;
* estados;
* entidades associativas;
* dados históricos;
* dependências entre entidades.

Neste momento, o banco de dados e o ORM ainda não foram definidos.

Portanto, este documento representa o **modelo de domínio dos dados**, e não uma estrutura física definitiva de tabelas.

---

# 2. Visão Geral do Domínio

A plataforma possui três atores principais:

```text
PLATAFORMA
│
├── USUÁRIO
│
├── EMPRESA
│
└── ADMINISTRADOR
```

Os principais núcleos do sistema são:

```text
Usuários
Empresas
Eventos
Inscrições
Programação
Atividades
Hackathons
Equipes
Submissões
Avaliações
Rankings
Conquistas
Patrocínios
Comunicação
Notificações
```

---

# 3. Árvore Geral de Entidades e Relacionamentos

```text
PLATAFORMA
│
├── USUARIO
│   │
│   ├── PERFIL
│   │   ├── PERFIL_TECNOLOGIA
│   │   │   └── TECNOLOGIA
│   │   │
│   │   ├── PERFIL_AREA_INTERESSE
│   │   │   └── AREA_INTERESSE
│   │   │
│   │   └── LINK_PROFISSIONAL
│   │
│   ├── SEGUIMENTO_USUARIO
│   │   ├── usuário seguidor
│   │   └── usuário seguido
│   │
│   ├── SEGUIMENTO_EMPRESA
│   │   ├── usuário
│   │   └── empresa
│   │
│   ├── INSCRICAO_EVENTO
│   │   └── EVENTO
│   │
│   ├── INSCRICAO_ATIVIDADE
│   │   └── ATIVIDADE
│   │
│   ├── CHECKIN_EVENTO
│   │   └── EVENTO
│   │
│   ├── CHECKIN_ATIVIDADE
│   │   └── ATIVIDADE
│   │
│   ├── MEMBRO_EQUIPE
│   │   └── EQUIPE
│   │
│   ├── CONVITE_EQUIPE
│   │   └── EQUIPE
│   │
│   ├── SOLICITACAO_ENTRADA_EQUIPE
│   │   └── EQUIPE
│   │
│   ├── JURADO_HACKATHON
│   │   └── HACKATHON
│   │
│   ├── AVALIACAO
│   │
│   ├── EMBLEMA_CONCEDIDO
│   │   └── EMBLEMA
│   │
│   ├── CERTIFICADO_EMITIDO
│   │   └── CERTIFICADO
│   │
│   ├── PREFERENCIA_NOTIFICACAO
│   │
│   └── NOTIFICACAO
│
├── EMPRESA
│   │
│   ├── VERIFICACAO_EMPRESA
│   │
│   ├── EVENTO_ORGANIZADOR
│   │   └── EVENTO
│   │
│   ├── PATROCINIO
│   │   └── EVENTO
│   │
│   ├── ESTANDE
│   │   └── EVENTO
│   │
│   └── OFERTA
│       └── EVENTO
│
├── EVENTO
│   │
│   ├── EVENTO_ORGANIZADOR
│   │   └── EMPRESA
│   │
│   ├── INSCRICAO_EVENTO
│   │   └── USUARIO
│   │
│   ├── TRILHA
│   │   └── ATIVIDADE
│   │
│   ├── ATIVIDADE
│   │   ├── INSCRICAO_ATIVIDADE
│   │   │   └── USUARIO
│   │   │
│   │   └── CHECKIN_ATIVIDADE
│   │       └── USUARIO
│   │
│   ├── CHECKIN_EVENTO
│   │   └── USUARIO
│   │
│   ├── COMUNICADO
│   │
│   ├── PATROCINIO
│   │   └── EMPRESA
│   │
│   ├── ESTANDE
│   │
│   ├── OFERTA
│   │
│   ├── EMBLEMA
│   │   └── EMBLEMA_CONCEDIDO
│   │
│   ├── CERTIFICADO
│   │   └── CERTIFICADO_EMITIDO
│   │
│   └── HACKATHON
│       │
│       ├── FASE_HACKATHON
│       │
│       ├── DESAFIO
│       │   └── PATROCINADOR opcional
│       │
│       ├── EQUIPE
│       │   ├── MEMBRO_EQUIPE
│       │   ├── CONVITE_EQUIPE
│       │   └── SOLICITACAO_ENTRADA_EQUIPE
│       │
│       ├── SUBMISSAO
│       │   └── VERSAO_SUBMISSAO
│       │
│       ├── CRITERIO_AVALIACAO
│       │
│       ├── JURADO_HACKATHON
│       │
│       ├── AVALIACAO
│       │
│       ├── RESULTADO
│       │
│       └── RANKING
│
└── ADMINISTRADOR
    │
    ├── analisa VERIFICACAO_EMPRESA
    │
    └── analisa EVENTO
```

---

Mapa das Entities

Cada arquivo abaixo representa uma Entity independente do sistema.


src/
└── entities/
    │
    ├── usuario/
    │   ├── Usuario.js
    │   ├── Perfil.js
    │   ├── Tecnologia.js
    │   └── AreaInteresse.js
    │
    ├── empresa/
    │   ├── Empresa.js
    │   └── VerificacaoEmpresa.js
    │
    ├── evento/
    │   ├── Evento.js
    │   ├── EventoOrganizador.js
    │   ├── InscricaoEvento.js
    │   ├── Trilha.js
    │   ├── Atividade.js
    │   ├── InscricaoAtividade.js
    │   ├── CheckInEvento.js
    │   └── CheckInAtividade.js
    │
    ├── hackathon/
    │   ├── Hackathon.js
    │   ├── FaseHackathon.js
    │   ├── Desafio.js
    │   ├── Equipe.js
    │   ├── MembroEquipe.js
    │   ├── ConviteEquipe.js
    │   ├── SolicitacaoEntradaEquipe.js
    │   ├── Submissao.js
    │   ├── VersaoSubmissao.js
    │   ├── CriterioAvaliacao.js
    │   ├── JuradoHackathon.js
    │   ├── Avaliacao.js
    │   └── Resultado.js
    │
    ├── conquista/
    │   ├── Emblema.js
    │   ├── EmblemaConcedido.js
    │   ├── Certificado.js
    │   └── CertificadoEmitido.js
    │
    ├── patrocinio/
    │   ├── Patrocinio.js
    │   ├── Estande.js
    │   └── Oferta.js
    │
    └── comunicacao/
        ├── Comunicado.js
        ├── Notificacao.js
        └── PreferenciaNotificacao.js

        

# 4. Usuário

## 4.1 Entidade USUARIO

Representa uma pessoa com conta na plataforma.

### Atributos conceituais

```text
USUARIO

id
nome
email
senha
status
dataCadastro
dataAtualizacao
```

A forma definitiva de armazenamento de senha será definida posteriormente na arquitetura técnica.

### Relacionamentos

```text
USUARIO 1:1 PERFIL

USUARIO 1:N INSCRICAO_EVENTO

USUARIO 1:N INSCRICAO_ATIVIDADE

USUARIO 1:N CHECKIN_EVENTO

USUARIO 1:N CHECKIN_ATIVIDADE

USUARIO N:N EQUIPE
por MEMBRO_EQUIPE

USUARIO N:N EMBLEMA
por EMBLEMA_CONCEDIDO

USUARIO N:N CERTIFICADO
por CERTIFICADO_EMITIDO
```

---

# 5. Perfil

## 5.1 Entidade PERFIL

Representa as informações públicas do usuário.

```text
PERFIL

id
usuarioId
nomePublico
foto
bio
localizacao
github
linkedin
portfolio
```

### Cardinalidade

```text
USUARIO 1:1 PERFIL
```

Cada perfil pertence a apenas um usuário.

Cada usuário possui no máximo um perfil principal.

---

# 6. Tecnologia

## 6.1 Entidade TECNOLOGIA

Representa uma tecnologia que pode ser associada ao perfil.

```text
TECNOLOGIA

id
nome
```

Exemplos:

```text
JavaScript
Java
Python
React
Node.js
Next.js
Docker
AWS
```

---

# 7. Perfil e Tecnologia

## 7.1 Entidade PERFIL_TECNOLOGIA

Entidade associativa entre perfil e tecnologia.

```text
PERFIL_TECNOLOGIA

id
perfilId
tecnologiaId
```

### Cardinalidade

```text
PERFIL N:N TECNOLOGIA
```

Um perfil pode possuir várias tecnologias.

Uma tecnologia pode aparecer em vários perfis.

---

# 8. Área de Interesse

## 8.1 Entidade AREA_INTERESSE

Representa uma área tecnológica ou profissional.

```text
AREA_INTERESSE

id
nome
```

Exemplos:

```text
Backend
Frontend
Mobile
Inteligência Artificial
Segurança
Dados
DevOps
Games
```

---

# 9. Perfil e Área de Interesse

## 9.1 Entidade PERFIL_AREA_INTERESSE

```text
PERFIL_AREA_INTERESSE

id
perfilId
areaInteresseId
```

### Cardinalidade

```text
PERFIL N:N AREA_INTERESSE
```

---

# 10. Link Profissional

## 10.1 Entidade LINK_PROFISSIONAL

Representa links adicionais adicionados pelo usuário.

```text
LINK_PROFISSIONAL

id
perfilId
tipo
titulo
url
```

### Cardinalidade

```text
PERFIL 1:N LINK_PROFISSIONAL
```

---

# 11. Seguimento entre Usuários

## 11.1 Entidade SEGUIMENTO_USUARIO

Representa a relação em que um usuário segue outro.

```text
SEGUIMENTO_USUARIO

id
seguidorId
seguidoId
dataSeguimento
```

### Cardinalidade

Conceitualmente:

```text
USUARIO N:N USUARIO
```

Exemplo:

```text
Leonardo
   ↓ segue
Carlos
```

A entidade precisa armazenar dois papéis diferentes:

```text
seguidor
seguido
```

---

# 12. Seguimento de Empresa

## 12.1 Entidade SEGUIMENTO_EMPRESA

```text
SEGUIMENTO_EMPRESA

id
usuarioId
empresaId
dataSeguimento
```

### Cardinalidade

```text
USUARIO N:N EMPRESA
```

---

# 13. Empresa

## 13.1 Entidade EMPRESA

Representa uma organização cadastrada.

```text
EMPRESA

id
nome
nomeFantasia
descricao
imagem
site
localizacao
status
dataCadastro
dataAtualizacao
```

A empresa pode atuar como:

```text
ORGANIZADORA
COORGANIZADORA
PATROCINADORA
```

Esses papéis são definidos pelos relacionamentos, não necessariamente por um campo fixo na empresa.

---

# 14. Verificação de Empresa

## 14.1 Entidade VERIFICACAO_EMPRESA

Representa o processo de verificação de uma empresa.

```text
VERIFICACAO_EMPRESA

id
empresaId
status
dataSolicitacao
dataAnalise
motivoRejeicao
administradorResponsavelId
```

### Estados

```text
PENDENTE
APROVADA
REJEITADA
```

### Cardinalidade

```text
EMPRESA 1:N VERIFICACAO_EMPRESA
```

Essa modelagem permite preservar histórico caso uma empresa passe por mais de uma análise ao longo do tempo.

---

# 15. Administrador

## 15.1 Conceito ADMINISTRADOR

Administrador representa uma conta autorizada a executar operações administrativas.

Conceitualmente:

```text
USUARIO
   ↓
possui papel
   ↓
ADMINISTRADOR
```

Não é obrigatório criar uma tabela independente `ADMINISTRADOR`.

Isso será decidido quando o modelo de autenticação e autorização for definido.

Responsabilidades relacionadas ao domínio:

```text
analisar empresa
aprovar empresa
rejeitar empresa

analisar evento
aprovar evento
rejeitar evento
```

---

# 16. Evento

## 16.1 Entidade EVENTO

Representa um evento da plataforma.

```text
EVENTO

id
nome
descricao
modalidade
tipoFinanceiro
dataInicio
dataFim
capacidade
status
localizacao
urlOnline
dataCriacao
dataAtualizacao
```

---

## 16.2 Modalidade

Valores previstos:

```text
PRESENCIAL
ONLINE
HIBRIDO
```

---

## 16.3 Tipo Financeiro

```text
GRATUITO
PAGO
```

---

## 16.4 Estados do Evento

```text
RASCUNHO
        ↓
AGUARDANDO_APROVACAO
        ↓
APROVADO
        ↓
PUBLICADO
        ↓
INSCRICOES_ABERTAS
        ↓
INSCRICOES_ENCERRADAS
        ↓
EM_ANDAMENTO
        ↓
ENCERRADO
```

Estados alternativos:

```text
REJEITADO
CANCELADO
```

---

# 17. Evento e Empresa Organizadora

## 17.1 Entidade EVENTO_ORGANIZADOR

Representa o relacionamento entre uma empresa e um evento organizado por ela.

```text
EVENTO_ORGANIZADOR

id
eventoId
empresaId
papel
dataAssociacao
```

Possíveis papéis:

```text
ORGANIZADOR_PRINCIPAL
COORGANIZADOR
```

### Cardinalidade

```text
EMPRESA N:N EVENTO
```

Porque:

* uma empresa pode organizar vários eventos;
* um evento pode possuir várias empresas organizadoras.

---

# 18. Inscrição em Evento

## 18.1 Entidade INSCRICAO_EVENTO

Representa a participação de um usuário em um evento.

```text
INSCRICAO_EVENTO

id
usuarioId
eventoId
status
dataInscricao
dataConfirmacao
dataCancelamento
```

### Cardinalidade

```text
USUARIO N:N EVENTO
```

Implementada conceitualmente por:

```text
INSCRICAO_EVENTO
```

---

## 18.2 Estados da Inscrição

```text
SOLICITADA
AGUARDANDO_APROVACAO
AGUARDANDO_PAGAMENTO
INSCRITA
LISTA_ESPERA
VAGA_OFERECIDA
CONFIRMADA
REJEITADA
CANCELADA
```

---

# 19. Lista de Espera

Neste modelo, **não será criada inicialmente uma entidade separada chamada LISTA_ESPERA**.

A lista poderá ser representada por inscrições cujo estado seja:

```text
LISTA_ESPERA
```

Isso evita criar uma entidade desnecessária.

Informações adicionais, como ordem na espera, podem ser armazenadas posteriormente na própria inscrição, caso necessário.

Exemplo:

```text
INSCRICAO_EVENTO
status = LISTA_ESPERA
posicaoEspera = 4
```

---

# 20. Trilha

## 20.1 Entidade TRILHA

Representa uma divisão temática da programação.

```text
TRILHA

id
eventoId
nome
descricao
```

### Cardinalidade

```text
EVENTO 1:N TRILHA
```

---

# 21. Atividade

## 21.1 Entidade ATIVIDADE

Representa uma atividade dentro da programação.

```text
ATIVIDADE

id
eventoId
trilhaId
nome
descricao
tipo
dataInicio
dataFim
local
urlOnline
capacidade
exigeInscricao
exigeCheckIn
```

### Tipos possíveis

```text
PALESTRA
WORKSHOP
MINICURSO
APRESENTACAO
NETWORKING
CERIMONIA
COMPETICAO
PERSONALIZADA
```

### Cardinalidades

```text
EVENTO 1:N ATIVIDADE

TRILHA 1:N ATIVIDADE
```

Porém:

```text
ATIVIDADE.trilhaId
```

pode ser opcional.

---

# 22. Inscrição em Atividade

## 22.1 Entidade INSCRICAO_ATIVIDADE

```text
INSCRICAO_ATIVIDADE

id
usuarioId
atividadeId
status
dataInscricao
dataCancelamento
```

### Cardinalidade

```text
USUARIO N:N ATIVIDADE
```

---

# 23. Check-in de Evento

## 23.1 Entidade CHECKIN_EVENTO

```text
CHECKIN_EVENTO

id
usuarioId
eventoId
dataHora
```

### Cardinalidade

```text
USUARIO N:N EVENTO
```

dentro do contexto de presença.

---

# 24. Check-in de Atividade

## 24.1 Entidade CHECKIN_ATIVIDADE

```text
CHECKIN_ATIVIDADE

id
usuarioId
atividadeId
dataHora
```

### Cardinalidade

```text
USUARIO N:N ATIVIDADE
```

dentro do contexto de presença.

---

# 25. Hackathon

## 25.1 Entidade HACKATHON

Representa as configurações específicas de um evento que funciona como hackathon.

```text
HACKATHON

id
eventoId
tipoParticipacao
minimoIntegrantes
maximoIntegrantes
descricaoRegras
```

### Cardinalidade

```text
EVENTO 1:0..1 HACKATHON
```

Nem todo evento é um hackathon.

Todo hackathon pertence a um evento.

---

## 25.2 Tipo de Participação

```text
INDIVIDUAL
EQUIPE
AMBOS
```

---

# 26. Fase do Hackathon

## 26.1 Entidade FASE_HACKATHON

```text
FASE_HACKATHON

id
hackathonId
nome
descricao
tipo
ordem
dataInicio
dataFim
status
```

### Tipos

```text
INSCRICAO
FORMACAO_EQUIPE
DESENVOLVIMENTO
SUBMISSAO
AVALIACAO
FINAL
PREMIACAO
PERSONALIZADA
```

### Cardinalidade

```text
HACKATHON 1:N FASE_HACKATHON
```

---

# 27. Desafio

## 27.1 Entidade DESAFIO

```text
DESAFIO

id
hackathonId
patrocinadorId
titulo
descricao
dataCriacao
```

`patrocinadorId` pode ser opcional.

### Cardinalidade

```text
HACKATHON 1:N DESAFIO
```

e opcionalmente:

```text
EMPRESA 1:N DESAFIO
```

quando a empresa for patrocinadora do desafio.

---

# 28. Equipe

## 28.1 Entidade EQUIPE

```text
EQUIPE

id
hackathonId
nome
liderId
status
dataCriacao
motivoDesclassificacao
dataDesclassificacao
```

### Estados

```text
EM_FORMACAO
APTA
COMPETINDO
FINALIZADA
DESCLASSIFICADA
```

### Cardinalidade

```text
HACKATHON 1:N EQUIPE
```

---

# 29. Membro da Equipe

## 29.1 Entidade MEMBRO_EQUIPE

Representa a relação entre usuários e equipes.

```text
MEMBRO_EQUIPE

id
equipeId
usuarioId
papel
dataEntrada
status
```

### Possíveis papéis

```text
LIDER
MEMBRO
```

### Cardinalidade

```text
USUARIO N:N EQUIPE
```

---

# 30. Convite de Equipe

## 30.1 Entidade CONVITE_EQUIPE

```text
CONVITE_EQUIPE

id
equipeId
usuarioConvidadoId
usuarioResponsavelId
status
dataConvite
dataResposta
```

### Estados

```text
PENDENTE
ACEITO
REJEITADO
CANCELADO
EXPIRADO
```

### Cardinalidade

```text
EQUIPE 1:N CONVITE_EQUIPE
```

---

# 31. Solicitação de Entrada em Equipe

## 31.1 Entidade SOLICITACAO_ENTRADA_EQUIPE

```text
SOLICITACAO_ENTRADA_EQUIPE

id
equipeId
usuarioId
status
dataSolicitacao
dataResposta
```

### Estados

```text
PENDENTE
APROVADA
REJEITADA
CANCELADA
```

---

# 32. Submissão

## 32.1 Entidade SUBMISSAO

Representa o projeto entregue por participante ou equipe.

```text
SUBMISSAO

id
hackathonId
equipeId
usuarioId
titulo
descricao
dataCriacao
```

A submissão poderá pertencer:

```text
a uma EQUIPE
```

ou, quando o hackathon for individual:

```text
a um USUARIO
```

Esses dois vínculos não devem ser obrigatórios simultaneamente.

---

# 33. Versão da Submissão

## 33.1 Entidade VERSAO_SUBMISSAO

```text
VERSAO_SUBMISSAO

id
submissaoId
numeroVersao
conteudo
urlProjeto
urlRepositorio
dataHoraEnvio
oficial
```

### Cardinalidade

```text
SUBMISSAO 1:N VERSAO_SUBMISSAO
```

Exemplo:

```text
Submissão Atlas
│
├── Versão 1
├── Versão 2
├── Versão 3
└── Versão 4 ← oficial
```

---

# 34. Critério de Avaliação

## 34.1 Entidade CRITERIO_AVALIACAO

```text
CRITERIO_AVALIACAO

id
hackathonId
nome
descricao
peso
```

### Cardinalidade

```text
HACKATHON 1:N CRITERIO_AVALIACAO
```

O campo `peso` pode ser opcional.

---

# 35. Jurado do Hackathon

## 35.1 Entidade JURADO_HACKATHON

Representa a associação de um usuário ao papel de jurado em um hackathon específico.

```text
JURADO_HACKATHON

id
hackathonId
usuarioId
dataAssociacao
```

### Cardinalidade

```text
USUARIO N:N HACKATHON
```

por:

```text
JURADO_HACKATHON
```

---

# 36. Avaliação

## 36.1 Entidade AVALIACAO

Representa uma avaliação realizada por um jurado.

```text
AVALIACAO

id
hackathonId
juradoId
equipeId
usuarioParticipanteId
criterioId
nota
observacao
dataAvaliacao
```

Dependendo do tipo de hackathon, a avaliação pode ser dirigida a:

```text
EQUIPE
```

ou:

```text
PARTICIPANTE INDIVIDUAL
```

### Cardinalidades

```text
JURADO_HACKATHON 1:N AVALIACAO

CRITERIO_AVALIACAO 1:N AVALIACAO

EQUIPE 1:N AVALIACAO
```

ou, em competição individual:

```text
USUARIO 1:N AVALIACAO
```

---

# 37. Resultado

## 37.1 Entidade RESULTADO

Representa o resultado oficial informado pelo organizador.

```text
RESULTADO

id
hackathonId
equipeId
usuarioId
pontuacaoFinal
posicao
observacao
dataPublicacao
```

A pontuação final pode ser opcional, pois nem todo evento precisa trabalhar com uma fórmula numérica.

---

# 38. Ranking

## 38.1 Entidade RANKING

Representa a configuração e publicação da classificação.

```text
RANKING

id
hackathonId
visibilidade
dataPublicacao
```

### Visibilidade

```text
OCULTO
PUBLICADO
```

A classificação propriamente dita pode ser derivada dos registros de `RESULTADO`.

Portanto, não é obrigatório duplicar todas as posições dentro de `RANKING`.

Conceitualmente:

```text
RANKING
   ↓
RESULTADOS ordenados
```

---

# 39. Emblema

## 39.1 Entidade EMBLEMA

```text
EMBLEMA

id
eventoId
nome
descricao
imagem
```

### Cardinalidade

```text
EVENTO 1:N EMBLEMA
```

---

# 40. Emblema Concedido

## 40.1 Entidade EMBLEMA_CONCEDIDO

Representa o fato histórico de que um usuário recebeu determinado emblema.

```text
EMBLEMA_CONCEDIDO

id
emblemaId
usuarioId
eventoId
dataConcessao
nomeHistorico
descricaoHistorica
imagemHistorica
```

Os campos históricos podem preservar a aparência e descrição existentes no momento da concessão.

### Cardinalidade

```text
USUARIO N:N EMBLEMA
```

---

# 41. Certificado

## 41.1 Entidade CERTIFICADO

Representa um modelo ou tipo de certificado disponível em um evento.

```text
CERTIFICADO

id
eventoId
nome
descricao
tipo
```

Exemplos:

```text
PARTICIPACAO
PALESTRANTE
WORKSHOP
FINALISTA
CAMPEAO
PERSONALIZADO
```

---

# 42. Certificado Emitido

## 42.1 Entidade CERTIFICADO_EMITIDO

Representa o certificado efetivamente concedido.

```text
CERTIFICADO_EMITIDO

id
certificadoId
usuarioId
eventoId
dataEmissao
codigoIdentificacao
```

### Cardinalidade

```text
USUARIO N:N CERTIFICADO
```

---

# 43. Patrocínio

## 43.1 Entidade PATROCINIO

Representa a associação de uma empresa patrocinadora a um evento.

```text
PATROCINIO

id
eventoId
empresaId
categoria
dataAssociacao
```

### Cardinalidade

```text
EMPRESA N:N EVENTO
```

por:

```text
PATROCINIO
```

---

# 44. Estande

## 44.1 Entidade ESTANDE

```text
ESTANDE

id
eventoId
empresaId
nome
descricao
tipo
localizacao
urlVirtual
```

### Tipo

```text
FISICO
VIRTUAL
HIBRIDO
```

### Cardinalidade

```text
EVENTO 1:N ESTANDE

EMPRESA 1:N ESTANDE
```

---

# 45. Oferta

## 45.1 Entidade OFERTA

```text
OFERTA

id
eventoId
empresaId
titulo
descricao
dataInicio
dataFim
status
```

### Cardinalidade

```text
EVENTO 1:N OFERTA

EMPRESA 1:N OFERTA
```

---

# 46. Comunicado

## 46.1 Entidade COMUNICADO

```text
COMUNICADO

id
eventoId
titulo
mensagem
tipoPublico
dataCriacao
```

Possíveis públicos:

```text
TODOS
HACKATHON
ATIVIDADE
EQUIPE
LISTA_ESPERA
```

Dependendo do público, podem existir referências adicionais ao grupo destinatário.

---

# 47. Preferência de Notificação

## 47.1 Entidade PREFERENCIA_NOTIFICACAO

```text
PREFERENCIA_NOTIFICACAO

id
usuarioId
categoria
habilitada
```

### Categorias

```text
ESSENCIAL
OPERACIONAL
SOCIAL
PROMOCIONAL
```

---

# 48. Notificação

## 48.1 Entidade NOTIFICACAO

```text
NOTIFICACAO

id
usuarioId
categoria
titulo
mensagem
lida
dataCriacao
```

Pode possuir referência opcional ao recurso que originou a notificação.

Exemplos:

```text
evento
atividade
equipe
hackathon
certificado
emblema
```

### Cardinalidade

```text
USUARIO 1:N NOTIFICACAO
```

---

# 49. Mapa Resumido de Cardinalidades

```text
USUARIO 1:1 PERFIL

PERFIL N:N TECNOLOGIA
por PERFIL_TECNOLOGIA

PERFIL N:N AREA_INTERESSE
por PERFIL_AREA_INTERESSE

PERFIL 1:N LINK_PROFISSIONAL


USUARIO N:N USUARIO
por SEGUIMENTO_USUARIO

USUARIO N:N EMPRESA
por SEGUIMENTO_EMPRESA


EMPRESA 1:N VERIFICACAO_EMPRESA

EMPRESA N:N EVENTO
por EVENTO_ORGANIZADOR

EMPRESA N:N EVENTO
por PATROCINIO


USUARIO N:N EVENTO
por INSCRICAO_EVENTO

EVENTO 1:N TRILHA

EVENTO 1:N ATIVIDADE

TRILHA 1:N ATIVIDADE

USUARIO N:N ATIVIDADE
por INSCRICAO_ATIVIDADE


USUARIO N:N EVENTO
por CHECKIN_EVENTO

USUARIO N:N ATIVIDADE
por CHECKIN_ATIVIDADE


EVENTO 1:0..1 HACKATHON

HACKATHON 1:N FASE_HACKATHON

HACKATHON 1:N DESAFIO

HACKATHON 1:N EQUIPE


USUARIO N:N EQUIPE
por MEMBRO_EQUIPE

EQUIPE 1:N CONVITE_EQUIPE

EQUIPE 1:N SOLICITACAO_ENTRADA_EQUIPE


HACKATHON 1:N SUBMISSAO

SUBMISSAO 1:N VERSAO_SUBMISSAO


HACKATHON 1:N CRITERIO_AVALIACAO

USUARIO N:N HACKATHON
por JURADO_HACKATHON

JURADO_HACKATHON 1:N AVALIACAO

CRITERIO_AVALIACAO 1:N AVALIACAO


HACKATHON 1:N RESULTADO

HACKATHON 1:0..1 RANKING


EVENTO 1:N EMBLEMA

USUARIO N:N EMBLEMA
por EMBLEMA_CONCEDIDO


EVENTO 1:N CERTIFICADO

USUARIO N:N CERTIFICADO
por CERTIFICADO_EMITIDO


EVENTO 1:N COMUNICADO

USUARIO 1:N NOTIFICACAO

USUARIO 1:N PREFERENCIA_NOTIFICACAO
```

---

# 50. Entidades Associativas

As seguintes entidades existem principalmente para representar relacionamentos entre outras entidades:

```text
PERFIL_TECNOLOGIA

PERFIL_AREA_INTERESSE

SEGUIMENTO_USUARIO

SEGUIMENTO_EMPRESA

EVENTO_ORGANIZADOR

INSCRICAO_EVENTO

INSCRICAO_ATIVIDADE

CHECKIN_EVENTO

CHECKIN_ATIVIDADE

MEMBRO_EQUIPE

JURADO_HACKATHON

EMBLEMA_CONCEDIDO

CERTIFICADO_EMITIDO

PATROCINIO
```

Essas entidades podem possuir informações próprias além das chaves dos relacionamentos.

---

# 51. Entidades com Histórico Importante

As seguintes entidades devem receber atenção especial para preservação histórica:

```text
VERIFICACAO_EMPRESA

EVENTO

INSCRICAO_EVENTO

MEMBRO_EQUIPE

VERSAO_SUBMISSAO

AVALIACAO

RESULTADO

EMBLEMA_CONCEDIDO

CERTIFICADO_EMITIDO
```

Esses registros representam fatos relevantes do sistema e não devem ser eliminados indiscriminadamente.

---

# 52. Entidades com Estados

## Verificação de Empresa

```text
PENDENTE
APROVADA
REJEITADA
```

## Evento

```text
RASCUNHO
AGUARDANDO_APROVACAO
APROVADO
PUBLICADO
INSCRICOES_ABERTAS
INSCRICOES_ENCERRADAS
EM_ANDAMENTO
ENCERRADO
REJEITADO
CANCELADO
```

## Inscrição no Evento

```text
SOLICITADA
AGUARDANDO_APROVACAO
AGUARDANDO_PAGAMENTO
INSCRITA
LISTA_ESPERA
VAGA_OFERECIDA
CONFIRMADA
REJEITADA
CANCELADA
```

## Equipe

```text
EM_FORMACAO
APTA
COMPETINDO
FINALIZADA
DESCLASSIFICADA
```

## Convite para Equipe

```text
PENDENTE
ACEITO
REJEITADO
CANCELADO
EXPIRADO
```

## Solicitação para Equipe

```text
PENDENTE
APROVADA
REJEITADA
CANCELADA
```

## Ranking

```text
OCULTO
PUBLICADO
```

---

# 53. Relações que Merecem Atenção

## 53.1 Empresa organizadora e empresa patrocinadora

São relações diferentes:

```text
EMPRESA
   │
   ├── EVENTO_ORGANIZADOR
   │
   └── PATROCINIO
```

Uma empresa pode exercer ambos os papéis, mas eles não devem ser confundidos.

---

## 53.2 Usuário e Perfil

```text
USUARIO
≠
PERFIL
```

`USUARIO` representa principalmente a conta e identidade interna.

`PERFIL` representa a apresentação pública.

---

## 53.3 Evento e Hackathon

```text
EVENTO
   │
   └── HACKATHON
```

Nem todo evento é um hackathon.

Hackathon adiciona funcionalidades específicas a determinado evento.

---

## 53.4 Inscrição e Check-in

```text
INSCRICAO
≠
CHECK-IN
```

Inscrição representa intenção ou autorização para participar.

Check-in representa presença.

---

## 53.5 Emblema e Emblema Concedido

```text
EMBLEMA
≠
EMBLEMA_CONCEDIDO
```

`EMBLEMA` representa a conquista criada pelo evento.

`EMBLEMA_CONCEDIDO` representa o fato de determinado usuário ter recebido aquela conquista.

---

## 53.6 Certificado e Certificado Emitido

```text
CERTIFICADO
≠
CERTIFICADO_EMITIDO
```

Um representa o modelo.

O outro representa uma emissão concreta para determinado usuário.

---

## 53.7 Submissão e Versão

```text
SUBMISSAO
   │
   ├── VERSAO 1
   ├── VERSAO 2
   └── VERSAO 3
```

Uma nova versão não substitui conceitualmente o histórico das anteriores.

---

# 54. Estrutura Conceitual Simplificada

```text
USUARIO
│
├── PERFIL
├── INSCRICOES
├── EQUIPES
├── CONQUISTAS
├── CERTIFICADOS
└── NOTIFICACOES


EMPRESA
│
├── VERIFICACAO
├── EVENTOS ORGANIZADOS
└── PATROCINIOS


EVENTO
│
├── ORGANIZADORES
├── INSCRICOES
├── PROGRAMACAO
│   ├── TRILHAS
│   └── ATIVIDADES
│
├── CHECK-INS
├── PATROCINADORES
├── COMUNICADOS
├── EMBLEMAS
├── CERTIFICADOS
│
└── HACKATHON
    │
    ├── FASES
    ├── DESAFIOS
    ├── EQUIPES
    ├── SUBMISSOES
    ├── AVALIACOES
    ├── RESULTADOS
    └── RANKING
```

---

# 55. Entidades Identificadas

A modelagem conceitual atual possui as seguintes entidades principais e associativas:

```text
1. Usuario
2. Perfil
3. Tecnologia
4. PerfilTecnologia
5. AreaInteresse
6. PerfilAreaInteresse
7. LinkProfissional
8. SeguimentoUsuario
9. SeguimentoEmpresa

10. Empresa
11. VerificacaoEmpresa

12. Evento
13. EventoOrganizador
14. InscricaoEvento
15. Trilha
16. Atividade
17. InscricaoAtividade
18. CheckInEvento
19. CheckInAtividade

20. Hackathon
21. FaseHackathon
22. Desafio
23. Equipe
24. MembroEquipe
25. ConviteEquipe
26. SolicitacaoEntradaEquipe

27. Submissao
28. VersaoSubmissao

29. CriterioAvaliacao
30. JuradoHackathon
31. Avaliacao
32. Resultado
33. Ranking

34. Emblema
35. EmblemaConcedido

36. Certificado
37. CertificadoEmitido

38. Patrocinio
39. Estande
40. Oferta

41. Comunicado
42. PreferenciaNotificacao
43. Notificacao
```

O conceito administrativo poderá inicialmente ser representado por papel ou perfil de acesso associado ao usuário, sem obrigatoriedade de uma entidade física independente.

---

# 56. Decisões Ainda Pendentes

Algumas decisões devem permanecer abertas até a definição da tecnologia de persistência.

Ainda não está definido:

```text
Banco de dados
ORM
Tipos físicos das colunas
Estratégia de IDs
Índices
Constraints físicas
Migrations
Estratégia de exclusão lógica
Estratégia de auditoria
```

Essas decisões não devem ser inventadas antes da escolha técnica correspondente.

---

# 57. Funcionalidades Futuras Não Modeladas

Os seguintes módulos ainda não fazem parte do modelo principal:

```text
Carteira interna
Saldo
Crédito do evento
Transação interna
Compra
Produto
Estorno
Meio de pagamento
```

Quando o sistema interno de pagamentos entrar no escopo, essas entidades deverão ser modeladas separadamente.

---

# 58. Regra de Evolução do Modelo

Sempre que uma nova funcionalidade introduzir:

```text
novo conceito de negócio
novo relacionamento
novo estado
nova informação histórica
nova restrição
```

este documento deve ser revisado.

A criação de uma nova entidade deve possuir uma justificativa de domínio.

Não devem ser criadas entidades apenas para reproduzir padrões arquiteturais ou aumentar artificialmente a complexidade do sistema.
