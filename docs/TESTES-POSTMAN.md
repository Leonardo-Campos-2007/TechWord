# TESTES DE API COM POSTMAN

## 1. Objetivo do Documento

Este documento define os testes manuais de API que devem ser executados utilizando o Postman.

O objetivo é validar:

* funcionamento dos endpoints;
* dados obrigatórios;
* formatos inválidos;
* recursos inexistentes;
* duplicidades;
* regras de negócio;
* permissões;
* mudanças de estado;
* respostas HTTP;
* integridade dos dados.

Cada funcionalidade deverá ser testada antes de ser considerada concluída.

---

# 2. Estrutura Recomendada no Postman

Criar uma Collection principal:

```text
API - Eventos e Hackathons
│
├── Auth
├── Usuarios
├── Perfis
├── Empresas
├── Verificacoes
├── Eventos
├── Organizadores
├── Inscricoes
├── Trilhas
├── Atividades
├── Checkins
├── Hackathons
├── Fases
├── Desafios
├── Equipes
├── Convites
├── SolicitacoesEquipe
├── Submissoes
├── Avaliacoes
├── Resultados
├── Ranking
├── Emblemas
├── Certificados
├── Patrocinadores
├── Estandes
├── Ofertas
├── Comunicados
├── Notificacoes
└── Admin
```

---

# 3. Variáveis de Ambiente

Criar no Postman:

```text
baseUrl

usuarioId

empresaId

eventoId

inscricaoId

atividadeId

hackathonId

equipeId

submissaoId

token
```

Exemplo:

```text
baseUrl = http://localhost:3000
```

Uso:

```text
{{baseUrl}}/api/usuarios
```

---

# 4. Padrão Geral de Validação

Para cada endpoint verificar:

```text
[ ] Método HTTP correto
[ ] URL correta
[ ] Headers corretos
[ ] Body correto
[ ] Status HTTP correto
[ ] Estrutura da resposta correta
[ ] Dados retornados corretos
[ ] Regras de negócio respeitadas
[ ] Operação persistida corretamente
```

---

# 5. AUTENTICAÇÃO

## TST-AUTH-001 — Login válido

Endpoint:

```http
POST /api/auth/login
```

Body:

```json
{
  "email": "usuario@email.com",
  "senha": "Senha123"
}
```

Esperado:

```text
200 OK
```

Validar:

```text
[ ] login realizado
[ ] usuário retornado
[ ] dados sensíveis não retornados
```

---

## TST-AUTH-002 — E-mail inexistente

Esperado:

```text
401 Unauthorized
```

---

## TST-AUTH-003 — Senha incorreta

Esperado:

```text
401 Unauthorized
```

---

## TST-AUTH-004 — E-mail vazio

Esperado:

```text
400 Bad Request
```

---

## TST-AUTH-005 — Senha vazia

Esperado:

```text
400 Bad Request
```

---

## TST-AUTH-006 — Body vazio

Esperado:

```text
400 Bad Request
```

---

## TST-AUTH-007 — Logout autenticado

```http
POST /api/auth/logout
```

Esperado:

```text
204 No Content
```

---

## TST-AUTH-008 — Logout sem autenticação

Esperado:

```text
401 Unauthorized
```

---

# 6. USUÁRIOS

## TST-USR-001 — Cadastro válido

```http
POST /api/usuarios
```

Body:

```json
{
  "nome": "Leonardo",
  "email": "leonardo@email.com",
  "senha": "Senha123"
}
```

Esperado:

```text
201 Created
```

Validar:

```text
[ ] usuário criado
[ ] id retornado
[ ] nome correto
[ ] e-mail correto
[ ] senha não retornada
```

---

## TST-USR-002 — E-mail duplicado

Enviar cadastro com e-mail já existente.

Esperado:

```text
409 Conflict
```

---

## TST-USR-003 — Nome ausente

Esperado:

```text
400 Bad Request
```

---

## TST-USR-004 — E-mail ausente

Esperado:

```text
400 Bad Request
```

---

## TST-USR-005 — Senha ausente

Esperado:

```text
400 Bad Request
```

---

## TST-USR-006 — E-mail inválido

Body:

```json
{
  "nome": "Leonardo",
  "email": "email-invalido",
  "senha": "Senha123"
}
```

Esperado:

```text
400 Bad Request
```

---

## TST-USR-007 — Consultar usuário existente

```http
GET /api/usuarios/:id
```

Esperado:

```text
200 OK
```

---

## TST-USR-008 — Consultar usuário inexistente

Esperado:

```text
404 Not Found
```

---

## TST-USR-009 — Atualizar próprio usuário

```http
PATCH /api/usuarios/:id
```

Esperado:

```text
200 OK
```

---

## TST-USR-010 — Atualizar usuário inexistente

Esperado:

```text
404 Not Found
```

---

## TST-USR-011 — Atualizar usuário de outra pessoa

Esperado:

```text
403 Forbidden
```

---

# 7. PERFIL

## TST-PRF-001 — Consultar perfil existente

```http
GET /api/perfis/:usuarioId
```

Esperado:

```text
200 OK
```

---

## TST-PRF-002 — Consultar perfil inexistente

Esperado:

```text
404 Not Found
```

---

## TST-PRF-003 — Atualizar próprio perfil

Esperado:

```text
200 OK
```

---

## TST-PRF-004 — Atualizar perfil de outro usuário

Esperado:

```text
403 Forbidden
```

---

## TST-PRF-005 — Link GitHub válido

Esperado:

```text
200 OK
```

---

## TST-PRF-006 — URL inválida

Esperado:

```text
400 Bad Request
```

---

# 8. TECNOLOGIAS

## TST-TEC-001 — Adicionar tecnologia

```http
POST /api/perfis/:usuarioId/tecnologias
```

Esperado:

```text
201 Created
```

---

## TST-TEC-002 — Tecnologia inexistente

Esperado:

```text
404 Not Found
```

---

## TST-TEC-003 — Tecnologia duplicada no perfil

Esperado:

```text
409 Conflict
```

---

## TST-TEC-004 — Remover tecnologia

Esperado:

```text
204 No Content
```

---

## TST-TEC-005 — Listar tecnologias

Esperado:

```text
200 OK
```

---

# 9. ÁREAS DE INTERESSE

## TST-ARE-001 — Adicionar área

Esperado:

```text
201 Created
```

---

## TST-ARE-002 — Área inexistente

Esperado:

```text
404 Not Found
```

---

## TST-ARE-003 — Área duplicada

Esperado:

```text
409 Conflict
```

---

## TST-ARE-004 — Remover área

Esperado:

```text
204 No Content
```

---

# 10. SEGUIR USUÁRIOS

## TST-SOC-001 — Seguir outro usuário

Esperado:

```text
201 Created
```

---

## TST-SOC-002 — Seguir usuário inexistente

Esperado:

```text
404 Not Found
```

---

## TST-SOC-003 — Seguir a si próprio

Esperado:

```text
409 Conflict
```

---

## TST-SOC-004 — Seguir usuário já seguido

Esperado:

```text
409 Conflict
```

---

## TST-SOC-005 — Deixar de seguir

Esperado:

```text
204 No Content
```

---

## TST-SOC-006 — Listar seguidores

Esperado:

```text
200 OK
```

---

# 11. EMPRESAS

## TST-EMP-001 — Cadastrar empresa

```http
POST /api/empresas
```

Esperado:

```text
201 Created
```

---

## TST-EMP-002 — Nome obrigatório ausente

Esperado:

```text
400 Bad Request
```

---

## TST-EMP-003 — Consultar empresa

Esperado:

```text
200 OK
```

---

## TST-EMP-004 — Empresa inexistente

Esperado:

```text
404 Not Found
```

---

## TST-EMP-005 — Atualizar empresa

Esperado:

```text
200 OK
```

---

## TST-EMP-006 — Atualização sem permissão

Esperado:

```text
403 Forbidden
```

---

# 12. SEGUIR EMPRESA

## TST-SEGEMP-001 — Seguir empresa

Esperado:

```text
201 Created
```

---

## TST-SEGEMP-002 — Seguir empresa inexistente

Esperado:

```text
404 Not Found
```

---

## TST-SEGEMP-003 — Seguir empresa novamente

Esperado:

```text
409 Conflict
```

---

## TST-SEGEMP-004 — Deixar de seguir empresa

Esperado:

```text
204 No Content
```

---

# 13. VERIFICAÇÃO DE EMPRESA

## TST-VER-001 — Solicitar verificação

Esperado:

```text
201 Created
```

---

## TST-VER-002 — Empresa inexistente

Esperado:

```text
404 Not Found
```

---

## TST-VER-003 — Solicitação duplicada pendente

Esperado:

```text
409 Conflict
```

---

## TST-VER-004 — Listar solicitações pendentes como admin

Esperado:

```text
200 OK
```

---

## TST-VER-005 — Usuário comum tenta listar verificações

Esperado:

```text
403 Forbidden
```

---

## TST-VER-006 — Aprovar empresa

Esperado:

```text
200 OK
```

Validar:

```text
[ ] status atualizado
[ ] selo de verificação disponível
```

---

## TST-VER-007 — Rejeitar empresa

Esperado:

```text
200 OK
```

---

## TST-VER-008 — Rejeitar sem motivo

Esperado:

```text
400 Bad Request
```

---

# 14. EVENTOS

## TST-EVT-001 — Criar evento válido

Esperado:

```text
201 Created
```

---

## TST-EVT-002 — Empresa não verificada cria evento oficial

Esperado:

```text
403 Forbidden
```

---

## TST-EVT-003 — Nome ausente

Esperado:

```text
400 Bad Request
```

---

## TST-EVT-004 — Data final anterior à inicial

Esperado:

```text
400 Bad Request
```

---

## TST-EVT-005 — Modalidade inválida

Esperado:

```text
400 Bad Request
```

---

## TST-EVT-006 — Evento presencial sem localização

Esperado:

```text
400 Bad Request
```

---

## TST-EVT-007 — Criar evento gratuito

Esperado:

```text
201 Created
```

---

## TST-EVT-008 — Criar evento pago

Esperado:

```text
201 Created
```

---

## TST-EVT-009 — Consultar evento

Esperado:

```text
200 OK
```

---

## TST-EVT-010 — Evento inexistente

Esperado:

```text
404 Not Found
```

---

## TST-EVT-011 — Editar evento

Esperado:

```text
200 OK
```

---

## TST-EVT-012 — Enviar evento para aprovação

Esperado:

```text
200 OK
```

---

## TST-EVT-013 — Enviar evento já submetido

Esperado:

```text
409 Conflict
```

---

## TST-EVT-014 — Aprovar evento como admin

Esperado:

```text
200 OK
```

---

## TST-EVT-015 — Usuário comum tenta aprovar

Esperado:

```text
403 Forbidden
```

---

## TST-EVT-016 — Rejeitar evento

Esperado:

```text
200 OK
```

---

## TST-EVT-017 — Cancelar evento

Esperado:

```text
200 OK
```

Validar:

```text
[ ] status CANCELADO
[ ] evento continua consultável
```

---

# 15. ORGANIZADORES

## TST-ORG-001 — Adicionar coorganizador

Esperado:

```text
201 Created
```

---

## TST-ORG-002 — Empresa inexistente

Esperado:

```text
404 Not Found
```

---

## TST-ORG-003 — Adicionar organizador duplicado

Esperado:

```text
409 Conflict
```

---

## TST-ORG-004 — Remover coorganizador

Esperado:

```text
204 No Content
```

---

# 16. BUSCA DE EVENTOS

## TST-BUS-001 — Listar eventos

Esperado:

```text
200 OK
```

---

## TST-BUS-002 — Filtrar por modalidade

```text
modalidade=PRESENCIAL
```

Esperado:

```text
200 OK
```

Validar:

```text
[ ] somente eventos presenciais
```

---

## TST-BUS-003 — Filtrar por gratuito

---

## TST-BUS-004 — Filtrar por período

---

## TST-BUS-005 — Filtrar por localização

---

## TST-BUS-006 — Paginação

```text
page=1&limit=10
```

Validar:

```text
[ ] máximo de 10 registros
[ ] paginação retornada
```

---

# 17. INSCRIÇÕES

## TST-INS-001 — Inscrição válida

Esperado:

```text
201 Created
```

---

## TST-INS-002 — Usuário não autenticado

Esperado:

```text
401 Unauthorized
```

---

## TST-INS-003 — Evento inexistente

Esperado:

```text
404 Not Found
```

---

## TST-INS-004 — Inscrição duplicada

Esperado:

```text
409 Conflict
```

---

## TST-INS-005 — Evento sem vagas

Sem lista de espera.

Esperado:

```text
409 Conflict
```

---

## TST-INS-006 — Evento lotado com lista de espera

Esperado:

```text
201 Created
```

Validar:

```text
[ ] status LISTA_ESPERA
```

---

## TST-INS-007 — Evento com aprovação manual

Validar:

```text
[ ] status AGUARDANDO_APROVACAO
```

---

## TST-INS-008 — Aprovar inscrição

Esperado:

```text
200 OK
```

---

## TST-INS-009 — Rejeitar inscrição

Esperado:

```text
200 OK
```

---

## TST-INS-010 — Confirmar participação

Esperado:

```text
200 OK
```

---

## TST-INS-011 — Cancelar inscrição

Esperado:

```text
204 No Content
```

---

## TST-INS-012 — Cancelar inscrição de outro usuário

Esperado:

```text
403 Forbidden
```

---

# 18. LISTA DE ESPERA

## TST-LST-001 — Consultar lista

Esperado:

```text
200 OK
```

---

## TST-LST-002 — Usuário sem permissão consulta lista

Esperado:

```text
403 Forbidden
```

---

## TST-LST-003 — Oferecer vaga

Esperado:

```text
200 OK
```

Validar:

```text
[ ] status VAGA_OFERECIDA
```

---

# 19. TRILHAS

## TST-TRI-001 — Criar trilha

Esperado:

```text
201 Created
```

---

## TST-TRI-002 — Evento inexistente

Esperado:

```text
404 Not Found
```

---

## TST-TRI-003 — Editar trilha

Esperado:

```text
200 OK
```

---

## TST-TRI-004 — Excluir trilha sem dependências

Esperado:

```text
204 No Content
```

---

## TST-TRI-005 — Excluir trilha com dependências incompatíveis

Esperado:

```text
409 Conflict
```

---

# 20. ATIVIDADES

## TST-ATV-001 — Criar atividade

Esperado:

```text
201 Created
```

---

## TST-ATV-002 — Horário inválido

Fim anterior ao início.

Esperado:

```text
400 Bad Request
```

---

## TST-ATV-003 — Criar atividade sem trilha

Esperado:

```text
201 Created
```

---

## TST-ATV-004 — Criar atividade com trilha

Esperado:

```text
201 Created
```

---

## TST-ATV-005 — Trilha inexistente

Esperado:

```text
404 Not Found
```

---

## TST-ATV-006 — Inscrição em atividade

Esperado:

```text
201 Created
```

---

## TST-ATV-007 — Atividade lotada

Esperado:

```text
409 Conflict
```

---

## TST-ATV-008 — Inscrição duplicada

Esperado:

```text
409 Conflict
```

---

## TST-ATV-009 — Cancelar inscrição

Esperado:

```text
204 No Content
```

---

# 21. CHECK-IN

## TST-CHK-001 — Check-in válido em evento

Esperado:

```text
201 Created
```

---

## TST-CHK-002 — Check-in sem inscrição quando exigida

Esperado:

```text
403 Forbidden
```

---

## TST-CHK-003 — Check-in duplicado

Esperado:

```text
409 Conflict
```

---

## TST-CHK-004 — Check-in em atividade

Esperado:

```text
201 Created
```

---

## TST-CHK-005 — Check-in em atividade inexistente

Esperado:

```text
404 Not Found
```

---

# 22. HACKATHONS

## TST-HCK-001 — Criar hackathon

Esperado:

```text
201 Created
```

---

## TST-HCK-002 — Evento inexistente

Esperado:

```text
404 Not Found
```

---

## TST-HCK-003 — Evento já possui hackathon

Esperado:

```text
409 Conflict
```

---

## TST-HCK-004 — Mínimo maior que máximo

Esperado:

```text
400 Bad Request
```

---

## TST-HCK-005 — Tipo de participação inválido

Esperado:

```text
400 Bad Request
```

---

# 23. FASES

## TST-FAS-001 — Criar fase

Esperado:

```text
201 Created
```

---

## TST-FAS-002 — Data final anterior à inicial

Esperado:

```text
400 Bad Request
```

---

## TST-FAS-003 — Criar fase personalizada

Esperado:

```text
201 Created
```

---

## TST-FAS-004 — Reordenar fases

Esperado:

```text
200 OK
```

---

## TST-FAS-005 — Ordem duplicada inválida

Esperado:

```text
409 Conflict
```

---

# 24. DESAFIOS

## TST-DSF-001 — Criar desafio

Esperado:

```text
201 Created
```

---

## TST-DSF-002 — Título ausente

Esperado:

```text
400 Bad Request
```

---

## TST-DSF-003 — Associar patrocinador

Esperado:

```text
201 Created
```

---

## TST-DSF-004 — Patrocinador inexistente

Esperado:

```text
404 Not Found
```

---

# 25. EQUIPES

## TST-EQP-001 — Criar equipe

Esperado:

```text
201 Created
```

---

## TST-EQP-002 — Hackathon individual

Tentar criar equipe em hackathon exclusivamente individual.

Esperado:

```text
409 Conflict
```

---

## TST-EQP-003 — Criador definido como líder

Validar:

```text
[ ] criador pertence à equipe
[ ] papel LIDER
```

---

## TST-EQP-004 — Equipe acima do limite máximo

Esperado:

```text
409 Conflict
```

---

## TST-EQP-005 — Equipe abaixo do mínimo

Validar:

```text
[ ] status EM_FORMACAO
```

---

## TST-EQP-006 — Equipe atinge mínimo

Validar:

```text
[ ] status pode se tornar APTA
```

---

## TST-EQP-007 — Desclassificar equipe

Esperado:

```text
200 OK
```

---

## TST-EQP-008 — Desclassificar sem motivo

Esperado:

```text
400 Bad Request
```

---

# 26. CONVITES DE EQUIPE

## TST-CNV-001 — Enviar convite

Esperado:

```text
201 Created
```

---

## TST-CNV-002 — Convite duplicado pendente

Esperado:

```text
409 Conflict
```

---

## TST-CNV-003 — Aceitar convite

Esperado:

```text
200 OK
```

Validar:

```text
[ ] usuário adicionado à equipe
[ ] convite ACEITO
```

---

## TST-CNV-004 — Rejeitar convite

Esperado:

```text
200 OK
```

---

## TST-CNV-005 — Aceitar convite com equipe lotada

Esperado:

```text
409 Conflict
```

---

# 27. SOLICITAÇÃO DE ENTRADA EM EQUIPE

## TST-SOL-001 — Solicitar entrada

Esperado:

```text
201 Created
```

---

## TST-SOL-002 — Solicitação duplicada

Esperado:

```text
409 Conflict
```

---

## TST-SOL-003 — Aprovar solicitação

Esperado:

```text
200 OK
```

---

## TST-SOL-004 — Rejeitar solicitação

Esperado:

```text
200 OK
```

---

## TST-SOL-005 — Aprovar com equipe cheia

Esperado:

```text
409 Conflict
```

---

# 28. SUBMISSÕES

## TST-SUB-001 — Criar submissão válida

Esperado:

```text
201 Created
```

---

## TST-SUB-002 — Submissão antes da abertura

Esperado:

```text
409 Conflict
```

---

## TST-SUB-003 — Submissão após encerramento

Esperado:

```text
409 Conflict
```

---

## TST-SUB-004 — Equipe inexistente

Esperado:

```text
404 Not Found
```

---

## TST-SUB-005 — Usuário sem participação

Esperado:

```text
403 Forbidden
```

---

## TST-SUB-006 — Enviar nova versão

Esperado:

```text
201 Created
```

---

## TST-SUB-007 — Histórico preservado

Após nova versão:

```text
[ ] versão anterior continua existindo
[ ] nova versão possui número diferente
```

---

## TST-SUB-008 — Versão enviada após prazo

Esperado:

```text
409 Conflict
```

---

# 29. CRITÉRIOS DE AVALIAÇÃO

## TST-CRT-001 — Criar critério

Esperado:

```text
201 Created
```

---

## TST-CRT-002 — Nome ausente

Esperado:

```text
400 Bad Request
```

---

## TST-CRT-003 — Peso inválido

Esperado:

```text
400 Bad Request
```

---

## TST-CRT-004 — Editar critério

Esperado:

```text
200 OK
```

---

# 30. JURADOS

## TST-JUR-001 — Associar jurado

Esperado:

```text
201 Created
```

---

## TST-JUR-002 — Usuário inexistente

Esperado:

```text
404 Not Found
```

---

## TST-JUR-003 — Jurado duplicado

Esperado:

```text
409 Conflict
```

---

## TST-JUR-004 — Remover jurado

Esperado:

```text
204 No Content
```

---

# 31. AVALIAÇÕES

## TST-AVL-001 — Registrar avaliação

Esperado:

```text
201 Created
```

---

## TST-AVL-002 — Jurado não associado

Esperado:

```text
403 Forbidden
```

---

## TST-AVL-003 — Critério inexistente

Esperado:

```text
404 Not Found
```

---

## TST-AVL-004 — Equipe inexistente

Esperado:

```text
404 Not Found
```

---

## TST-AVL-005 — Nota inválida

Esperado:

```text
400 Bad Request
```

---

## TST-AVL-006 — Múltiplos jurados avaliam mesma equipe

Esperado:

```text
201 Created
```

Validar:

```text
[ ] avaliações independentes preservadas
```

---

# 32. RESULTADOS

## TST-RES-001 — Registrar resultado

Esperado:

```text
201 Created
```

---

## TST-RES-002 — Resultado para equipe inexistente

Esperado:

```text
404 Not Found
```

---

## TST-RES-003 — Atualizar resultado

Esperado:

```text
200 OK
```

---

## TST-RES-004 — Registrar empate permitido

Esperado:

```text
201 Created
```

---

# 33. RANKING

## TST-RKG-001 — Consultar ranking publicado

Esperado:

```text
200 OK
```

---

## TST-RKG-002 — Consultar ranking oculto como participante

Esperado:

```text
403 Forbidden
```

ou resposta sem posições públicas, conforme contrato final.

---

## TST-RKG-003 — Publicar ranking

Esperado:

```text
200 OK
```

---

## TST-RKG-004 — Ocultar ranking

Esperado:

```text
200 OK
```

---

## TST-RKG-005 — Empate permitido

Validar:

```text
[ ] posições respeitam configuração do evento
```

---

# 34. EMBLEMAS

## TST-EMB-001 — Criar emblema

Esperado:

```text
201 Created
```

---

## TST-EMB-002 — Nome ausente

Esperado:

```text
400 Bad Request
```

---

## TST-EMB-003 — Conceder emblema

Esperado:

```text
201 Created
```

---

## TST-EMB-004 — Conceder a usuário inexistente

Esperado:

```text
404 Not Found
```

---

## TST-EMB-005 — Concessão duplicada

Esperado:

```text
409 Conflict
```

se o mesmo emblema não puder ser concedido duas vezes.

---

## TST-EMB-006 — Consultar emblemas do usuário

Esperado:

```text
200 OK
```

---

# 35. CERTIFICADOS

## TST-CER-001 — Criar certificado

Esperado:

```text
201 Created
```

---

## TST-CER-002 — Emitir certificado

Esperado:

```text
201 Created
```

---

## TST-CER-003 — Emitir para usuário inexistente

Esperado:

```text
404 Not Found
```

---

## TST-CER-004 — Consultar certificados do usuário

Esperado:

```text
200 OK
```

---

## TST-CER-005 — Verificar histórico após encerramento do evento

Validar:

```text
[ ] certificado continua disponível
```

---

# 36. PATROCINADORES

## TST-PAT-001 — Associar patrocinador

Esperado:

```text
201 Created
```

---

## TST-PAT-002 — Empresa inexistente

Esperado:

```text
404 Not Found
```

---

## TST-PAT-003 — Patrocinador duplicado

Esperado:

```text
409 Conflict
```

---

## TST-PAT-004 — Listar patrocinadores

Esperado:

```text
200 OK
```

---

## TST-PAT-005 — Remover patrocinador

Esperado:

```text
204 No Content
```

---

# 37. ESTANDES

## TST-EST-001 — Criar estande

Esperado:

```text
201 Created
```

---

## TST-EST-002 — Empresa inexistente

Esperado:

```text
404 Not Found
```

---

## TST-EST-003 — Evento inexistente

Esperado:

```text
404 Not Found
```

---

## TST-EST-004 — Atualizar estande

Esperado:

```text
200 OK
```

---

# 38. OFERTAS

## TST-OFE-001 — Criar oferta

Esperado:

```text
201 Created
```

---

## TST-OFE-002 — Data final anterior à inicial

Esperado:

```text
400 Bad Request
```

---

## TST-OFE-003 — Consultar oferta

Esperado:

```text
200 OK
```

---

# 39. COMUNICADOS

## TST-COM-001 — Criar comunicado geral

Esperado:

```text
201 Created
```

---

## TST-COM-002 — Criar comunicado por atividade

Esperado:

```text
201 Created
```

---

## TST-COM-003 — Criar comunicado para recurso inexistente

Esperado:

```text
404 Not Found
```

---

## TST-COM-004 — Usuário sem permissão cria comunicado

Esperado:

```text
403 Forbidden
```

---

# 40. NOTIFICAÇÕES

## TST-NTF-001 — Listar notificações

Esperado:

```text
200 OK
```

---

## TST-NTF-002 — Filtrar notificações não lidas

Esperado:

```text
200 OK
```

---

## TST-NTF-003 — Marcar como lida

Esperado:

```text
200 OK
```

---

## TST-NTF-004 — Notificação inexistente

Esperado:

```text
404 Not Found
```

---

## TST-NTF-005 — Marcar todas como lidas

Esperado:

```text
200 OK
```

---

## TST-NTF-006 — Alterar preferências

Esperado:

```text
200 OK
```

---

## TST-NTF-007 — Desabilitar promocional

Validar:

```text
[ ] promocional = false
```

---

## TST-NTF-008 — Tentar desabilitar notificação essencial

Validar:

```text
[ ] regra de notificação essencial permanece respeitada
```

---

# 41. HISTÓRICO DO USUÁRIO

## TST-HIS-001 — Consultar eventos participados

Esperado:

```text
200 OK
```

---

## TST-HIS-002 — Consultar hackathons participados

Esperado:

```text
200 OK
```

---

## TST-HIS-003 — Consultar resultados

Esperado:

```text
200 OK
```

---

## TST-HIS-004 — Evento cancelado continua no histórico

Validar:

```text
[ ] evento aparece
[ ] status CANCELADO
```

---

## TST-HIS-005 — Emblema continua após evento encerrado

Validar:

```text
[ ] emblema continua no perfil
```

---

# 42. PAGINAÇÃO

## TST-PAG-001 — Primeira página

```text
?page=1&limit=10
```

Validar:

```text
[ ] no máximo 10 registros
```

---

## TST-PAG-002 — Segunda página

Validar:

```text
[ ] registros diferentes da primeira página
```

---

## TST-PAG-003 — Página inexistente

Esperado:

```text
200 OK
```

com lista vazia, conforme contrato adotado.

---

## TST-PAG-004 — Limite inválido

```text
limit=-1
```

Esperado:

```text
400 Bad Request
```

---

# 43. FILTROS

## TST-FIL-001 — Filtro válido

Esperado:

```text
200 OK
```

---

## TST-FIL-002 — Combinação de filtros

Exemplo:

```text
modalidade=PRESENCIAL
tipoFinanceiro=GRATUITO
```

Validar:

```text
[ ] todos os resultados atendem aos dois filtros
```

---

## TST-FIL-003 — Filtro sem resultados

Esperado:

```text
200 OK
```

com lista vazia.

---

# 44. AUTORIZAÇÃO

## TST-AUT-001 — Endpoint autenticado sem token

Esperado:

```text
401 Unauthorized
```

---

## TST-AUT-002 — Usuário tenta operação de administrador

Esperado:

```text
403 Forbidden
```

---

## TST-AUT-003 — Empresa tenta editar evento de outra empresa

Esperado:

```text
403 Forbidden
```

---

## TST-AUT-004 — Usuário tenta alterar equipe sem permissão

Esperado:

```text
403 Forbidden
```

---

## TST-AUT-005 — Jurado não associado tenta avaliar

Esperado:

```text
403 Forbidden
```

---

# 45. RECURSOS INEXISTENTES

Todos os endpoints que recebem identificadores devem ser testados com IDs inexistentes.

Exemplos:

```text
usuarioId inexistente

empresaId inexistente

eventoId inexistente

atividadeId inexistente

hackathonId inexistente

equipeId inexistente

submissaoId inexistente

emblemaId inexistente

certificadoId inexistente
```

Resultado esperado:

```text
404 Not Found
```

---

# 46. BODY INVÁLIDO

Todos os endpoints `POST` e `PATCH` devem ser testados com:

```text
[ ] body vazio
[ ] JSON inválido
[ ] campo obrigatório ausente
[ ] campo com tipo incorreto
[ ] valor fora do permitido
```

Resultado esperado:

```text
400 Bad Request
```

---

# 47. CONCORRÊNCIA — TESTES MANUAIS

Alguns testes podem ser simulados usando duas abas do Postman.

## TST-CON-001 — Última vaga do evento

Preparação:

```text
capacidade = 1
vagas disponíveis = 1
```

Executar quase simultaneamente:

```text
Usuário A → inscrição
Usuário B → inscrição
```

Validar:

```text
[ ] apenas uma inscrição confirmada ocupa a última vaga
[ ] capacidade não ultrapassada
```

---

## TST-CON-002 — Última vaga de equipe

Preparação:

```text
máximo da equipe = 5
membros atuais = 4
```

Aceitar dois convites próximos.

Validar:

```text
[ ] equipe termina com no máximo 5 membros
```

---

# 48. TESTE DE SUBMISSÃO NO PRAZO

## TST-TMP-001 — Antes do prazo

Esperado:

```text
201 Created
```

---

## TST-TMP-002 — Após o prazo

Esperado:

```text
409 Conflict
```

---

# 49. TESTES DE ESTADO

## TST-ESTADO-001 — Evento cancelado

Validar:

```text
[ ] não tratado como ativo
[ ] continua no histórico
```

---

## TST-ESTADO-002 — Inscrição rejeitada

Validar:

```text
[ ] não aparece como confirmada
```

---

## TST-ESTADO-003 — Equipe desclassificada

Validar:

```text
[ ] não aparece como competidora válida
```

---

## TST-ESTADO-004 — Lista de espera

Validar:

```text
[ ] usuário não aparece como confirmado
```

---

# 50. TESTES DE HISTÓRICO

## TST-HIST-001 — Versões de submissão

Criar:

```text
Versão 1
Versão 2
Versão 3
```

Validar:

```text
[ ] três versões continuam disponíveis
```

---

## TST-HIST-002 — Emblema concedido

Depois de encerrar evento:

```text
[ ] emblema continua no perfil
```

---

## TST-HIST-003 — Certificado emitido

Depois de encerrar evento:

```text
[ ] certificado continua disponível
```

---

# 51. TESTES DE RESPOSTA

Todos os endpoints devem ser verificados quanto a:

```text
[ ] JSON válido
[ ] sucesso consistente
[ ] campo dados quando aplicável
[ ] erro padronizado
[ ] mensagem compreensível
[ ] nenhum dado sensível exposto
```

---

# 52. SCRIPT DE TESTE NO POSTMAN

Exemplo para validar status:

```javascript
pm.test("Status deve ser 200", function () {
  pm.response.to.have.status(200);
});
```

Para criação:

```javascript
pm.test("Status deve ser 201", function () {
  pm.response.to.have.status(201);
});
```

---

# 53. Validar JSON

```javascript
pm.test("Resposta deve ser JSON", function () {
  pm.response.to.be.json;
});
```

---

# 54. Validar campo de sucesso

```javascript
pm.test("Sucesso deve ser true", function () {
  const json = pm.response.json();

  pm.expect(json.sucesso).to.eql(true);
});
```

---

# 55. Validar ID retornado

```javascript
pm.test("Deve retornar ID", function () {
  const json = pm.response.json();

  pm.expect(json.dados.id).to.exist;
});
```

---

# 56. Salvar ID em Variável

Depois de cadastrar usuário:

```javascript
const json = pm.response.json();

pm.environment.set(
  "usuarioId",
  json.dados.id
);
```

Depois usar:

```text
{{usuarioId}}
```

---

# 57. Testar Erro

```javascript
pm.test("Deve retornar erro", function () {

  const json = pm.response.json();

  pm.expect(json.sucesso).to.eql(false);

  pm.expect(json.erro).to.exist;
});
```

---

# 58. Ordem Recomendada de Execução

Os testes devem seguir uma ordem que respeite dependências.

```text
1. Usuarios
2. Auth
3. Perfis
4. Empresas
5. Verificacoes
6. Eventos
7. Organizadores
8. Inscricoes
9. Trilhas
10. Atividades
11. Checkins
12. Hackathons
13. Fases
14. Desafios
15. Equipes
16. Convites
17. Solicitacoes
18. Submissoes
19. Criterios
20. Jurados
21. Avaliacoes
22. Resultados
23. Ranking
24. Emblemas
25. Certificados
26. Patrocinadores
27. Estandes
28. Ofertas
29. Comunicados
30. Notificacoes
```

---

# 59. Critério de Conclusão de Endpoint

Um endpoint somente deve ser considerado concluído quando:

```text
[ ] cenário válido passou

[ ] campos obrigatórios foram testados

[ ] entrada inválida foi testada

[ ] recurso inexistente foi testado

[ ] conflitos foram testados

[ ] permissões foram testadas quando aplicável

[ ] regra de negócio foi testada

[ ] status HTTP está correto

[ ] resposta está correta

[ ] persistência foi validada
```

---

# 60. Critério de Conclusão da Sprint

Antes de avançar:

```text
[ ] Todos os endpoints obrigatórios da Sprint funcionam

[ ] Todos os testes de sucesso passaram

[ ] Todos os principais testes de erro passaram

[ ] Regras de negócio foram verificadas

[ ] Não existem erros bloqueadores conhecidos

[ ] Collection do Postman está atualizada
```

---

# 61. Resumo das Categorias de Teste

Para cada módulo, considerar:

```text
SUCESSO

VALIDAÇÃO

DUPLICIDADE

RECURSO INEXISTENTE

AUTENTICAÇÃO

AUTORIZAÇÃO

REGRA DE NEGÓCIO

MUDANÇA DE ESTADO

HISTÓRICO

CONCORRÊNCIA

PAGINAÇÃO

FILTROS
```

---

# 62. Regra Final

O objetivo dos testes com Postman não é apenas verificar se o endpoint responde.

O teste deve confirmar:

```text
requisição correta
+
resposta correta
+
regra correta
+
estado correto
+
dados corretos
```

Uma resposta `200 OK` não significa que a funcionalidade está correta se o resultado produzido violar uma regra de negócio.
