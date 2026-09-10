# REQUISITOS

## 1. Requisitos Funcionais

### Usuários

**RF-001** — O sistema deve permitir o cadastro de usuários.

**RF-002** — O sistema deve permitir autenticação de usuários.

**RF-003** — O sistema deve permitir consulta de perfil público.

**RF-004** — O sistema deve permitir edição do próprio perfil.

**RF-005** — O usuário deve poder cadastrar bio, tecnologias, áreas de interesse e links externos.

**RF-006** — O usuário deve poder seguir outros usuários.

**RF-007** — O usuário deve poder seguir empresas.

### Empresas

**RF-008** — O sistema deve permitir o cadastro de empresas.

**RF-009** — Empresas devem possuir página pública.

**RF-010** — Empresas devem poder solicitar verificação.

**RF-011** — Administradores devem poder aprovar ou rejeitar solicitações de verificação.

**RF-012** — Empresas verificadas devem possuir selo de verificação.

### Eventos

**RF-013** — Empresas verificadas devem poder criar eventos.

**RF-014** — Um evento deve poder ser presencial, online ou híbrido.

**RF-015** — Um evento deve poder ser gratuito ou pago.

**RF-016** — Um evento deve poder possuir múltiplas empresas organizadoras.

**RF-017** — O sistema deve permitir envio de evento para aprovação.

**RF-018** — Administradores devem poder aprovar ou rejeitar eventos.

**RF-019** — Empresas devem poder editar eventos publicados.

**RF-020** — Empresas devem poder cancelar eventos.

**RF-021** — Eventos cancelados devem permanecer visíveis no histórico.

**RF-022** — O sistema deve permitir consulta de eventos por localização.

**RF-023** — O sistema deve permitir busca e filtros de eventos.

### Inscrições

**RF-024** — Usuários devem poder se inscrever em eventos.

**RF-025** — Eventos devem poder possuir limite de vagas.

**RF-026** — O organizador deve poder habilitar lista de espera.

**RF-027** — O organizador deve poder exigir aprovação manual da inscrição.

**RF-028** — O usuário deve poder cancelar sua própria inscrição.

**RF-029** — O sistema deve controlar estados da inscrição.

**RF-030** — O sistema deve permitir confirmação de participação.

### Programação e atividades

**RF-031** — Eventos devem poder possuir programação.

**RF-032** — Eventos devem poder possuir múltiplas trilhas.

**RF-033** — Trilhas devem poder possuir atividades.

**RF-034** — Atividades devem poder existir sem trilha.

**RF-035** — Atividades devem poder exigir inscrição própria.

**RF-036** — Atividades devem poder possuir limite próprio de vagas.

**RF-037** — O sistema deve permitir check-in no evento.

**RF-038** — O sistema deve permitir check-in em atividades.

### Hackathons

**RF-039** — Um evento deve poder possuir características de hackathon.

**RF-040** — Hackathons devem permitir participação individual, por equipe ou ambas.

**RF-041** — O organizador deve poder definir tamanho mínimo e máximo de equipe.

**RF-042** — O sistema deve permitir criação de equipes por usuários.

**RF-043** — O sistema deve permitir convite para equipe.

**RF-044** — O sistema deve permitir solicitação de entrada em equipe.

**RF-045** — O organizador deve poder formar equipes manualmente.

**RF-046** — Hackathons devem poder possuir múltiplas fases.

**RF-047** — O organizador deve poder definir ordem e período das fases.

**RF-048** — Hackathons devem poder possuir desafios.

### Submissões

**RF-049** — Participantes ou equipes devem poder realizar submissões.

**RF-050** — O sistema deve permitir múltiplas versões de submissão.

**RF-051** — O sistema deve bloquear submissões fora do prazo.

**RF-052** — Versões anteriores devem permanecer registradas.

### Avaliação e ranking

**RF-053** — Hackathons devem poder possuir múltiplos critérios de avaliação.

**RF-054** — Um critério deve poder possuir peso definido pelo evento.

**RF-055** — Uma equipe deve poder ser avaliada por múltiplos jurados.

**RF-056** — O sistema deve permitir registrar resultado final.

**RF-057** — O sistema deve permitir exibir ranking.

**RF-058** — O organizador deve poder ocultar o ranking até o momento definido.

**RF-059** — O sistema deve permitir empates quando o evento permitir.

**RF-060** — O organizador deve poder definir critérios de desempate.

**RF-061** — O organizador deve poder desclassificar uma equipe.

### Emblemas e certificados

**RF-062** — Eventos devem poder criar emblemas próprios.

**RF-063** — A plataforma deve permitir conceder emblemas aos usuários.

**RF-064** — Emblemas concedidos devem aparecer no perfil do usuário.

**RF-065** — Eventos devem poder emitir certificados.

**RF-066** — Certificados emitidos devem permanecer vinculados ao histórico do usuário.

### Patrocinadores

**RF-067** — Eventos devem poder possuir múltiplos patrocinadores.

**RF-068** — Patrocinadores devem poder possuir página pública.

**RF-069** — Patrocinadores devem poder possuir estandes.

**RF-070** — Patrocinadores devem poder cadastrar ofertas relacionadas ao evento.

**RF-071** — Desafios devem poder ser associados a patrocinadores.

### Comunicação e notificações

**RF-072** — Organizadores devem poder enviar comunicados.

**RF-073** — Comunicados devem poder ser direcionados a grupos específicos.

**RF-074** — O sistema deve possuir central de notificações.

**RF-075** — Usuários devem poder personalizar categorias de notificação.

**RF-076** — O sistema deve permitir notificações essenciais.

**RF-077** — O sistema deve informar mudança de horário, local ou cancelamento.

**RF-078** — O sistema deve informar convites, solicitações e alterações de equipe.

**RF-079** — O sistema deve informar mudanças de fase do hackathon.

**RF-080** — O sistema deve informar resultados, emblemas e certificados.

## 2. Requisitos Não Funcionais

**RNF-001** — O sistema deve possuir interface responsiva.

**RNF-002** — A aplicação deve ser executada utilizando Node.js e Next.js.

**RNF-003** — O sistema deve utilizar arquitetura organizada em responsabilidades separadas.

**RNF-004** — Rotas da API não devem concentrar regras de negócio complexas.

**RNF-005** — Entradas de dados devem ser validadas antes da execução das regras de negócio.

**RNF-006** — Operações de consulta em listas extensas devem prever paginação.

**RNF-007** — Dados históricos importantes não devem ser apagados sem necessidade.

**RNF-008** — O sistema deve utilizar respostas HTTP padronizadas.

**RNF-009** — Endpoints devem ser documentados.

**RNF-010** — Os endpoints principais devem possuir cenários de teste documentados no Postman.

**RNF-011** — O projeto deve manter organização de código compreensível para todos os integrantes da equipe.

**RNF-012** — O sistema deve permitir evolução incremental sem exigir separação inicial em múltiplos serviços.
