# GUIA DO CICLO DE UM ENDPOINT

## 1. Objetivo do Documento

Este documento explica, de forma prática, como um endpoint deve funcionar dentro da arquitetura do projeto.

O objetivo é orientar integrantes que ainda não possuem experiência com APIs ou separação de responsabilidades.

O exemplo principal será:

```text
Cadastrar usuário
```

Fluxo:

```text
POST /api/usuarios
```

Este documento mostra:

* o que é Route Handler;
* o que é Controller;
* o que é DTO;
* o que é Validator;
* o que é Service;
* o que é Repository;
* o que é Entity / Model;
* como essas partes se conectam;
* como construir um endpoint completo;
* quais erros evitar.

---

# 2. Visão Geral do Ciclo

Um endpoint não deve ser entendido apenas como uma função que recebe dados e salva no banco.

O fluxo ideal será:

```text
CLIENTE
   ↓
REQUISIÇÃO HTTP
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
MODEL / ENTITY
   ↓
BANCO DE DADOS
   ↓
REPOSITORY
   ↓
SERVICE
   ↓
ROUTE HANDLER
   ↓
RESPOSTA HTTP
   ↓
CLIENTE
```

---

# 3. O que é Endpoint

Endpoint é um ponto de acesso da API.

Exemplo:

```text
POST /api/usuarios
```

Esse endpoint representa uma ação específica:

```text
Cadastrar usuário
```

Um endpoint normalmente é composto por:

```text
Método HTTP
+
Rota
```

Exemplo:

```text
POST /api/usuarios
```

Onde:

```text
POST
```

representa a ação.

E:

```text
/api/usuarios
```

representa o recurso.

---

# 4. Métodos HTTP mais utilizados

## GET

Utilizado para buscar informações.

Exemplo:

```text
GET /api/usuarios/10
```

Objetivo:

```text
Buscar usuário 10
```

---

## POST

Utilizado normalmente para criar um novo recurso.

Exemplo:

```text
POST /api/usuarios
```

Objetivo:

```text
Criar usuário
```

---

## PATCH

Utilizado para atualização parcial.

Exemplo:

```text
PATCH /api/usuarios/10
```

Objetivo:

```text
Alterar algumas informações do usuário 10
```

---

## DELETE

Utilizado para remover ou cancelar um recurso quando aplicável.

Exemplo:

```text
DELETE /api/inscricoes/50
```

---

# 5. Controller e Route Handler

Em projetos Java com Spring Boot, seria comum encontrar:

```text
UsuarioController
```

No Next.js, o projeto utilizará principalmente:

```text
Route Handler
```

Portanto, para este projeto:

```text
Controller
≈
Route Handler
```

Eles possuem funções conceitualmente semelhantes na entrada HTTP.

---

# 6. Responsabilidade do Route Handler

O Route Handler deve cuidar principalmente da camada HTTP.

Ele deve:

```text
receber requisição
↓
ler parâmetros
↓
ler body
↓
acionar validação
↓
chamar Service
↓
receber resultado
↓
retornar resposta HTTP
```

Exemplo conceitual:

```javascript
export async function POST(request) {
  const body = await request.json();

  const resultado = await usuarioService.cadastrar(body);

  return Response.json(resultado, {
    status: 201
  });
}
```

Esse exemplo ainda está simplificado.

---

# 7. O que não colocar no Route Handler

Evitar fazer isto:

```text
Route Handler
│
├── verifica todos os campos
├── verifica se email existe
├── cria entidade
├── consulta banco
├── cria perfil
├── salva tudo
├── define regra de negócio
└── responde
```

Isso deixa o endpoint difícil de:

* entender;
* manter;
* corrigir;
* testar;
* reutilizar.

O Route Handler deve permanecer pequeno.

---

# 8. DTO

DTO significa:

```text
Data Transfer Object
```

Ele representa os dados que entram ou saem de determinada operação.

---

# 9. Por que utilizar DTO

Imagine uma entidade de usuário:

```text
Usuario

id
nome
email
senhaHash
status
createdAt
updatedAt
```

Para cadastrar um usuário, o cliente não deve enviar tudo isso.

Ele deveria enviar apenas:

```text
nome
email
senha
```

Portanto:

```text
CreateUsuarioDTO
```

representa:

```text
nome
email
senha
```

---

# 10. DTO não é Entity

Isso é importante.

```text
DTO
≠
Entity
```

Exemplo:

## DTO

```text
CreateUsuarioDTO

nome
email
senha
```

## Entity

```text
Usuario

id
nome
email
senhaHash
status
createdAt
updatedAt
```

A entidade possui informações que não devem ser controladas diretamente pelo cliente.

---

# 11. DTO de Entrada

DTO de entrada representa informações recebidas.

Exemplo:

```javascript
const createUsuarioDTO = {
  nome,
  email,
  senha
};
```

Conceitualmente:

```text
CreateUsuarioDTO
```

---

# 12. DTO de Saída

Também podemos utilizar um DTO para resposta.

Exemplo:

```text
UsuarioResponseDTO

id
nome
email
```

A resposta não deve necessariamente devolver a entidade inteira.

Por exemplo:

```text
senhaHash
```

não deve ser devolvida.

---

# 13. Validator

Validator é responsável por validar a estrutura dos dados recebidos.

Exemplo:

```text
nome existe?
email existe?
senha existe?
email está em formato válido?
```

---

# 14. Exemplo de validação

Entrada:

```json
{
  "nome": "",
  "email": "abc",
  "senha": ""
}
```

Validator deve identificar problemas como:

```text
nome obrigatório
email inválido
senha obrigatória
```

---

# 15. Validator não é regra de negócio

Essa diferença é essencial.

## Validator

Responde perguntas como:

```text
email está vazio?
email possui formato válido?
nome foi informado?
```

## Service / Regra de negócio

Responde perguntas como:

```text
email já está cadastrado?
usuário pode realizar essa ação?
evento possui vaga?
empresa está verificada?
```

Portanto:

```text
VALIDAÇÃO DE FORMATO
≠
REGRA DE NEGÓCIO
```

---

# 16. Service

O Service representa o caso de uso.

Exemplo:

```text
UsuarioService
```

Pode possuir operação:

```text
cadastrarUsuario()
```

---

# 17. Responsabilidade do Service

O Service deve coordenar o processo.

No cadastro:

```text
receber dados válidos
↓
verificar email duplicado
↓
preparar usuário
↓
solicitar persistência
↓
receber usuário salvo
↓
retornar resultado
```

---

# 18. Exemplo de Service

Exemplo simplificado:

```javascript
export async function cadastrarUsuario(dados) {

  const usuarioExistente =
    await usuarioRepository.buscarPorEmail(dados.email);

  if (usuarioExistente) {
    throw new Error("EMAIL_JA_CADASTRADO");
  }

  const novoUsuario = {
    nome: dados.nome,
    email: dados.email
  };

  const usuarioSalvo =
    await usuarioRepository.salvar(novoUsuario);

  return usuarioSalvo;
}
```

Esse código é apenas didático.

Detalhes como senha serão definidos posteriormente conforme as decisões técnicas do projeto.

---

# 19. Repository

Repository é a camada responsável pelo acesso aos dados.

Exemplo:

```text
UsuarioRepository
```

Ele pode possuir operações como:

```text
buscarPorEmail()

buscarPorId()

salvar()

atualizar()
```

---

# 20. Exemplo de Repository

Exemplo conceitual:

```javascript
export async function buscarPorEmail(email) {
  // consulta no banco
}

export async function salvar(usuario) {
  // salva no banco
}
```

A implementação real dependerá do banco e ORM escolhidos.

---

# 21. Por que usar Repository

Sem Repository:

```text
Service
↓
faz consultas diretamente no banco
```

Com Repository:

```text
Service
↓
Repository
↓
Banco
```

Isso deixa cada parte com uma responsabilidade mais clara.

---

# 22. Repository não deve conter regra de negócio

Exemplo ruim:

```javascript
async function salvarUsuario(usuario) {

  if (usuario.idade < 18) {
    throw new Error("NAO_PODE");
  }

  // salva
}
```

Se essa fosse uma regra de negócio, ela deveria ficar em camada apropriada, normalmente no Service.

Repository deve cuidar principalmente de persistência.

---

# 23. Model / Entity

Entity ou Model representa um conceito persistido do sistema.

Exemplo:

```text
Usuario
```

Possíveis atributos:

```text
id
nome
email
senhaHash
status
dataCriacao
dataAtualizacao
```

---

# 24. Responsabilidade da Entity

A Entity representa:

```text
o que existe no domínio
```

Exemplo:

```text
Usuario
Evento
Empresa
Equipe
Submissao
```

Essas entidades já foram descritas no documento:

```text
MODELO-DE-DADOS.md
```

---

# 25. Fluxo Completo — Cadastro de Usuário

Agora vamos juntar tudo.

O cliente envia:

```text
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

---

# 26. Etapa 1 — Route Handler

Arquivo conceitual:

```text
src/app/api/usuarios/route.js
```

Exemplo:

```javascript
export async function POST(request) {

  const body = await request.json();

  const resultado =
    await cadastrarUsuario(body);

  return Response.json(resultado, {
    status: 201
  });
}
```

O Route Handler recebe a requisição.

---

# 27. Etapa 2 — Criar DTO

Dados recebidos:

```javascript
const createUsuarioDTO = {
  nome: body.nome,
  email: body.email,
  senha: body.senha
};
```

Com isso, trabalhamos apenas com os dados esperados.

---

# 28. Etapa 3 — Validar DTO

Exemplo conceitual:

```javascript
function validarCreateUsuario(dados) {

  if (!dados.nome) {
    throw new Error("NOME_OBRIGATORIO");
  }

  if (!dados.email) {
    throw new Error("EMAIL_OBRIGATORIO");
  }

  if (!dados.senha) {
    throw new Error("SENHA_OBRIGATORIA");
  }
}
```

Depois:

```javascript
validarCreateUsuario(createUsuarioDTO);
```

Se os dados forem inválidos:

```text
a operação não continua
```

---

# 29. Etapa 4 — Chamar o Service

Após a validação:

```javascript
const usuario =
  await usuarioService.cadastrar(createUsuarioDTO);
```

Agora começa o caso de uso.

---

# 30. Etapa 5 — Verificar Regra de Negócio

O Service precisa verificar:

```text
Já existe usuário com esse email?
```

Então:

```javascript
const usuarioExistente =
  await usuarioRepository.buscarPorEmail(dados.email);
```

---

# 31. Etapa 6 — E-mail já existe

Caso exista:

```javascript
if (usuarioExistente) {
  throw new Error("EMAIL_JA_CADASTRADO");
}
```

Isso é uma regra de negócio.

Não é apenas validação estrutural.

---

# 32. Etapa 7 — Preparar Entity

Conceitualmente:

```javascript
const usuario = {
  nome: dados.nome,
  email: dados.email
};
```

Detalhes definitivos dependerão da persistência escolhida.

---

# 33. Etapa 8 — Repository salva

O Service chama:

```javascript
const usuarioSalvo =
  await usuarioRepository.salvar(usuario);
```

Fluxo:

```text
Service
   ↓
Repository
   ↓
Banco de dados
```

---

# 34. Etapa 9 — Banco retorna dados

Exemplo conceitual:

```text
id: 10
nome: Leonardo
email: leonardo@email.com
```

---

# 35. Etapa 10 — Repository devolve ao Service

Fluxo:

```text
Banco
   ↓
Repository
   ↓
Service
```

O Service recebe o usuário persistido.

---

# 36. Etapa 11 — Criar Response DTO

Não devemos necessariamente devolver todos os dados internos.

Exemplo:

```javascript
const responseDTO = {
  id: usuarioSalvo.id,
  nome: usuarioSalvo.nome,
  email: usuarioSalvo.email
};
```

---

# 37. Etapa 12 — Resposta HTTP

Route Handler retorna:

```http
201 Created
```

Body:

```json
{
  "id": 10,
  "nome": "Leonardo",
  "email": "leonardo@email.com"
}
```

---

# 38. Fluxo Visual Completo

```text
POST /api/usuarios
        ↓
Route Handler
        ↓
CreateUsuarioDTO
        ↓
Validator
        ↓
UsuarioService
        ↓
UsuarioRepository.buscarPorEmail()
        ↓
Banco
        ↓
email existe?
   ├── SIM
   │     ↓
   │  erro
   │
   └── NÃO
         ↓
    preparar Usuario
         ↓
UsuarioRepository.salvar()
         ↓
       Banco
         ↓
 Usuario persistido
         ↓
UsuarioResponseDTO
         ↓
 Route Handler
         ↓
  201 Created
```

---

# 39. Estrutura Conceitual dos Arquivos

Exemplo:

```text
src/
│
├── app/
│   └── api/
│       └── usuarios/
│           └── route.js
│
├── dto/
│   └── usuario/
│       ├── createUsuarioDTO.js
│       └── usuarioResponseDTO.js
│
├── validators/
│   └── usuario/
│       └── createUsuarioValidator.js
│
├── services/
│   └── usuario/
│       └── usuarioService.js
│
├── repositories/
│   └── usuario/
│       └── usuarioRepository.js
│
└── models/
    └── usuario.js
```

Essa estrutura poderá sofrer ajustes durante a implementação.

---

# 40. Exemplo de Route Handler mais Completo

```javascript
import { validarCreateUsuario } from "@/validators/usuario/createUsuarioValidator";
import { usuarioService } from "@/services/usuario/usuarioService";

export async function POST(request) {

  try {

    const body = await request.json();

    const dto = {
      nome: body.nome,
      email: body.email,
      senha: body.senha
    };

    validarCreateUsuario(dto);

    const usuario =
      await usuarioService.cadastrar(dto);

    return Response.json(usuario, {
      status: 201
    });

  } catch (error) {

    return Response.json(
      {
        erro: error.message
      },
      {
        status: 400
      }
    );
  }
}
```

Esse exemplo é didático.

O tratamento definitivo de erros será padronizado posteriormente.

---

# 41. Exemplo de Validator

```javascript
export function validarCreateUsuario(dados) {

  if (!dados.nome) {
    throw new Error("NOME_OBRIGATORIO");
  }

  if (!dados.email) {
    throw new Error("EMAIL_OBRIGATORIO");
  }

  if (!dados.senha) {
    throw new Error("SENHA_OBRIGATORIA");
  }

  if (!dados.email.includes("@")) {
    throw new Error("EMAIL_INVALIDO");
  }
}
```

Posteriormente pode ser utilizada uma biblioteca especializada de validação.

---

# 42. Exemplo de Service

```javascript
import { usuarioRepository } from "@/repositories/usuario/usuarioRepository";

async function cadastrar(dados) {

  const existente =
    await usuarioRepository.buscarPorEmail(dados.email);

  if (existente) {
    throw new Error("EMAIL_JA_CADASTRADO");
  }

  const usuario = {
    nome: dados.nome,
    email: dados.email
  };

  return usuarioRepository.salvar(usuario);
}

export const usuarioService = {
  cadastrar
};
```

---

# 43. Exemplo de Repository

```javascript
async function buscarPorEmail(email) {

  // implementação futura
  // depende do ORM e banco escolhidos

}

async function salvar(usuario) {

  // implementação futura
  // depende do ORM e banco escolhidos

}

export const usuarioRepository = {
  buscarPorEmail,
  salvar
};
```

---

# 44. Por que o Repository está incompleto no exemplo

Porque ainda não foram escolhidos:

```text
Banco
ORM
```

Portanto, não devemos inventar código de persistência antes da decisão.

Quando essas tecnologias forem escolhidas, apenas essa camada será adaptada conforme necessário.

---

# 45. Onde cada responsabilidade deve ficar

## Route Handler

Pergunta:

```text
Como a requisição HTTP será recebida e respondida?
```

---

## DTO

Pergunta:

```text
Quais dados entram ou saem?
```

---

## Validator

Pergunta:

```text
Esses dados possuem formato válido?
```

---

## Service

Pergunta:

```text
O que precisa acontecer neste caso de uso?
```

---

## Repository

Pergunta:

```text
Quais dados precisam ser consultados ou persistidos?
```

---

## Entity / Model

Pergunta:

```text
Qual entidade do domínio está sendo representada?
```

---

# 46. Outro Exemplo — Inscrição em Evento

Fluxo:

```text
POST /api/eventos/:id/inscricoes
        ↓
Route Handler
        ↓
InscricaoDTO
        ↓
Validator
        ↓
InscricaoService
        ↓
verificar usuário
        ↓
verificar evento
        ↓
verificar inscrição existente
        ↓
verificar vagas
        ↓
InscricaoRepository
        ↓
Banco
```

Perceba que a lógica:

```text
evento possui vaga?
```

não deveria ficar dentro do Route Handler.

---

# 47. Outro Exemplo — Criar Equipe

```text
POST /api/hackathons/:id/equipes
        ↓
Route Handler
        ↓
CreateEquipeDTO
        ↓
Validator
        ↓
EquipeService
        ↓
verificar hackathon
        ↓
verificar participação por equipe
        ↓
criar equipe
        ↓
adicionar criador como líder
        ↓
Repository
        ↓
Banco
```

---

# 48. Regra Prática para Criar um Endpoint

Antes de começar a programar, responda:

```text
1. Qual funcionalidade estou implementando?

2. Qual é o método HTTP?

3. Qual é a rota?

4. Quais dados entram?

5. Qual DTO representa esses dados?

6. Quais validações de formato existem?

7. Quais regras de negócio precisam ser verificadas?

8. Qual Service representa o caso de uso?

9. Quais dados precisam ser buscados?

10. Qual Repository deve realizar essas consultas?

11. Qual entidade será criada ou alterada?

12. O que deve ser devolvido?

13. Qual status HTTP representa o resultado?

14. Quais erros podem acontecer?

15. Como isso será testado no Postman?
```

---

# 49. Checklist de Implementação de Endpoint

Antes de considerar um endpoint pronto:

```text
[ ] rota criada

[ ] método HTTP correto

[ ] DTO definido

[ ] validação criada

[ ] Service criado

[ ] regras de negócio verificadas

[ ] Repository criado

[ ] persistência funcionando

[ ] Response DTO definido quando necessário

[ ] códigos HTTP definidos

[ ] erros tratados

[ ] teste de sucesso no Postman

[ ] teste de erro no Postman
```

---

# 50. Erro Comum — Colocar tudo no Route Handler

Evitar:

```javascript
export async function POST(request) {

  const body = await request.json();

  // valida

  // consulta usuário

  // consulta evento

  // verifica regra

  // salva no banco

  // atualiza outro registro

  // cria resposta

}
```

Isso funciona em projetos muito pequenos, mas tende a dificultar a manutenção conforme o sistema cresce.

---

# 51. Erro Comum — Service com HTTP

Evitar:

```javascript
return Response.json(...)
```

dentro de Service.

O Service deve devolver:

```text
dados
```

ou:

```text
resultado
```

O Route Handler transforma isso em resposta HTTP.

---

# 52. Erro Comum — Repository com regra de negócio

Evitar:

```text
Repository decide se empresa pode criar evento
```

Preferir:

```text
Service verifica empresa
↓
Repository apenas fornece os dados necessários
```

---

# 53. Erro Comum — Usar Entity diretamente como entrada

Evitar receber:

```json
{
  "id": 10,
  "nome": "Leonardo",
  "email": "email@email.com",
  "status": "ADMIN",
  "createdAt": "...",
  "updatedAt": "..."
}
```

se o endpoint necessita apenas:

```json
{
  "nome": "Leonardo",
  "email": "email@email.com",
  "senha": "..."
}
```

O DTO limita claramente o contrato.

---

# 54. Erro Comum — Expor dados internos

Uma entidade pode possuir:

```text
senhaHash
```

Isso não significa que esse campo deva aparecer na resposta.

Por isso:

```text
ENTITY
≠
RESPONSE DTO
```

---

# 55. Erro Comum — Duplicar Regra

Imagine que a regra seja:

```text
Empresa precisa estar verificada para criar evento.
```

Não devemos implementar essa lógica separadamente em vários lugares:

```text
Route A

Route B

Route C
```

Preferir centralizá-la em uma camada apropriada.

---

# 56. Como Pensar no Service

Pense no Service como uma ação do sistema.

Exemplos:

```text
CadastrarUsuario

CriarEvento

InscreverUsuario

CancelarInscricao

CriarEquipe

AceitarConvite

EnviarSubmissao

ConcederEmblema
```

Isso ajuda a evitar Services genéricos demais.

---

# 57. Como Pensar no Repository

Pense no Repository como perguntas e operações de dados.

Exemplos:

```text
buscarUsuarioPorEmail

buscarEventoPorId

buscarInscricaoDoUsuario

contarParticipantesConfirmados

buscarEquipe

salvarSubmissao
```

---

# 58. Exemplo de Separação Correta

## Route

```text
Receba os dados.
```

## Validator

```text
Os dados têm formato válido?
```

## Service

```text
Esse cadastro pode acontecer?
```

## Repository

```text
O e-mail já existe?
Salve o usuário.
```

## Entity

```text
Este é o usuário.
```

---

# 59. Fluxo Mental Simplificado

Quando estiver desenvolvendo:

```text
REQUISIÇÃO
↓
ENTRADA
↓
VALIDAÇÃO
↓
REGRA
↓
DADOS
↓
RESPOSTA
```

Mapeando para o projeto:

```text
Route Handler
↓
DTO
↓
Validator
↓
Service
↓
Repository
↓
Response
```

---

# 60. Relação com os Outros Documentos

Antes de implementar um endpoint, consultar:

```text
REQUISITOS.md
```

para saber:

```text
o que precisa existir
```

Depois:

```text
REGRAS-DE-NEGOCIO.md
```

para saber:

```text
quais condições precisam ser respeitadas
```

Depois:

```text
MODELO-DE-DADOS.md
```

para saber:

```text
quais entidades participam
```

Depois:

```text
API.md
```

para saber:

```text
qual rota e contrato devem ser implementados
```

Depois deste guia:

```text
GUIA-CICLO-ENDPOINT.md
```

para saber:

```text
como organizar o código
```

E finalmente:

```text
TESTES-POSTMAN.md
```

para saber:

```text
como validar o endpoint
```

---

# 61. Fluxo de Trabalho Recomendado para a Equipe

```text
1. Escolher item da Sprint

2. Encontrar requisito

3. Ler regra de negócio relacionada

4. Identificar entidades

5. Consultar contrato da API

6. Criar DTO

7. Criar Validator

8. Criar Service

9. Criar Repository

10. Criar Route Handler

11. Executar endpoint

12. Testar no Postman

13. Corrigir erros

14. Marcar item como concluído
```

---

# 62. Regra Principal

O objetivo da separação não é criar a maior quantidade possível de arquivos.

O objetivo é manter responsabilidades claras.

Se uma classe, função ou arquivo não possuir responsabilidade clara, a separação deve ser reconsiderada.

A equipe deve evitar tanto:

```text
tudo em um arquivo
```

quanto:

```text
um arquivo diferente para cada linha de código
```

O equilíbrio deve favorecer:

```text
clareza
+
manutenção
+
facilidade de aprendizado
+
consistência
```
