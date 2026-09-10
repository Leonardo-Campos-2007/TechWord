# API

## 1. Objetivo

Este documento apresenta a estrutura inicial dos endpoints.

Os contratos detalhados poderão ser refinados durante a implementação.

## 2. Usuários

```text
POST   /api/usuarios
GET    /api/usuarios/:id
PATCH  /api/usuarios/:id
```

## 3. Autenticação

```text
POST /api/auth/login
POST /api/auth/logout
```

## 4. Empresas

```text
POST   /api/empresas
GET    /api/empresas
GET    /api/empresas/:id
PATCH  /api/empresas/:id
POST   /api/empresas/:id/verificacao
```

## 5. Administração de Empresas

```text
GET   /api/admin/verificacoes
PATCH /api/admin/verificacoes/:id/aprovar
PATCH /api/admin/verificacoes/:id/rejeitar
```

## 6. Eventos

```text
POST   /api/eventos
GET    /api/eventos
GET    /api/eventos/:id
PATCH  /api/eventos/:id
POST   /api/eventos/:id/enviar-aprovacao
POST   /api/eventos/:id/cancelar
```

## 7. Aprovação de Eventos

```text
GET   /api/admin/eventos/pendentes
PATCH /api/admin/eventos/:id/aprovar
PATCH /api/admin/eventos/:id/rejeitar
```

## 8. Inscrições

```text
POST   /api/eventos/:id/inscricoes
GET    /api/eventos/:id/inscricoes
PATCH  /api/inscricoes/:id/aprovar
PATCH  /api/inscricoes/:id/rejeitar
PATCH  /api/inscricoes/:id/confirmar
DELETE /api/inscricoes/:id
```

## 9. Trilhas

```text
POST   /api/eventos/:id/trilhas
GET    /api/eventos/:id/trilhas
PATCH  /api/trilhas/:id
DELETE /api/trilhas/:id
```

## 10. Atividades

```text
POST   /api/eventos/:id/atividades
GET    /api/eventos/:id/atividades
GET    /api/atividades/:id
PATCH  /api/atividades/:id
```

## 11. Inscrição em Atividade

```text
POST   /api/atividades/:id/inscricoes
DELETE /api/atividades/:id/inscricoes/:inscricaoId
```

## 12. Check-in

```text
POST /api/eventos/:id/checkin
POST /api/atividades/:id/checkin
```

## 13. Hackathons

```text
POST  /api/eventos/:id/hackathon
GET   /api/hackathons/:id
PATCH /api/hackathons/:id
```

## 14. Fases

```text
POST  /api/hackathons/:id/fases
GET   /api/hackathons/:id/fases
PATCH /api/fases/:id
```

## 15. Desafios

```text
POST  /api/hackathons/:id/desafios
GET   /api/hackathons/:id/desafios
PATCH /api/desafios/:id
```

## 16. Equipes

```text
POST   /api/hackathons/:id/equipes
GET    /api/hackathons/:id/equipes
GET    /api/equipes/:id
PATCH  /api/equipes/:id
POST   /api/equipes/:id/convites
POST   /api/equipes/:id/solicitacoes
PATCH  /api/equipes/:id/desclassificar
```

## 17. Submissões

```text
POST /api/hackathons/:id/submissoes
GET  /api/hackathons/:id/submissoes
POST /api/submissoes/:id/versoes
```

## 18. Avaliações

```text
POST /api/hackathons/:id/criterios
POST /api/hackathons/:id/jurados
POST /api/hackathons/:id/avaliacoes
POST /api/hackathons/:id/resultados
```

## 19. Ranking

```text
GET   /api/hackathons/:id/ranking
PATCH /api/hackathons/:id/ranking/visibilidade
```

## 20. Emblemas

```text
POST /api/eventos/:id/emblemas
GET  /api/eventos/:id/emblemas
POST /api/emblemas/:id/conceder
```

## 21. Certificados

```text
POST /api/eventos/:id/certificados
GET  /api/usuarios/:id/certificados
```

## 22. Seguimentos

```text
POST   /api/usuarios/:id/seguir
DELETE /api/usuarios/:id/seguir

POST   /api/empresas/:id/seguir
DELETE /api/empresas/:id/seguir
```

## 23. Patrocinadores

```text
POST /api/eventos/:id/patrocinadores
POST /api/eventos/:id/estandes
POST /api/eventos/:id/ofertas
```

## 24. Comunicados

```text
POST /api/eventos/:id/comunicados
GET  /api/eventos/:id/comunicados
```

## 25. Notificações

```text
GET   /api/notificacoes
PATCH /api/notificacoes/:id/lida
GET   /api/notificacoes/preferencias
PATCH /api/notificacoes/preferencias
```
