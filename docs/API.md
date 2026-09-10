# API

## 1. Objetivo do Documento

Este documento define os endpoints da plataforma de eventos e hackathons de tecnologia.

Para cada endpoint são apresentados:

* método HTTP;
* rota;
* finalidade;
* parâmetros;
* body esperado;
* resposta esperada;
* principais códigos HTTP.

Este documento não define:

* implementação interna;
* Services;
* Repositories;
* regras de negócio;
* testes Postman;
* estrutura de banco.

---

# 2. Padrão Geral da API

## 2.1 Base das Rotas

Todas as rotas da API devem utilizar o prefixo:

```text
/api
```

Exemplo:

```text
/api/usuarios
```

---

## 2.2 Formato de Dados

O formato padrão de entrada e saída será:

```text
JSON
```

---

## 2.3 Resposta de Sucesso

Exemplo:

```json
{
  "sucesso": true,
  "dados": {}
}
```

---

## 2.4 Resposta de Erro

Exemplo:

```json
{
  "sucesso": false,
  "erro": {
    "codigo": "RECURSO_NAO_ENCONTRADO",
    "mensagem": "Recurso não encontrado."
  }
}
```

---

# 3. Status HTTP Utilizados

```text
200 OK
Operação concluída com sucesso.

201 Created
Recurso criado com sucesso.

204 No Content
Operação concluída sem conteúdo de resposta.

400 Bad Request
Dados enviados são inválidos.

401 Unauthorized
Usuário não autenticado.

403 Forbidden
Usuário autenticado sem permissão.

404 Not Found
Recurso não encontrado.

409 Conflict
Conflito de estado ou duplicidade.

422 Unprocessable Entity
Dados válidos estruturalmente, mas incompatíveis com a operação.

500 Internal Server Error
Erro interno inesperado.
```

---

# 4. Autenticação

## 4.1 Login

### Endpoint

```http
POST /api/auth/login
```

### Finalidade

Autenticar um usuário.

### Body

```json
{
  "email": "usuario@email.com",
  "senha": "Senha123"
}
```

### Resposta

```json
{
  "sucesso": true,
  "dados": {
    "usuario": {
      "id": 1,
      "nome": "Leonardo",
      "email": "usuario@email.com"
    }
  }
}
```

### Status

```text
200 OK
400 Bad Request
401 Unauthorized
```

---

## 4.2 Logout

```http
POST /api/auth/logout
```

### Finalidade

Encerrar a sessão do usuário autenticado.

### Status

```text
204 No Content
401 Unauthorized
```

---

# 5. Usuários

## 5.1 Cadastrar Usuário

```http
POST /api/usuarios
```

### Body

```json
{
  "nome": "Leonardo",
  "email": "leonardo@email.com",
  "senha": "Senha123"
}
```

### Resposta

```json
{
  "sucesso": true,
  "dados": {
    "id": 1,
    "nome": "Leonardo",
    "email": "leonardo@email.com"
  }
}
```

### Status

```text
201 Created
400 Bad Request
409 Conflict
```

---

## 5.2 Buscar Usuário

```http
GET /api/usuarios/:id
```

### Parâmetro

```text
id = identificador do usuário
```

### Status

```text
200 OK
404 Not Found
```

---

## 5.3 Atualizar Usuário

```http
PATCH /api/usuarios/:id
```

### Body

Exemplo:

```json
{
  "nome": "Leonardo Silva"
}
```

### Status

```text
200 OK
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

---

# 6. Perfil

## 6.1 Consultar Perfil

```http
GET /api/perfis/:usuarioId
```

---

## 6.2 Atualizar Perfil

```http
PATCH /api/perfis/:usuarioId
```

### Body

```json
{
  "nomePublico": "Leonardo",
  "bio": "Desenvolvedor de Software",
  "localizacao": "Brasília",
  "github": "https://github.com/exemplo",
  "linkedin": "https://linkedin.com/in/exemplo",
  "portfolio": "https://exemplo.com"
}
```

### Status

```text
200 OK
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

---

# 7. Tecnologias do Perfil

## 7.1 Adicionar Tecnologia

```http
POST /api/perfis/:usuarioId/tecnologias
```

### Body

```json
{
  "tecnologiaId": 10
}
```

---

## 7.2 Remover Tecnologia

```http
DELETE /api/perfis/:usuarioId/tecnologias/:tecnologiaId
```

---

## 7.3 Listar Tecnologias

```http
GET /api/perfis/:usuarioId/tecnologias
```

---

# 8. Áreas de Interesse

## 8.1 Adicionar Área

```http
POST /api/perfis/:usuarioId/areas-interesse
```

### Body

```json
{
  "areaInteresseId": 2
}
```

---

## 8.2 Remover Área

```http
DELETE /api/perfis/:usuarioId/areas-interesse/:areaInteresseId
```

---

## 8.3 Listar Áreas

```http
GET /api/perfis/:usuarioId/areas-interesse
```

---

# 9. Seguimento de Usuários

## 9.1 Seguir Usuário

```http
POST /api/usuarios/:id/seguir
```

---

## 9.2 Deixar de Seguir Usuário

```http
DELETE /api/usuarios/:id/seguir
```

---

## 9.3 Listar Seguidores

```http
GET /api/usuarios/:id/seguidores
```

---

## 9.4 Listar Usuários Seguidos

```http
GET /api/usuarios/:id/seguindo
```

---

# 10. Empresas

## 10.1 Cadastrar Empresa

```http
POST /api/empresas
```

### Body

```json
{
  "nome": "Tech Company",
  "nomeFantasia": "Tech",
  "descricao": "Empresa de tecnologia",
  "site": "https://empresa.com"
}
```

### Status

```text
201 Created
400 Bad Request
409 Conflict
```

---

## 10.2 Listar Empresas

```http
GET /api/empresas
```

### Query Parameters opcionais

```text
page
limit
nome
verificada
```

---

## 10.3 Consultar Empresa

```http
GET /api/empresas/:id
```

---

## 10.4 Atualizar Empresa

```http
PATCH /api/empresas/:id
```

---

# 11. Seguimento de Empresas

## 11.1 Seguir Empresa

```http
POST /api/empresas/:id/seguir
```

---

## 11.2 Deixar de Seguir Empresa

```http
DELETE /api/empresas/:id/seguir
```

---

## 11.3 Listar Seguidores

```http
GET /api/empresas/:id/seguidores
```

---

# 12. Verificação de Empresas

## 12.1 Solicitar Verificação

```http
POST /api/empresas/:id/verificacoes
```

---

## 12.2 Consultar Verificação

```http
GET /api/empresas/:id/verificacoes
```

---

## 12.3 Listar Verificações Pendentes

```http
GET /api/admin/verificacoes
```

### Query

```text
status=PENDENTE
```

---

## 12.4 Aprovar Verificação

```http
PATCH /api/admin/verificacoes/:id/aprovar
```

---

## 12.5 Rejeitar Verificação

```http
PATCH /api/admin/verificacoes/:id/rejeitar
```

### Body

```json
{
  "motivo": "Informações insuficientes."
}
```

---

# 13. Eventos

## 13.1 Criar Evento

```http
POST /api/eventos
```

### Body

```json
{
  "nome": "Tech Summit 2027",
  "descricao": "Evento de tecnologia",
  "modalidade": "PRESENCIAL",
  "tipoFinanceiro": "GRATUITO",
  "dataInicio": "2027-05-10T08:00:00",
  "dataFim": "2027-05-10T18:00:00",
  "capacidade": 500,
  "localizacao": "Centro de Convenções"
}
```

### Status

```text
201 Created
400 Bad Request
401 Unauthorized
403 Forbidden
```

---

## 13.2 Listar Eventos

```http
GET /api/eventos
```

### Query Parameters

```text
page
limit
nome
modalidade
tipoFinanceiro
dataInicio
dataFim
localizacao
status
```

---

## 13.3 Consultar Evento

```http
GET /api/eventos/:id
```

---

## 13.4 Atualizar Evento

```http
PATCH /api/eventos/:id
```

---

## 13.5 Enviar Evento para Aprovação

```http
POST /api/eventos/:id/enviar-aprovacao
```

---

## 13.6 Cancelar Evento

```http
POST /api/eventos/:id/cancelar
```

### Body

```json
{
  "motivo": "Evento cancelado pela organização."
}
```

---

# 14. Organizadores do Evento

## 14.1 Adicionar Organizador

```http
POST /api/eventos/:id/organizadores
```

### Body

```json
{
  "empresaId": 5,
  "papel": "COORGANIZADOR"
}
```

---

## 14.2 Listar Organizadores

```http
GET /api/eventos/:id/organizadores
```

---

## 14.3 Remover Organizador

```http
DELETE /api/eventos/:id/organizadores/:empresaId
```

---

# 15. Administração de Eventos

## 15.1 Listar Eventos Pendentes

```http
GET /api/admin/eventos
```

### Query

```text
status=AGUARDANDO_APROVACAO
```

---

## 15.2 Aprovar Evento

```http
PATCH /api/admin/eventos/:id/aprovar
```

---

## 15.3 Rejeitar Evento

```http
PATCH /api/admin/eventos/:id/rejeitar
```

### Body

```json
{
  "motivo": "Informações incompletas."
}
```

---

# 16. Inscrições em Eventos

## 16.1 Inscrever-se

```http
POST /api/eventos/:eventoId/inscricoes
```

---

## 16.2 Consultar Inscrição Própria

```http
GET /api/eventos/:eventoId/minha-inscricao
```

---

## 16.3 Listar Inscrições

```http
GET /api/eventos/:eventoId/inscricoes
```

### Query

```text
page
limit
status
```

---

## 16.4 Consultar Inscrição

```http
GET /api/inscricoes/:id
```

---

## 16.5 Aprovar Inscrição

```http
PATCH /api/inscricoes/:id/aprovar
```

---

## 16.6 Rejeitar Inscrição

```http
PATCH /api/inscricoes/:id/rejeitar
```

### Body opcional

```json
{
  "motivo": "Inscrição não aprovada."
}
```

---

## 16.7 Confirmar Participação

```http
PATCH /api/inscricoes/:id/confirmar
```

---

## 16.8 Cancelar Inscrição

```http
DELETE /api/inscricoes/:id
```

---

# 17. Lista de Espera

## 17.1 Consultar Lista de Espera

```http
GET /api/eventos/:eventoId/lista-espera
```

---

## 17.2 Oferecer Vaga

```http
POST /api/inscricoes/:id/oferecer-vaga
```

---

# 18. Trilhas

## 18.1 Criar Trilha

```http
POST /api/eventos/:eventoId/trilhas
```

### Body

```json
{
  "nome": "Backend",
  "descricao": "Trilha focada em desenvolvimento backend."
}
```

---

## 18.2 Listar Trilhas

```http
GET /api/eventos/:eventoId/trilhas
```

---

## 18.3 Consultar Trilha

```http
GET /api/trilhas/:id
```

---

## 18.4 Atualizar Trilha

```http
PATCH /api/trilhas/:id
```

---

## 18.5 Remover Trilha

```http
DELETE /api/trilhas/:id
```

---

# 19. Atividades

## 19.1 Criar Atividade

```http
POST /api/eventos/:eventoId/atividades
```

### Body

```json
{
  "nome": "Introdução ao Next.js",
  "descricao": "Palestra sobre Next.js",
  "tipo": "PALESTRA",
  "dataInicio": "2027-05-10T10:00:00",
  "dataFim": "2027-05-10T11:00:00",
  "local": "Sala 2",
  "capacidade": 100,
  "exigeInscricao": false,
  "exigeCheckIn": false
}
```

---

## 19.2 Listar Atividades

```http
GET /api/eventos/:eventoId/atividades
```

---

## 19.3 Consultar Atividade

```http
GET /api/atividades/:id
```

---

## 19.4 Atualizar Atividade

```http
PATCH /api/atividades/:id
```

---

# 20. Inscrição em Atividade

## 20.1 Inscrever-se em Atividade

```http
POST /api/atividades/:atividadeId/inscricoes
```

---

## 20.2 Listar Inscritos

```http
GET /api/atividades/:atividadeId/inscricoes
```

---

## 20.3 Cancelar Inscrição

```http
DELETE /api/atividades/:atividadeId/inscricoes/minha
```

---

# 21. Check-in

## 21.1 Check-in no Evento

```http
POST /api/eventos/:eventoId/checkins
```

---

## 21.2 Listar Check-ins do Evento

```http
GET /api/eventos/:eventoId/checkins
```

---

## 21.3 Check-in em Atividade

```http
POST /api/atividades/:atividadeId/checkins
```

---

## 21.4 Listar Check-ins da Atividade

```http
GET /api/atividades/:atividadeId/checkins
```

---

# 22. Hackathons

## 22.1 Criar Configuração de Hackathon

```http
POST /api/eventos/:eventoId/hackathon
```

### Body

```json
{
  "tipoParticipacao": "EQUIPE",
  "minimoIntegrantes": 3,
  "maximoIntegrantes": 5,
  "descricaoRegras": "Regras do hackathon."
}
```

---

## 22.2 Consultar Hackathon

```http
GET /api/hackathons/:id
```

---

## 22.3 Atualizar Hackathon

```http
PATCH /api/hackathons/:id
```

---

# 23. Fases do Hackathon

## 23.1 Criar Fase

```http
POST /api/hackathons/:hackathonId/fases
```

### Body

```json
{
  "nome": "Desenvolvimento",
  "tipo": "DESENVOLVIMENTO",
  "ordem": 3,
  "dataInicio": "2027-05-10T10:00:00",
  "dataFim": "2027-05-11T16:00:00"
}
```

---

## 23.2 Listar Fases

```http
GET /api/hackathons/:hackathonId/fases
```

---

## 23.3 Consultar Fase

```http
GET /api/fases/:id
```

---

## 23.4 Atualizar Fase

```http
PATCH /api/fases/:id
```

---

## 23.5 Reordenar Fases

```http
PATCH /api/hackathons/:hackathonId/fases/ordem
```

### Body

```json
{
  "fases": [
    {
      "id": 1,
      "ordem": 1
    },
    {
      "id": 2,
      "ordem": 2
    }
  ]
}
```

---

# 24. Desafios

## 24.1 Criar Desafio

```http
POST /api/hackathons/:hackathonId/desafios
```

### Body

```json
{
  "titulo": "Mobilidade Urbana",
  "descricao": "Criar solução tecnológica para transporte urbano."
}
```

---

## 24.2 Listar Desafios

```http
GET /api/hackathons/:hackathonId/desafios
```

---

## 24.3 Consultar Desafio

```http
GET /api/desafios/:id
```

---

## 24.4 Atualizar Desafio

```http
PATCH /api/desafios/:id
```

---

# 25. Equipes

## 25.1 Criar Equipe

```http
POST /api/hackathons/:hackathonId/equipes
```

### Body

```json
{
  "nome": "Equipe Atlas"
}
```

---

## 25.2 Listar Equipes

```http
GET /api/hackathons/:hackathonId/equipes
```

---

## 25.3 Consultar Equipe

```http
GET /api/equipes/:id
```

---

## 25.4 Atualizar Equipe

```http
PATCH /api/equipes/:id
```

---

# 26. Convites de Equipe

## 26.1 Convidar Usuário

```http
POST /api/equipes/:equipeId/convites
```

### Body

```json
{
  "usuarioId": 20
}
```

---

## 26.2 Listar Convites

```http
GET /api/equipes/:equipeId/convites
```

---

## 26.3 Aceitar Convite

```http
PATCH /api/convites-equipe/:id/aceitar
```

---

## 26.4 Rejeitar Convite

```http
PATCH /api/convites-equipe/:id/rejeitar
```

---

# 27. Solicitações de Entrada

## 27.1 Solicitar Entrada

```http
POST /api/equipes/:equipeId/solicitacoes
```

---

## 27.2 Listar Solicitações

```http
GET /api/equipes/:equipeId/solicitacoes
```

---

## 27.3 Aprovar Solicitação

```http
PATCH /api/solicitacoes-equipe/:id/aprovar
```

---

## 27.4 Rejeitar Solicitação

```http
PATCH /api/solicitacoes-equipe/:id/rejeitar
```

---

# 28. Membros da Equipe

## 28.1 Listar Membros

```http
GET /api/equipes/:equipeId/membros
```

---

## 28.2 Adicionar Membro pelo Organizador

```http
POST /api/equipes/:equipeId/membros
```

### Body

```json
{
  "usuarioId": 30,
  "papel": "MEMBRO"
}
```

---

## 28.3 Remover Membro

```http
DELETE /api/equipes/:equipeId/membros/:usuarioId
```

---

# 29. Desclassificação de Equipe

## 29.1 Desclassificar

```http
PATCH /api/equipes/:id/desclassificar
```

### Body

```json
{
  "motivo": "Violação das regras do hackathon."
}
```

---

# 30. Submissões

## 30.1 Criar Submissão

```http
POST /api/hackathons/:hackathonId/submissoes
```

### Body

Exemplo por equipe:

```json
{
  "equipeId": 10,
  "titulo": "Projeto Atlas",
  "descricao": "Solução desenvolvida pela equipe."
}
```

Exemplo individual:

```json
{
  "usuarioId": 15,
  "titulo": "Projeto Individual",
  "descricao": "Descrição do projeto."
}
```

---

## 30.2 Consultar Submissão

```http
GET /api/submissoes/:id
```

---

## 30.3 Listar Submissões

```http
GET /api/hackathons/:hackathonId/submissoes
```

---

# 31. Versões da Submissão

## 31.1 Enviar Versão

```http
POST /api/submissoes/:submissaoId/versoes
```

### Body

```json
{
  "urlProjeto": "https://projeto.com",
  "urlRepositorio": "https://github.com/equipe/projeto"
}
```

---

## 31.2 Listar Versões

```http
GET /api/submissoes/:submissaoId/versoes
```

---

## 31.3 Consultar Versão

```http
GET /api/versoes-submissao/:id
```

---

# 32. Critérios de Avaliação

## 32.1 Criar Critério

```http
POST /api/hackathons/:hackathonId/criterios-avaliacao
```

### Body

```json
{
  "nome": "Inovação",
  "descricao": "Nível de inovação da solução.",
  "peso": 3
}
```

---

## 32.2 Listar Critérios

```http
GET /api/hackathons/:hackathonId/criterios-avaliacao
```

---

## 32.3 Atualizar Critério

```http
PATCH /api/criterios-avaliacao/:id
```

---

# 33. Jurados

## 33.1 Associar Jurado

```http
POST /api/hackathons/:hackathonId/jurados
```

### Body

```json
{
  "usuarioId": 50
}
```

---

## 33.2 Listar Jurados

```http
GET /api/hackathons/:hackathonId/jurados
```

---

## 33.3 Remover Jurado

```http
DELETE /api/hackathons/:hackathonId/jurados/:usuarioId
```

---

# 34. Avaliações

## 34.1 Registrar Avaliação

```http
POST /api/hackathons/:hackathonId/avaliacoes
```

### Body

```json
{
  "equipeId": 10,
  "criterioId": 4,
  "nota": 9.0,
  "observacao": "Boa execução técnica."
}
```

---

## 34.2 Listar Avaliações

```http
GET /api/hackathons/:hackathonId/avaliacoes
```

---

## 34.3 Consultar Avaliação

```http
GET /api/avaliacoes/:id
```

---

# 35. Resultados

## 35.1 Registrar Resultado

```http
POST /api/hackathons/:hackathonId/resultados
```

### Body

```json
{
  "equipeId": 10,
  "pontuacaoFinal": 92.5,
  "posicao": 1
}
```

---

## 35.2 Listar Resultados

```http
GET /api/hackathons/:hackathonId/resultados
```

---

## 35.3 Atualizar Resultado

```http
PATCH /api/resultados/:id
```

---

# 36. Ranking

## 36.1 Consultar Ranking

```http
GET /api/hackathons/:hackathonId/ranking
```

---

## 36.2 Alterar Visibilidade

```http
PATCH /api/hackathons/:hackathonId/ranking/visibilidade
```

### Body

```json
{
  "visibilidade": "PUBLICADO"
}
```

Valores:

```text
OCULTO
PUBLICADO
```

---

# 37. Emblemas

## 37.1 Criar Emblema

```http
POST /api/eventos/:eventoId/emblemas
```

### Body

```json
{
  "nome": "Campeão",
  "descricao": "Primeiro lugar no hackathon.",
  "imagem": "url-da-imagem"
}
```

---

## 37.2 Listar Emblemas

```http
GET /api/eventos/:eventoId/emblemas
```

---

## 37.3 Consultar Emblema

```http
GET /api/emblemas/:id
```

---

# 38. Concessão de Emblemas

## 38.1 Conceder Emblema

```http
POST /api/emblemas/:emblemaId/concessoes
```

### Body

```json
{
  "usuarioId": 15
}
```

---

## 38.2 Consultar Emblemas do Usuário

```http
GET /api/usuarios/:usuarioId/emblemas
```

---

# 39. Certificados

## 39.1 Criar Modelo de Certificado

```http
POST /api/eventos/:eventoId/certificados
```

### Body

```json
{
  "nome": "Certificado de Participação",
  "descricao": "Certificado destinado aos participantes.",
  "tipo": "PARTICIPACAO"
}
```

---

## 39.2 Listar Certificados do Evento

```http
GET /api/eventos/:eventoId/certificados
```

---

# 40. Emissão de Certificados

## 40.1 Emitir Certificado

```http
POST /api/certificados/:certificadoId/emissoes
```

### Body

```json
{
  "usuarioId": 15
}
```

---

## 40.2 Consultar Certificados do Usuário

```http
GET /api/usuarios/:usuarioId/certificados
```

---

# 41. Patrocinadores

## 41.1 Associar Patrocinador

```http
POST /api/eventos/:eventoId/patrocinadores
```

### Body

```json
{
  "empresaId": 20,
  "categoria": "GOLD"
}
```

---

## 41.2 Listar Patrocinadores

```http
GET /api/eventos/:eventoId/patrocinadores
```

---

## 41.3 Remover Patrocinador

```http
DELETE /api/eventos/:eventoId/patrocinadores/:empresaId
```

---

# 42. Estandes

## 42.1 Criar Estande

```http
POST /api/eventos/:eventoId/estandes
```

### Body

```json
{
  "empresaId": 20,
  "nome": "Estande Tech",
  "descricao": "Demonstrações e recrutamento.",
  "tipo": "FISICO",
  "localizacao": "Área B - Estande 12"
}
```

---

## 42.2 Listar Estandes

```http
GET /api/eventos/:eventoId/estandes
```

---

## 42.3 Consultar Estande

```http
GET /api/estandes/:id
```

---

## 42.4 Atualizar Estande

```http
PATCH /api/estandes/:id
```

---

# 43. Ofertas

## 43.1 Criar Oferta

```http
POST /api/eventos/:eventoId/ofertas
```

### Body

```json
{
  "empresaId": 20,
  "titulo": "30% de desconto",
  "descricao": "Oferta exclusiva para participantes.",
  "dataInicio": "2027-05-10T08:00:00",
  "dataFim": "2027-05-10T18:00:00"
}
```

---

## 43.2 Listar Ofertas

```http
GET /api/eventos/:eventoId/ofertas
```

---

## 43.3 Consultar Oferta

```http
GET /api/ofertas/:id
```

---

# 44. Comunicados

## 44.1 Criar Comunicado

```http
POST /api/eventos/:eventoId/comunicados
```

### Body

```json
{
  "titulo": "Mudança de Sala",
  "mensagem": "A palestra foi movida para a Sala 5.",
  "tipoPublico": "TODOS"
}
```

---

## 44.2 Listar Comunicados

```http
GET /api/eventos/:eventoId/comunicados
```

---

## 44.3 Consultar Comunicado

```http
GET /api/comunicados/:id
```

---

# 45. Notificações

## 45.1 Listar Notificações do Usuário

```http
GET /api/notificacoes
```

### Query

```text
page
limit
lida
categoria
```

---

## 45.2 Marcar Notificação como Lida

```http
PATCH /api/notificacoes/:id/lida
```

---

## 45.3 Marcar Todas como Lidas

```http
PATCH /api/notificacoes/marcar-todas-lidas
```

---

# 46. Preferências de Notificação

## 46.1 Consultar Preferências

```http
GET /api/notificacoes/preferencias
```

---

## 46.2 Atualizar Preferências

```http
PATCH /api/notificacoes/preferencias
```

### Body

```json
{
  "operacional": true,
  "social": true,
  "promocional": false
}
```

Notificações essenciais seguem as regras próprias da plataforma.

---

# 47. Histórico do Usuário

## 47.1 Eventos Participados

```http
GET /api/usuarios/:usuarioId/eventos
```

---

## 47.2 Hackathons Participados

```http
GET /api/usuarios/:usuarioId/hackathons
```

---

## 47.3 Resultados do Usuário

```http
GET /api/usuarios/:usuarioId/resultados
```

---

# 48. Histórico da Empresa

## 48.1 Eventos Organizados

```http
GET /api/empresas/:empresaId/eventos
```

---

## 48.2 Patrocínios

```http
GET /api/empresas/:empresaId/patrocinios
```

---

# 49. Paginação

Endpoints que retornem listas extensas devem aceitar:

```text
page
limit
```

Exemplo:

```http
GET /api/eventos?page=1&limit=20
```

Resposta sugerida:

```json
{
  "sucesso": true,
  "dados": [
    {}
  ],
  "paginacao": {
    "pagina": 1,
    "limite": 20,
    "totalItens": 150,
    "totalPaginas": 8
  }
}
```

---

# 50. Filtros

Os endpoints podem aceitar filtros de acordo com o recurso.

Exemplo:

```http
GET /api/eventos?modalidade=PRESENCIAL&tipoFinanceiro=GRATUITO
```

---

# 51. Ordenação

Quando aplicável:

```text
sort
order
```

Exemplo:

```http
GET /api/eventos?sort=dataInicio&order=asc
```

---

# 52. Rotas que Exigem Autenticação

Operações pessoais ou de alteração devem exigir usuário autenticado.

Exemplos:

```text
editar perfil
seguir usuário
seguir empresa
inscrever-se
criar equipe
enviar submissão
consultar notificações
```

---

# 53. Rotas de Empresa

Operações administrativas de empresa devem exigir vínculo apropriado com a empresa.

Exemplos:

```text
editar empresa
criar evento
editar evento
administrar inscrições
criar atividades
configurar hackathon
```

---

# 54. Rotas Administrativas

Rotas iniciadas por:

```text
/api/admin
```

devem representar funções administrativas da plataforma.

Exemplos:

```text
/api/admin/verificacoes

/api/admin/eventos
```

---

# 55. Rotas de Organização do Evento

Recursos relacionados ao evento devem, sempre que possível, manter o contexto explícito na rota.

Exemplo:

```text
/api/eventos/:eventoId/atividades

/api/eventos/:eventoId/trilhas

/api/eventos/:eventoId/patrocinadores
```

Isso facilita compreender a relação entre os recursos.

---

# 56. Identificadores

O formato técnico definitivo dos identificadores ainda será definido.

Este documento utiliza exemplos numéricos apenas para facilitar a leitura:

```text
1
10
20
```

Posteriormente os IDs poderão utilizar outro formato conforme a decisão de persistência.

---

# 57. Campos de Data

Datas enviadas pela API devem seguir formato padronizado.

Exemplo recomendado:

```text
2027-05-10T10:00:00
```

A estratégia definitiva de timezone deverá ser definida na implementação.

---

# 58. Recursos Ainda Não Cobertos

Os seguintes módulos não fazem parte da API inicial:

```text
carteira interna
saldo
créditos
compras
transações
estornos
pagamento privado dentro do evento
```

Quando esses módulos entrarem no escopo, seus endpoints deverão ser adicionados neste documento.

---

# 59. Fluxo de Consulta para Implementação

Antes de implementar um endpoint:

```text
REQUISITOS.md
↓
REGRAS-DE-NEGOCIO.md
↓
MODELO-DE-DADOS.md
↓
API.md
↓
GUIA-CICLO-ENDPOINT.md
↓
IMPLEMENTAÇÃO
↓
TESTES-POSTMAN.md
```

---

# 60. Resumo dos Principais Recursos

```text
/api/auth

/api/usuarios

/api/perfis

/api/empresas

/api/eventos

/api/inscricoes

/api/trilhas

/api/atividades

/api/hackathons

/api/fases

/api/desafios

/api/equipes

/api/submissoes

/api/avaliacoes

/api/resultados

/api/emblemas

/api/certificados

/api/estandes

/api/ofertas

/api/comunicados

/api/notificacoes

/api/admin
```

---

# 61. Regra de Manutenção

Sempre que uma funcionalidade nova exigir comunicação pela API, este documento deve ser atualizado.

Toda alteração relevante em:

```text
rota
método
body
parâmetro
resposta
status
```

deve ser refletida aqui.

O `API.md` representa o contrato de comunicação da aplicação.

Ele deve permanecer consistente com:

```text
REQUISITOS.md
REGRAS-DE-NEGOCIO.md
MODELO-DE-DADOS.md
```
