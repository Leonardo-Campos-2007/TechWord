# MAPA DA FASE 1

## 1. Objetivo do Documento

Este documento apresenta o mapa estrutural da primeira fase de desenvolvimento da plataforma de eventos e hackathons de tecnologia.

O objetivo é orientar a equipe sobre:

* estrutura de pastas;
* organização dos arquivos;
* separação por responsabilidade;
* ordem aproximada de criação;
* localização dos módulos;
* relação entre backend e frontend;
* arquivos que devem ser criados conforme as Sprints avançarem.

Este documento representa um **plano de estrutura**.

Não significa que todos os arquivos devem ser criados de uma só vez.

---

# 2. Estrutura Geral do Projeto

```text
projeto-eventos-hackathons/
│
├── README.md
│
├── package.json
├── package-lock.json
├── next.config.js
├── jsconfig.json
│
├── .env
├── .env.example
├── .gitignore
│
├── docs/
│   ├── REQUISITOS.md
│   ├── REGRAS-DE-NEGOCIO.md
│   ├── MODELO-DE-DADOS.md
│   ├── ARQUITETURA.md
│   ├── GUIA-CICLO-ENDPOINT.md
│   ├── API.md
│   ├── TESTES-POSTMAN.md
│   ├── BACKLOG.md
│   ├── SPRINTS.md
│   └── MAPA-FASE-1.md
│
├── public/
│
└── src/
    │
    ├── app/
    │
    ├── components/
    │
    ├── services/
    │
    ├── repositories/
    │
    ├── models/
    │
    ├── dto/
    │
    ├── validators/
    │
    ├── config/
    │
    └── utils/
```

---

# 3. Diretório `docs`

O diretório:

```text
docs/
```

contém toda a documentação do projeto.

Estrutura:

```text
docs/
│
├── REQUISITOS.md
├── REGRAS-DE-NEGOCIO.md
├── MODELO-DE-DADOS.md
├── ARQUITETURA.md
├── GUIA-CICLO-ENDPOINT.md
├── API.md
├── TESTES-POSTMAN.md
├── BACKLOG.md
├── SPRINTS.md
└── MAPA-FASE-1.md
```

---

# 4. Responsabilidade dos Documentos

## `REQUISITOS.md`

Define:

```text
o que o sistema deve oferecer
```

---

## `REGRAS-DE-NEGOCIO.md`

Define:

```text
condições
restrições
permissões
comportamentos do domínio
```

---

## `MODELO-DE-DADOS.md`

Define:

```text
entidades
atributos
relacionamentos
cardinalidades
estados
```

---

## `ARQUITETURA.md`

Define:

```text
organização técnica
camadas
responsabilidades
fluxo da aplicação
```

---

## `GUIA-CICLO-ENDPOINT.md`

Explica:

```text
Route Handler
DTO
Validator
Service
Repository
Entity
Response
```

---

## `API.md`

Define:

```text
métodos HTTP
rotas
entradas
saídas
status
```

---

## `TESTES-POSTMAN.md`

Define:

```text
cenários de teste
resultado esperado
status esperado
validação manual
```

---

## `BACKLOG.md`

Define:

```text
épicos
histórias
prioridades
dependências
critérios de aceitação
```

---

## `SPRINTS.md`

Define:

```text
ordem de implementação
condições para avançar
```

---

# 5. Diretório `src`

Todo o código principal da aplicação deverá ficar dentro:

```text
src/
```

Estrutura geral:

```text
src/
│
├── app/
├── components/
├── services/
├── repositories/
├── models/
├── dto/
├── validators/
├── config/
└── utils/
```

---

# 6. Diretório `app`

O diretório:

```text
src/app/
```

será utilizado pelo Next.js.

Ele poderá conter:

* páginas;
* layouts;
* rotas;
* API;
* estrutura visual.

Estrutura conceitual:

```text
src/app/
│
├── api/
│
├── login/
├── cadastro/
├── perfil/
├── empresas/
├── eventos/
├── hackathons/
└── ...
```

As páginas devem ser criadas conforme as funcionalidades forem sendo desenvolvidas.

---

# 7. Diretório `api`

As rotas da API ficarão em:

```text
src/app/api/
```

Estrutura prevista:

```text
src/app/api/
│
├── auth/
├── usuarios/
├── perfis/
├── empresas/
├── eventos/
├── inscricoes/
├── trilhas/
├── atividades/
├── hackathons/
├── fases/
├── desafios/
├── equipes/
├── convites-equipe/
├── solicitacoes-equipe/
├── submissoes/
├── versoes-submissao/
├── criterios-avaliacao/
├── avaliacoes/
├── resultados/
├── emblemas/
├── certificados/
├── estandes/
├── ofertas/
├── comunicados/
├── notificacoes/
└── admin/
```

---

# 8. Exemplo de Estrutura de Rota

Para:

```text
POST /api/usuarios
```

estrutura:

```text
src/
└── app/
    └── api/
        └── usuarios/
            └── route.js
```

---

# 9. Exemplo com ID

Para:

```text
GET /api/usuarios/:id
```

estrutura:

```text
src/
└── app/
    └── api/
        └── usuarios/
            ├── route.js
            │
            └── [id]/
                └── route.js
```

---

# 10. Estrutura de Autenticação

```text
src/app/api/auth/
│
├── login/
│   └── route.js
│
└── logout/
    └── route.js
```

A estrutura poderá ser adaptada à estratégia de autenticação escolhida.

---

# 11. Estrutura de Usuários

```text
src/app/api/usuarios/
│
├── route.js
│
└── [id]/
    │
    ├── route.js
    │
    ├── seguidores/
    │   └── route.js
    │
    ├── seguindo/
    │   └── route.js
    │
    ├── emblemas/
    │   └── route.js
    │
    ├── certificados/
    │   └── route.js
    │
    ├── eventos/
    │   └── route.js
    │
    └── hackathons/
        └── route.js
```

---

# 12. Estrutura de Perfis

```text
src/app/api/perfis/
│
└── [usuarioId]/
    │
    ├── route.js
    │
    ├── tecnologias/
    │   └── route.js
    │
    └── areas-interesse/
        └── route.js
```

---

# 13. Estrutura de Empresas

```text
src/app/api/empresas/
│
├── route.js
│
└── [id]/
    │
    ├── route.js
    │
    ├── verificacoes/
    │   └── route.js
    │
    ├── seguidores/
    │   └── route.js
    │
    └── eventos/
        └── route.js
```

---

# 14. Estrutura de Eventos

```text
src/app/api/eventos/
│
├── route.js
│
└── [id]/
    │
    ├── route.js
    │
    ├── enviar-aprovacao/
    │   └── route.js
    │
    ├── cancelar/
    │   └── route.js
    │
    ├── organizadores/
    │   └── route.js
    │
    ├── inscricoes/
    │   └── route.js
    │
    ├── trilhas/
    │   └── route.js
    │
    ├── atividades/
    │   └── route.js
    │
    ├── checkins/
    │   └── route.js
    │
    ├── patrocinadores/
    │   └── route.js
    │
    ├── estandes/
    │   └── route.js
    │
    ├── ofertas/
    │   └── route.js
    │
    ├── comunicados/
    │   └── route.js
    │
    ├── emblemas/
    │   └── route.js
    │
    ├── certificados/
    │   └── route.js
    │
    └── hackathon/
        └── route.js
```

---

# 15. Estrutura Administrativa

```text
src/app/api/admin/
│
├── verificacoes/
│   │
│   ├── route.js
│   │
│   └── [id]/
│       │
│       ├── aprovar/
│       │   └── route.js
│       │
│       └── rejeitar/
│           └── route.js
│
└── eventos/
    │
    ├── route.js
    │
    └── [id]/
        │
        ├── aprovar/
        │   └── route.js
        │
        └── rejeitar/
            └── route.js
```

---

# 16. Estrutura de Inscrições

```text
src/app/api/inscricoes/
│
└── [id]/
    │
    ├── route.js
    │
    ├── aprovar/
    │   └── route.js
    │
    ├── rejeitar/
    │   └── route.js
    │
    ├── confirmar/
    │   └── route.js
    │
    └── oferecer-vaga/
        └── route.js
```

---

# 17. Estrutura de Atividades

```text
src/app/api/atividades/
│
└── [id]/
    │
    ├── route.js
    │
    ├── inscricoes/
    │   └── route.js
    │
    └── checkins/
        └── route.js
```

---

# 18. Estrutura de Hackathons

```text
src/app/api/hackathons/
│
└── [id]/
    │
    ├── route.js
    │
    ├── fases/
    │   └── route.js
    │
    ├── desafios/
    │   └── route.js
    │
    ├── equipes/
    │   └── route.js
    │
    ├── submissoes/
    │   └── route.js
    │
    ├── criterios-avaliacao/
    │   └── route.js
    │
    ├── jurados/
    │   └── route.js
    │
    ├── avaliacoes/
    │   └── route.js
    │
    ├── resultados/
    │   └── route.js
    │
    └── ranking/
        │
        ├── route.js
        │
        └── visibilidade/
            └── route.js
```

---

# 19. Estrutura de Equipes

```text
src/app/api/equipes/
│
└── [id]/
    │
    ├── route.js
    │
    ├── membros/
    │   └── route.js
    │
    ├── convites/
    │   └── route.js
    │
    ├── solicitacoes/
    │   └── route.js
    │
    └── desclassificar/
        └── route.js
```

---

# 20. Estrutura de Submissões

```text
src/app/api/submissoes/
│
└── [id]/
    │
    ├── route.js
    │
    └── versoes/
        └── route.js
```

---

# 21. Diretório `services`

Os Services representam os casos de uso.

Estrutura prevista:

```text
src/services/
│
├── usuario/
│   └── usuarioService.js
│
├── perfil/
│   └── perfilService.js
│
├── empresa/
│   └── empresaService.js
│
├── verificacao/
│   └── verificacaoEmpresaService.js
│
├── evento/
│   └── eventoService.js
│
├── inscricao/
│   └── inscricaoEventoService.js
│
├── trilha/
│   └── trilhaService.js
│
├── atividade/
│   └── atividadeService.js
│
├── checkin/
│   └── checkinService.js
│
├── hackathon/
│   └── hackathonService.js
│
├── fase/
│   └── faseHackathonService.js
│
├── desafio/
│   └── desafioService.js
│
├── equipe/
│   └── equipeService.js
│
├── submissao/
│   └── submissaoService.js
│
├── avaliacao/
│   └── avaliacaoService.js
│
├── resultado/
│   └── resultadoService.js
│
├── ranking/
│   └── rankingService.js
│
├── emblema/
│   └── emblemaService.js
│
├── certificado/
│   └── certificadoService.js
│
├── patrocinio/
│   └── patrocinioService.js
│
├── comunicado/
│   └── comunicadoService.js
│
└── notificacao/
    └── notificacaoService.js
```

---

# 22. Regra para Services

Não criar todos os Services antecipadamente.

Exemplo:

Durante a Sprint de usuários:

```text
criar:
UsuarioService
PerfilService
```

Não há necessidade de criar nesse momento:

```text
RankingService
PatrocinioService
CertificadoService
```

---

# 23. Diretório `repositories`

Os Repositories representam acesso aos dados.

Estrutura prevista:

```text
src/repositories/
│
├── usuario/
│   └── usuarioRepository.js
│
├── perfil/
│   └── perfilRepository.js
│
├── empresa/
│   └── empresaRepository.js
│
├── verificacao/
│   └── verificacaoEmpresaRepository.js
│
├── evento/
│   └── eventoRepository.js
│
├── inscricao/
│   └── inscricaoEventoRepository.js
│
├── atividade/
│   └── atividadeRepository.js
│
├── hackathon/
│   └── hackathonRepository.js
│
├── equipe/
│   └── equipeRepository.js
│
├── submissao/
│   └── submissaoRepository.js
│
├── avaliacao/
│   └── avaliacaoRepository.js
│
└── notificacao/
    └── notificacaoRepository.js
```

---

# 24. Diretório `models`

O diretório:

```text
src/models/
```

representará as entidades persistidas do sistema.

Estrutura conceitual:

```text
src/models/
│
├── usuario.js
├── perfil.js
├── tecnologia.js
├── areaInteresse.js
├── empresa.js
├── verificacaoEmpresa.js
├── evento.js
├── eventoOrganizador.js
├── inscricaoEvento.js
├── trilha.js
├── atividade.js
├── inscricaoAtividade.js
├── checkinEvento.js
├── checkinAtividade.js
├── hackathon.js
├── faseHackathon.js
├── desafio.js
├── equipe.js
├── membroEquipe.js
├── conviteEquipe.js
├── solicitacaoEntradaEquipe.js
├── submissao.js
├── versaoSubmissao.js
├── criterioAvaliacao.js
├── juradoHackathon.js
├── avaliacao.js
├── resultado.js
├── ranking.js
├── emblema.js
├── emblemaConcedido.js
├── certificado.js
├── certificadoEmitido.js
├── patrocinio.js
├── estande.js
├── oferta.js
├── comunicado.js
├── preferenciaNotificacao.js
└── notificacao.js
```

A forma exata desses arquivos dependerá do ORM escolhido.

---

# 25. Diretório `dto`

Os DTOs serão separados por domínio.

Estrutura:

```text
src/dto/
│
├── usuario/
│   ├── createUsuarioDTO.js
│   ├── updateUsuarioDTO.js
│   └── usuarioResponseDTO.js
│
├── perfil/
│   └── updatePerfilDTO.js
│
├── empresa/
│   ├── createEmpresaDTO.js
│   └── updateEmpresaDTO.js
│
├── evento/
│   ├── createEventoDTO.js
│   └── updateEventoDTO.js
│
├── inscricao/
│
├── atividade/
│
├── hackathon/
│
├── equipe/
│
├── submissao/
│
├── avaliacao/
│
└── notificacao/
```

---

# 26. Regra para DTOs

Criar somente DTOs que possuam finalidade clara.

Exemplo:

```text
CreateUsuarioDTO
```

é necessário porque representa os dados do cadastro.

Evitar criar:

```text
UsuarioDTO1
UsuarioDTO2
UsuarioDTO3
```

sem responsabilidade definida.

---

# 27. Diretório `validators`

Estrutura prevista:

```text
src/validators/
│
├── usuario/
│   └── createUsuarioValidator.js
│
├── perfil/
│
├── empresa/
│
├── evento/
│
├── inscricao/
│
├── atividade/
│
├── hackathon/
│
├── equipe/
│
├── submissao/
│
└── avaliacao/
```

A biblioteca utilizada para validação ainda será definida.

---

# 28. Diretório `config`

Estrutura:

```text
src/config/
│
├── database.js
│
└── env.js
```

Outros arquivos devem ser adicionados somente quando necessários.

Exemplos futuros:

```text
auth.js
storage.js
notifications.js
```

---

# 29. Diretório `utils`

Utilizado somente para funções realmente genéricas.

Estrutura possível:

```text
src/utils/
│
├── date.js
├── pagination.js
└── response.js
```

Evitar:

```text
src/utils/
└── utils.js
```

com dezenas de funções sem relação.

---

# 30. Diretório `components`

O frontend poderá utilizar:

```text
src/components/
│
├── usuario/
├── empresa/
├── evento/
├── atividade/
├── hackathon/
├── equipe/
├── ranking/
├── notificacao/
└── shared/
```

---

# 31. Componentes Compartilhados

```text
src/components/shared/
```

poderá conter componentes genéricos.

Exemplos:

```text
Button

Input

Modal

Pagination

Loading

EmptyState

ErrorMessage
```

---

# 32. Páginas de Usuário

Estrutura possível:

```text
src/app/
│
├── login/
│   └── page.js
│
├── cadastro/
│   └── page.js
│
└── perfil/
    └── [id]/
        └── page.js
```

---

# 33. Páginas de Empresa

```text
src/app/empresas/
│
├── page.js
│
└── [id]/
    └── page.js
```

---

# 34. Páginas de Eventos

```text
src/app/eventos/
│
├── page.js
│
├── novo/
│   └── page.js
│
└── [id]/
    │
    ├── page.js
    │
    ├── programacao/
    │   └── page.js
    │
    ├── participantes/
    │   └── page.js
    │
    └── hackathon/
        └── page.js
```

---

# 35. Páginas de Hackathon

Estrutura futura:

```text
src/app/hackathons/
│
└── [id]/
    │
    ├── page.js
    │
    ├── desafios/
    │   └── page.js
    │
    ├── equipes/
    │   └── page.js
    │
    ├── submissao/
    │   └── page.js
    │
    └── ranking/
        └── page.js
```

---

# 36. Páginas Administrativas

```text
src/app/admin/
│
├── page.js
│
├── empresas/
│   └── page.js
│
└── eventos/
    └── page.js
```

---

# 37. Fluxo de Criação de Arquivos por Endpoint

Ao implementar um endpoint novo, a equipe deve avaliar quais arquivos realmente são necessários.

Exemplo:

```text
Cadastrar usuário
```

Pode gerar:

```text
src/app/api/usuarios/route.js

src/dto/usuario/createUsuarioDTO.js

src/validators/usuario/createUsuarioValidator.js

src/services/usuario/usuarioService.js

src/repositories/usuario/usuarioRepository.js

src/models/usuario.js
```

---

# 38. Ciclo Visual

```text
route.js
   ↓
DTO
   ↓
Validator
   ↓
Service
   ↓
Repository
   ↓
Model
   ↓
Banco
```

---

# 39. Sprint 0 — Arquivos Principais

Na Sprint 0 devem existir inicialmente:

```text
package.json

next.config.js

.gitignore

.env

.env.example

src/

docs/
```

Depois da escolha do banco:

```text
configuração de banco

estrutura do ORM

migration inicial
```

---

# 40. Sprint 1 — Usuários

Criar conforme necessário:

```text
src/app/api/usuarios/

src/app/api/auth/

src/services/usuario/

src/repositories/usuario/

src/dto/usuario/

src/validators/usuario/

src/models/usuario.js
```

---

# 41. Sprint 2 — Perfis

Adicionar:

```text
src/app/api/perfis/

src/services/perfil/

src/repositories/perfil/

src/dto/perfil/

src/validators/perfil/

src/models/perfil.js
```

E, conforme necessário:

```text
tecnologia

areaInteresse

perfilTecnologia

perfilAreaInteresse
```

---

# 42. Sprint 3 e 4 — Empresas

Adicionar:

```text
src/app/api/empresas/

src/services/empresa/

src/services/verificacao/

src/repositories/empresa/

src/repositories/verificacao/

src/models/empresa.js

src/models/verificacaoEmpresa.js
```

---

# 43. Sprint 5 e 6 — Eventos

Adicionar:

```text
src/app/api/eventos/

src/app/api/admin/eventos/

src/services/evento/

src/repositories/evento/

src/models/evento.js

src/models/eventoOrganizador.js
```

---

# 44. Sprint 8 e 9 — Inscrições

Adicionar:

```text
src/app/api/inscricoes/

src/services/inscricao/

src/repositories/inscricao/

src/models/inscricaoEvento.js
```

---

# 45. Sprint 10 e 11 — Programação

Adicionar:

```text
src/app/api/trilhas/

src/app/api/atividades/

src/services/trilha/

src/services/atividade/

src/repositories/trilha/

src/repositories/atividade/

src/models/trilha.js

src/models/atividade.js

src/models/inscricaoAtividade.js
```

---

# 46. Sprint 12 — Check-in

Adicionar:

```text
src/services/checkin/

src/models/checkinEvento.js

src/models/checkinAtividade.js
```

---

# 47. Sprint 13 a 15 — Hackathon

Adicionar:

```text
src/app/api/hackathons/

src/app/api/fases/

src/app/api/desafios/

src/services/hackathon/

src/services/fase/

src/services/desafio/

src/models/hackathon.js

src/models/faseHackathon.js

src/models/desafio.js
```

---

# 48. Sprint 16 — Equipes

Adicionar:

```text
src/app/api/equipes/

src/app/api/convites-equipe/

src/app/api/solicitacoes-equipe/

src/services/equipe/

src/repositories/equipe/

src/models/equipe.js

src/models/membroEquipe.js

src/models/conviteEquipe.js

src/models/solicitacaoEntradaEquipe.js
```

---

# 49. Sprint 17 — Submissões

Adicionar:

```text
src/app/api/submissoes/

src/app/api/versoes-submissao/

src/services/submissao/

src/repositories/submissao/

src/models/submissao.js

src/models/versaoSubmissao.js
```

---

# 50. Sprint 18 e 19 — Avaliação e Ranking

Adicionar:

```text
src/app/api/criterios-avaliacao/

src/app/api/avaliacoes/

src/app/api/resultados/

src/services/avaliacao/

src/services/resultado/

src/services/ranking/

src/models/criterioAvaliacao.js

src/models/juradoHackathon.js

src/models/avaliacao.js

src/models/resultado.js

src/models/ranking.js
```

---

# 51. Sprint 20 e 21 — Conquistas

Adicionar:

```text
src/app/api/emblemas/

src/app/api/certificados/

src/services/emblema/

src/services/certificado/

src/models/emblema.js

src/models/emblemaConcedido.js

src/models/certificado.js

src/models/certificadoEmitido.js
```

---

# 52. Sprint 23 — Social

Adicionar:

```text
src/models/seguimentoUsuario.js

src/models/seguimentoEmpresa.js
```

Além das rotas correspondentes.

---

# 53. Sprint 24 e 25 — Patrocinadores

Adicionar:

```text
src/app/api/estandes/

src/app/api/ofertas/

src/services/patrocinio/

src/models/patrocinio.js

src/models/estande.js

src/models/oferta.js
```

---

# 54. Sprint 26 — Comunicação

Adicionar:

```text
src/app/api/comunicados/

src/services/comunicado/

src/models/comunicado.js
```

---

# 55. Sprint 27 — Notificações

Adicionar:

```text
src/app/api/notificacoes/

src/services/notificacao/

src/repositories/notificacao/

src/models/notificacao.js

src/models/preferenciaNotificacao.js
```

---

# 56. Estrutura Completa Conceitual

Ao final da Fase 1, uma estrutura semelhante poderá existir:

```text
src/
│
├── app/
│   │
│   ├── api/
│   │   ├── auth/
│   │   ├── usuarios/
│   │   ├── perfis/
│   │   ├── empresas/
│   │   ├── eventos/
│   │   ├── inscricoes/
│   │   ├── trilhas/
│   │   ├── atividades/
│   │   ├── hackathons/
│   │   ├── fases/
│   │   ├── desafios/
│   │   ├── equipes/
│   │   ├── submissoes/
│   │   ├── avaliacoes/
│   │   ├── resultados/
│   │   ├── emblemas/
│   │   ├── certificados/
│   │   ├── estandes/
│   │   ├── ofertas/
│   │   ├── comunicados/
│   │   ├── notificacoes/
│   │   └── admin/
│   │
│   ├── login/
│   ├── cadastro/
│   ├── perfil/
│   ├── empresas/
│   ├── eventos/
│   ├── hackathons/
│   └── admin/
│
├── components/
│
├── services/
│
├── repositories/
│
├── models/
│
├── dto/
│
├── validators/
│
├── config/
│
└── utils/
```

---

# 57. Arquivos que Não Devem Ser Criados Antecipadamente

Evitar criar antecipadamente:

```text
service vazio

repository vazio

DTO sem uso

validator sem uso

model de funcionalidade futura

rota sem endpoint previsto

componente sem tela prevista
```

Criar arquivos conforme necessidade real.

---

# 58. Regra de Criação de Módulo

Um novo módulo deve ser criado quando existir:

```text
funcionalidade real
+
requisito correspondente
+
regra de negócio correspondente
+
entidade quando necessária
+
endpoint quando necessário
```

---

# 59. Regra de Nomeação

A equipe deve utilizar nomenclatura consistente.

Exemplo recomendado:

```text
usuarioService.js

usuarioRepository.js

createUsuarioDTO.js

createUsuarioValidator.js
```

Evitar misturar estilos:

```text
Usuario_service.js

repositoryUsuario.js

create-user-dto.js

ValidaUsuario.js
```

Escolher um padrão e mantê-lo.

---

# 60. Regra para Pastas

Pastas devem representar:

```text
domínio
```

ou:

```text
responsabilidade
```

Exemplo válido:

```text
services/evento/
```

Evitar estrutura sem significado:

```text
services/outros/
```

---

# 61. Regra para Imports

Sempre que possível, evitar caminhos excessivamente longos.

Exemplo:

```javascript
import { usuarioService } from "@/services/usuario/usuarioService";
```

em vez de:

```javascript
import { usuarioService } from "../../../../services/usuario/usuarioService";
```

A configuração definitiva de aliases será realizada no projeto.

---

# 62. Dependência entre Camadas

Fluxo principal:

```text
Route Handler
        ↓
Service
        ↓
Repository
        ↓
Persistência
```

O contrário deve ser evitado.

---

# 63. Relação com o Banco

Somente a camada responsável pela persistência deve possuir conhecimento direto da tecnologia de banco quando possível.

```text
Service
   ↓
Repository
   ↓
ORM
   ↓
Banco
```

---

# 64. Banco Ainda Não Definido

Até a decisão técnica:

```text
BANCO = A DEFINIR

ORM = A DEFINIR
```

Portanto, o mapa não inclui arquivos específicos como:

```text
prisma/
sequelize/
mongoose/
```

antes dessa escolha.

---

# 65. Validação Ainda Não Definida

A biblioteca de validação também permanece:

```text
A DEFINIR
```

Portanto, este mapa utiliza:

```text
validators/
```

como conceito arquitetural.

---

# 66. Autenticação Ainda Não Definida

A estratégia definitiva também permanece:

```text
A DEFINIR
```

A pasta:

```text
api/auth/
```

representa a necessidade funcional, não uma tecnologia específica.

---

# 67. Arquivos Futuros

Funcionalidades futuras poderão adicionar:

```text
src/services/carteira/

src/repositories/carteira/

src/models/carteira.js

src/models/transacao.js

src/app/api/carteira/
```

Porém, esses arquivos não pertencem à Fase 1 atual.

---

# 68. Fluxo para um Novo Recurso

Quando a equipe for desenvolver uma funcionalidade nova:

```text
1. Consultar BACKLOG.md

2. Identificar a Sprint

3. Consultar REQUISITOS.md

4. Consultar REGRAS-DE-NEGOCIO.md

5. Consultar MODELO-DE-DADOS.md

6. Consultar API.md

7. Criar apenas os arquivos necessários

8. Implementar o ciclo

9. Testar no Postman

10. Atualizar documentação caso algo tenha mudado
```

---

# 69. Exemplo Completo — Cadastro de Usuário

Arquivos envolvidos:

```text
src/app/api/usuarios/route.js

src/dto/usuario/createUsuarioDTO.js

src/validators/usuario/createUsuarioValidator.js

src/services/usuario/usuarioService.js

src/repositories/usuario/usuarioRepository.js

src/models/usuario.js
```

Fluxo:

```text
POST /api/usuarios
        ↓
route.js
        ↓
CreateUsuarioDTO
        ↓
Validator
        ↓
UsuarioService
        ↓
UsuarioRepository
        ↓
Usuario
        ↓
Banco
```

---

# 70. Exemplo — Criar Evento

Arquivos conceituais:

```text
src/app/api/eventos/route.js

src/dto/evento/createEventoDTO.js

src/validators/evento/createEventoValidator.js

src/services/evento/eventoService.js

src/repositories/evento/eventoRepository.js

src/models/evento.js
```

---

# 71. Exemplo — Criar Equipe

```text
src/app/api/hackathons/[id]/equipes/route.js

src/dto/equipe/createEquipeDTO.js

src/validators/equipe/createEquipeValidator.js

src/services/equipe/equipeService.js

src/repositories/equipe/equipeRepository.js

src/models/equipe.js

src/models/membroEquipe.js
```

---

# 72. Exemplo — Enviar Submissão

```text
src/app/api/submissoes/[id]/versoes/route.js

src/dto/submissao/createVersaoSubmissaoDTO.js

src/validators/submissao/createVersaoSubmissaoValidator.js

src/services/submissao/submissaoService.js

src/repositories/submissao/submissaoRepository.js

src/models/versaoSubmissao.js
```

---

# 73. O que Este Documento Não Substitui

Este arquivo não substitui:

```text
ARQUITETURA.md
```

porque não explica profundamente as responsabilidades.

Não substitui:

```text
API.md
```

porque não define contratos dos endpoints.

Não substitui:

```text
BACKLOG.md
```

porque não define histórias.

Não substitui:

```text
SPRINTS.md
```

porque não define prioridade de entrega em detalhes.

Este documento apenas mostra:

```text
onde cada parte deverá existir
```

---

# 74. Estrutura Mental para a Equipe

```text
DOCUMENTAÇÃO
      ↓
BACKLOG
      ↓
SPRINT
      ↓
FUNCIONALIDADE
      ↓
ROTA
      ↓
SERVICE
      ↓
REPOSITORY
      ↓
BANCO
      ↓
POSTMAN
```

---

# 75. Regra Final

O mapa deve evoluir junto com o projeto.

Não é obrigatório seguir a árvore literalmente caso durante a implementação seja encontrada uma estrutura mais simples e coerente.

Qualquer mudança importante deve manter:

```text
clareza

separação de responsabilidades

consistência

facilidade de manutenção

facilidade de entendimento pela equipe
```

A estrutura existe para ajudar o desenvolvimento.

Ela não deve se tornar uma fonte de complexidade desnecessária.
