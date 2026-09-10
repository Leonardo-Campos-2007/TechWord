# TESTES DE API COM POSTMAN

## 1. Objetivo

Este documento orienta a equipe na validação dos endpoints utilizando Postman.

Cada funcionalidade só deve ser considerada concluída após testar:

- cenário de sucesso;
- dados inválidos;
- recursos inexistentes;
- duplicidade quando aplicável;
- permissões quando aplicável.

## 2. Padrão de Teste

Para cada endpoint registrar:

```text
Endpoint:
Método:
Headers:
Body:
Status esperado:
Resposta esperada:
Resultado:
```

## 3. Exemplo — Cadastro de Usuário

### Cenário 1 — Cadastro válido

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
Status: 201 Created
```

Checklist:

```text
[ ] Usuário criado
[ ] ID retornado
[ ] Nome retornado
[ ] E-mail retornado
[ ] Senha não retornada
```

### Cenário 2 — E-mail duplicado

Enviar novamente o mesmo e-mail.

Esperado:

```text
409 Conflict
```

### Cenário 3 — E-mail inválido

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

### Cenário 4 — Campo obrigatório ausente

```json
{
  "email": "leonardo@email.com",
  "senha": "Senha123"
}
```

Esperado:

```text
400 Bad Request
```

## 4. Checklist Geral por Endpoint

```text
[ ] Método correto
[ ] URL correta
[ ] Headers corretos
[ ] Body correto
[ ] Status esperado
[ ] Resposta esperada
[ ] Cenário válido
[ ] Campo obrigatório ausente
[ ] Formato inválido
[ ] Recurso inexistente
[ ] Duplicidade
[ ] Regra de negócio
```

## 5. Organização de Collections

Sugestão:

```text
API Eventos
├── Auth
├── Usuarios
├── Empresas
├── Eventos
├── Inscricoes
├── Atividades
├── Hackathons
├── Equipes
├── Submissoes
├── Ranking
├── Emblemas
├── Certificados
└── Notificacoes
```

## 6. Regra para Avançar de Sprint

Endpoints definidos na Sprint devem possuir os testes mínimos documentados e executados no Postman antes da Sprint seguinte.
