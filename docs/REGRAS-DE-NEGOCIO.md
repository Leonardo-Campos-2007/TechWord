# REGRAS DE NEGÓCIO

## 1. Objetivo do Documento

Este documento define as regras de negócio da plataforma de eventos e hackathons de tecnologia.

As regras de negócio representam condições, restrições, permissões e comportamentos que devem ser respeitados independentemente da tecnologia utilizada.

Este documento não define:

* endpoints;
* estrutura de código;
* banco de dados;
* DTOs;
* repositories;
* services;
* testes;
* Sprints.

---

# 2. Usuários

## RN-USR-001 — Unicidade de e-mail

Cada conta de usuário deve possuir um e-mail único na plataforma.

## RN-USR-002 — Conta necessária para participação

Somente usuários cadastrados podem realizar inscrições em eventos, atividades ou hackathons.

## RN-USR-003 — Alteração da própria conta

Um usuário comum somente pode alterar os dados de sua própria conta.

## RN-USR-004 — Identidade da conta

Uma conta deve representar um único usuário dentro da plataforma.

## RN-USR-005 — Conta e perfil são conceitos distintos

Os dados utilizados para acesso ao sistema não devem ser tratados como equivalentes às informações públicas do perfil.

## RN-USR-006 — Histórico do usuário

Informações históricas relevantes relacionadas à participação do usuário devem permanecer vinculadas a ele.

## RN-USR-007 — Participação vinculada ao usuário

Inscrições, certificados, emblemas, colocações e participações devem estar vinculados a um usuário identificável.

---

# 3. Perfil do Usuário

## RN-PRF-001 — Perfil público

O perfil do usuário pode ser visualizado por outros usuários da plataforma.

## RN-PRF-002 — Controle do próprio perfil

Somente o próprio usuário pode editar seus dados pessoais de perfil, salvo atuação administrativa autorizada.

## RN-PRF-003 — Conquistas públicas

Emblemas, certificados e colocações podem ser exibidos no perfil público.

## RN-PRF-004 — Histórico de eventos

Eventos e hackathons dos quais o usuário participou podem compor seu histórico público.

## RN-PRF-005 — Links profissionais

Links adicionados ao perfil devem representar informações fornecidas pelo próprio usuário.

## RN-PRF-006 — Tecnologias e interesses

Tecnologias e áreas de interesse cadastradas no perfil representam informações declaradas pelo usuário.

## RN-PRF-007 — Conquista não editável pelo usuário

O usuário não pode criar, alterar ou atribuir a si próprio emblemas, certificados ou colocações oficiais.

## RN-PRF-008 — Origem da conquista

Toda conquista exibida no perfil deve possuir origem identificável.

---

# 4. Seguidores e Recursos Sociais

## RN-SOC-001 — Seguir usuário

Um usuário pode seguir outros usuários.

## RN-SOC-002 — Deixar de seguir

Um usuário pode deixar de seguir outro usuário a qualquer momento.

## RN-SOC-003 — Seguir empresa

Um usuário pode seguir empresas cadastradas na plataforma.

## RN-SOC-004 — Relação independente

Seguir um usuário ou empresa não cria qualquer vínculo de inscrição, participação ou organização.

## RN-SOC-005 — Não duplicidade de seguimento

Um mesmo usuário não deve possuir mais de uma relação ativa de seguimento com o mesmo usuário ou empresa.

## RN-SOC-006 — Autoseguimento

Um usuário não deve seguir a si próprio.

## RN-SOC-007 — Histórico social não obrigatório

A plataforma não é obrigada a manter publicamente histórico de usuários anteriormente seguidos.

---

# 5. Empresas

## RN-EMP-001 — Cadastro de empresa

Uma empresa deve estar cadastrada antes de utilizar recursos exclusivos de organização ou patrocínio.

## RN-EMP-002 — Página pública

Uma empresa cadastrada pode possuir uma página pública própria.

## RN-EMP-003 — Empresa e usuário são conceitos distintos

A empresa deve ser tratada como entidade de negócio independente da conta utilizada para administrá-la.

## RN-EMP-004 — Múltiplas participações

Uma empresa pode participar de múltiplos eventos.

## RN-EMP-005 — Papéis diferentes

Uma empresa pode atuar como:

* organizadora;
* coorganizadora;
* patrocinadora.

## RN-EMP-006 — Acúmulo de papéis

Uma mesma empresa pode exercer mais de um papel em eventos diferentes.

## RN-EMP-007 — Histórico da empresa

Eventos organizados ou patrocinados podem permanecer associados ao histórico da empresa.

---

# 6. Verificação de Empresas

## RN-VER-001 — Verificação necessária

Uma empresa deve ser verificada antes de poder enviar eventos para aprovação.

## RN-VER-002 — Verificação não automática

O cadastro da empresa não concede automaticamente status de empresa verificada.

## RN-VER-003 — Aprovação administrativa

A verificação da empresa depende de decisão administrativa da plataforma.

## RN-VER-004 — Rejeição possível

Uma solicitação de verificação pode ser rejeitada.

## RN-VER-005 — Motivo de rejeição

Uma rejeição deve possuir motivo registrado.

## RN-VER-006 — Selo de verificação

Somente empresas aprovadas podem possuir selo de verificação.

## RN-VER-007 — Verificação da empresa não aprova eventos

O fato de uma empresa ser verificada não significa que seus eventos estejam automaticamente aprovados.

## RN-VER-008 — Estado de verificação

A solicitação deve possuir um estado identificável durante seu ciclo.

Estados esperados:

* pendente;
* aprovada;
* rejeitada.

---

# 7. Eventos

## RN-EVT-001 — Evento vinculado a organizador

Todo evento deve possuir pelo menos uma empresa organizadora.

## RN-EVT-002 — Empresa verificada para criação oficial

Somente empresas verificadas podem enviar eventos para aprovação e publicação.

## RN-EVT-003 — Múltiplos organizadores

Um evento pode possuir mais de uma empresa organizadora.

## RN-EVT-004 — Evento em rascunho

Um evento pode permanecer como rascunho antes de ser enviado para aprovação.

## RN-EVT-005 — Rascunho não publicado

Eventos em rascunho não devem ser tratados como eventos públicos ativos.

## RN-EVT-006 — Aprovação obrigatória

Um evento deve ser aprovado pela plataforma antes de ser publicado.

## RN-EVT-007 — Rejeição de evento

A plataforma pode rejeitar um evento submetido para aprovação.

## RN-EVT-008 — Motivo da rejeição

Um evento rejeitado deve possuir motivo registrado.

## RN-EVT-009 — Publicação após aprovação

Somente eventos aprovados podem ser publicados.

## RN-EVT-010 — Edição após publicação

Um evento publicado pode ser editado pelo organizador.

## RN-EVT-011 — Alteração sem nova aprovação

Alterações realizadas após a publicação não obrigam o evento a retornar ao processo de aprovação.

## RN-EVT-012 — Cancelamento

O organizador pode cancelar um evento publicado.

## RN-EVT-013 — Cancelamento não remove histórico

Um evento cancelado deve permanecer registrado.

## RN-EVT-014 — Identificação de cancelamento

Eventos cancelados devem permanecer claramente identificados como cancelados.

## RN-EVT-015 — Encerramento

Eventos concluídos devem poder ser identificados como encerrados.

## RN-EVT-016 — Modalidade

Um evento deve possuir uma modalidade definida.

As modalidades permitidas são:

* presencial;
* online;
* híbrido.

## RN-EVT-017 — Localização presencial

Eventos presenciais devem possuir informação de localização física.

## RN-EVT-018 — Evento híbrido

Eventos híbridos podem possuir localização física e acesso online.

## RN-EVT-019 — Evento online

Eventos exclusivamente online não dependem de localização física para participação.

## RN-EVT-020 — Evento gratuito ou pago

Um evento deve poder ser classificado como gratuito ou pago.

## RN-EVT-021 — Preço e carteira são conceitos distintos

O pagamento da inscrição do evento não deve ser tratado como equivalente ao sistema futuro de créditos internos.

## RN-EVT-022 — Capacidade

Um evento pode possuir quantidade máxima de participantes.

## RN-EVT-023 — Datas coerentes

A data de término de um evento não pode ser anterior à data de início.

## RN-EVT-024 — Estado do evento

O evento deve possuir um estado coerente com sua situação atual.

Estados previstos:

* rascunho;
* aguardando aprovação;
* aprovado;
* publicado;
* inscrições abertas;
* inscrições encerradas;
* em andamento;
* encerrado;
* rejeitado;
* cancelado.

---

# 8. Descoberta de Eventos

## RN-DSC-001 — Eventos pesquisáveis

Somente eventos adequados à visualização pública devem aparecer em buscas comuns.

## RN-DSC-002 — Evento cancelado

Eventos cancelados podem continuar acessíveis por histórico, mas devem ser claramente identificados.

## RN-DSC-003 — Localização

A busca por proximidade deve considerar a localização informada para o evento.

## RN-DSC-004 — Eventos online

Eventos online podem ser exibidos independentemente da localização física do usuário.

## RN-DSC-005 — Filtros combináveis

O usuário pode utilizar múltiplos critérios de busca quando disponíveis.

---

# 9. Inscrições em Eventos

## RN-INS-001 — Usuário cadastrado

Somente usuários cadastrados podem realizar inscrição em eventos.

## RN-INS-002 — Evento disponível para inscrição

Uma inscrição somente pode ocorrer quando o evento estiver aceitando inscrições.

## RN-INS-003 — Inscrição única

Um usuário não deve possuir múltiplas inscrições ativas equivalentes no mesmo evento.

## RN-INS-004 — Capacidade máxima

O número de inscrições confirmadas não deve ultrapassar a capacidade definida pelo evento.

## RN-INS-005 — Inscrição automática

O organizador pode configurar o evento para aceitar inscrições automaticamente.

## RN-INS-006 — Aprovação manual

O organizador pode configurar o evento para exigir aprovação manual.

## RN-INS-007 — Aprovação do organizador

Quando houver aprovação manual, a inscrição somente pode ser considerada aprovada após decisão do organizador.

## RN-INS-008 — Rejeição de inscrição

O organizador pode rejeitar uma solicitação quando o evento utilizar aprovação manual.

## RN-INS-009 — Cancelamento pelo usuário

O usuário pode cancelar sua inscrição.

## RN-INS-010 — Cancelamento sujeito às regras do evento

O cancelamento pode estar sujeito às condições definidas pelo evento.

## RN-INS-011 — Inscrição e presença são diferentes

Estar inscrito não significa necessariamente ter presença confirmada.

## RN-INS-012 — Confirmação de participação

O evento pode exigir confirmação adicional de participação.

## RN-INS-013 — Lista de espera opcional

A lista de espera não deve ser criada automaticamente para todos os eventos.

## RN-INS-014 — Habilitação da lista de espera

A lista de espera somente deve existir quando o organizador permitir possibilidade de expansão ou substituição de vagas.

## RN-INS-015 — Vagas esgotadas

Quando as vagas forem esgotadas e não houver lista de espera, novas inscrições não devem ser aceitas.

## RN-INS-016 — Entrada em lista de espera

Quando as vagas estiverem esgotadas e a lista de espera estiver ativa, novos interessados podem ser adicionados a ela.

## RN-INS-017 — Liberação de vaga

O cancelamento ou liberação de uma vaga pode gerar oportunidade para participante da lista de espera.

## RN-INS-018 — Vaga oferecida não é confirmação automática

Um usuário da lista de espera que recebe uma vaga não deve ser considerado automaticamente confirmado.

## RN-INS-019 — Estado da inscrição

A inscrição deve possuir um estado coerente com sua situação.

Estados previstos:

* solicitada;
* aguardando aprovação;
* aguardando pagamento;
* inscrita;
* lista de espera;
* vaga oferecida;
* confirmada;
* rejeitada;
* cancelada.

---

# 10. Programação do Evento

## RN-PRG-001 — Programação vinculada ao evento

Toda programação deve estar relacionada a um evento.

## RN-PRG-002 — Múltiplas trilhas

Um evento pode possuir diversas trilhas.

## RN-PRG-003 — Trilhas simultâneas

Diferentes trilhas podem possuir atividades ocorrendo simultaneamente.

## RN-PRG-004 — Trilha opcional

Uma atividade não precisa obrigatoriamente pertencer a uma trilha.

## RN-PRG-005 — Organização da programação

O organizador é responsável por definir a programação do evento.

---

# 11. Atividades

## RN-ATV-001 — Atividade vinculada a evento

Toda atividade deve pertencer a um evento.

## RN-ATV-002 — Atividade em trilha

Uma atividade pode estar associada a uma trilha.

## RN-ATV-003 — Atividade sem trilha

Uma atividade também pode existir diretamente na programação geral.

## RN-ATV-004 — Capacidade independente

Uma atividade pode possuir limite de participantes diferente da capacidade geral do evento.

## RN-ATV-005 — Inscrição própria

Uma atividade pode exigir inscrição específica.

## RN-ATV-006 — Inscrição no evento não garante atividade

Estar inscrito no evento não garante automaticamente vaga em atividades com inscrição própria.

## RN-ATV-007 — Limite de atividade

A quantidade de participantes inscritos em uma atividade não deve ultrapassar sua capacidade.

## RN-ATV-008 — Cancelamento de inscrição

O usuário pode cancelar sua participação em uma atividade quando permitido.

## RN-ATV-009 — Horário coerente

O horário final de uma atividade não pode ser anterior ao horário inicial.

## RN-ATV-010 — Atividade dentro do contexto do evento

A atividade deve ocorrer dentro de período compatível com o evento, salvo programação especial explicitamente definida pelo organizador.

---

# 12. Check-in

## RN-CHK-001 — Check-in opcional

O organizador decide se o evento utilizará check-in.

## RN-CHK-002 — Check-in de atividade independente

Uma atividade pode exigir check-in mesmo que o evento geral não exija.

## RN-CHK-003 — Participante elegível

Somente participante relacionado ao evento ou atividade pode possuir check-in correspondente.

## RN-CHK-004 — Check-in não substitui inscrição

Realizar check-in não cria automaticamente uma inscrição.

## RN-CHK-005 — Registro de presença

O check-in representa registro de presença, e não necessariamente conclusão da atividade ou evento.

---

# 13. Hackathons

## RN-HCK-001 — Hackathon como especialização de evento

Um hackathon deve estar associado a um evento.

## RN-HCK-002 — Participação configurável

O organizador pode definir participação:

* individual;
* por equipe;
* ambas.

## RN-HCK-003 — Tamanho mínimo da equipe

Quando houver equipes, o organizador pode definir quantidade mínima de integrantes.

## RN-HCK-004 — Tamanho máximo da equipe

Quando houver equipes, o organizador pode definir quantidade máxima de integrantes.

## RN-HCK-005 — Regras definidas pelo organizador

As regras específicas do hackathon são definidas pelo organizador.

## RN-HCK-006 — Regras visíveis

Os participantes devem poder consultar as regras aplicáveis ao hackathon.

## RN-HCK-007 — Estrutura variável

Hackathons diferentes podem possuir estruturas e regras diferentes.

---

# 14. Fases do Hackathon

## RN-FAS-001 — Múltiplas fases

Um hackathon pode possuir várias fases.

## RN-FAS-002 — Ordem definida

As fases devem possuir uma ordem determinada pelo organizador.

## RN-FAS-003 — Fase personalizada

O organizador pode criar fases personalizadas.

## RN-FAS-004 — Período da fase

Uma fase pode possuir início e término definidos.

## RN-FAS-005 — Datas coerentes

O término de uma fase não pode ser anterior ao seu início.

## RN-FAS-006 — Fase atual

O hackathon deve possuir no máximo uma fase principal considerada atual quando as fases forem sequenciais.

## RN-FAS-007 — Fases futuras

As fases posteriores devem poder ser apresentadas como próximas etapas.

## RN-FAS-008 — Exemplos de fase

Fases possíveis incluem:

* inscrição;
* formação de equipes;
* desenvolvimento;
* submissão;
* avaliação;
* final;
* premiação;
* personalizada.

---

# 15. Desafios

## RN-DSF-001 — Desafio associado ao hackathon

Todo desafio deve estar relacionado a um hackathon.

## RN-DSF-002 — Descrição do desafio

O desafio deve possuir informações suficientes para que os participantes entendam o objetivo.

## RN-DSF-003 — Patrocinador opcional

Um desafio pode possuir uma empresa patrocinadora associada.

## RN-DSF-004 — Patrocínio não obrigatório

Um desafio não precisa ter patrocinador.

---

# 16. Equipes

## RN-EQP-001 — Equipe vinculada ao hackathon

Toda equipe deve pertencer a um hackathon.

## RN-EQP-002 — Equipes somente quando permitidas

Equipes somente podem ser utilizadas quando o hackathon permitir participação por equipe.

## RN-EQP-003 — Formação pelo participante

Participantes podem criar equipes quando essa modalidade estiver habilitada.

## RN-EQP-004 — Formação pelo organizador

O organizador pode formar equipes manualmente.

## RN-EQP-005 — Convites

Uma equipe pode receber integrantes por convite.

## RN-EQP-006 — Solicitação de entrada

Usuários podem solicitar entrada em equipes quando essa opção estiver disponível.

## RN-EQP-007 — Aceitação de convite

Um convite somente adiciona o usuário à equipe após aceitação.

## RN-EQP-008 — Rejeição de convite

O usuário pode rejeitar convite sem ser adicionado à equipe.

## RN-EQP-009 — Aprovação de solicitação

Uma solicitação de entrada depende de aprovação do responsável quando aplicável.

## RN-EQP-010 — Tamanho máximo

Uma equipe não pode ultrapassar o número máximo de integrantes.

## RN-EQP-011 — Tamanho mínimo

Uma equipe que não atingir o mínimo definido não deve ser considerada apta para competir.

## RN-EQP-012 — Equipe apta

Uma equipe somente deve ser considerada apta quando cumprir os critérios de participação do hackathon.

## RN-EQP-013 — Líder

Uma equipe pode possuir um líder ou responsável.

## RN-EQP-014 — Líder como integrante

O líder deve pertencer à própria equipe.

## RN-EQP-015 — Participação incompatível

Um usuário não deve integrar simultaneamente equipes incompatíveis dentro do mesmo hackathon quando as regras exigirem exclusividade.

## RN-EQP-016 — Desclassificação

O organizador pode desclassificar uma equipe.

## RN-EQP-017 — Motivo obrigatório

Toda desclassificação deve possuir motivo registrado.

## RN-EQP-018 — Histórico da desclassificação

Uma equipe desclassificada não deve ser apagada automaticamente.

## RN-EQP-019 — Estado da equipe

A equipe deve possuir estado coerente.

Estados previstos:

* em formação;
* apta;
* competindo;
* finalizada;
* desclassificada.

---

# 17. Submissões

## RN-SUB-001 — Participante elegível

Somente participante ou equipe elegível pode realizar submissão.

## RN-SUB-002 — Período de submissão

Submissões somente podem ser realizadas dentro do período permitido.

## RN-SUB-003 — Bloqueio antes da abertura

Envios não devem ser aceitos antes da abertura das submissões.

## RN-SUB-004 — Bloqueio após encerramento

Envios não devem ser aceitos após o prazo final.

## RN-SUB-005 — Múltiplas versões

O hackathon pode permitir múltiplas versões da submissão.

## RN-SUB-006 — Histórico obrigatório

Versões anteriores devem permanecer registradas.

## RN-SUB-007 — Data e horário

Cada versão deve manter o momento em que foi enviada.

## RN-SUB-008 — Última versão válida

Por padrão, a última versão válida enviada antes do prazo pode ser utilizada como versão oficial.

## RN-SUB-009 — Versão oficial identificável

Deve ser possível identificar qual versão está sendo considerada na avaliação.

## RN-SUB-010 — Submissões não devem ser sobrescritas

Uma nova versão não deve apagar silenciosamente as versões anteriores.

---

# 18. Critérios de Avaliação

## RN-CRT-001 — Múltiplos critérios

Um hackathon pode possuir vários critérios de avaliação.

## RN-CRT-002 — Critério definido pelo organizador

Os critérios são definidos pela organização do hackathon.

## RN-CRT-003 — Peso opcional

Um critério pode possuir peso quando o modelo de avaliação utilizar ponderação.

## RN-CRT-004 — Pesos variáveis

Os pesos não precisam ser iguais entre os critérios.

## RN-CRT-005 — Modelo flexível

A plataforma não deve impor um conjunto universal de critérios a todos os hackathons.

---

# 19. Jurados e Avaliações

## RN-AVL-001 — Múltiplos jurados

Uma equipe pode ser avaliada por vários jurados.

## RN-AVL-002 — Jurados associados ao hackathon

Um jurado deve estar associado ao hackathon correspondente para realizar avaliação oficial.

## RN-AVL-003 — Avaliação por critérios

As avaliações podem utilizar os critérios definidos pelo organizador.

## RN-AVL-004 — Observações

Uma avaliação pode possuir observações.

## RN-AVL-005 — Cálculo não obrigatório

A plataforma não é obrigada a calcular automaticamente a nota final.

## RN-AVL-006 — Resultado fornecido pelo organizador

O resultado final pode ser informado diretamente pelo organizador.

## RN-AVL-007 — Avaliação externa

O resultado pode ter origem em processo de avaliação externo à plataforma.

## RN-AVL-008 — Plataforma como meio de exibição

A plataforma pode atuar apenas como meio de registro e apresentação dos resultados.

## RN-AVL-009 — Sem bônus genérico

O conceito genérico de bônus de pontuação não faz parte do escopo atual.

---

# 20. Resultado e Ranking

## RN-RKG-001 — Resultado oficial

O organizador é responsável por definir ou registrar o resultado oficial.

## RN-RKG-002 — Ranking opcionalmente oculto

O ranking pode permanecer oculto durante o hackathon.

## RN-RKG-003 — Publicação controlada

O organizador define quando o ranking será exibido.

## RN-RKG-004 — Ranking parcial não obrigatório

A plataforma não é obrigada a exibir ranking em tempo real.

## RN-RKG-005 — Empate permitido

O evento pode permitir empate.

## RN-RKG-006 — Desempate configurável

Quando houver desempate, os critérios devem ser definidos pelo próprio evento.

## RN-RKG-007 — Plataforma não inventa desempate

A plataforma não deve aplicar critério de desempate não definido pelo organizador.

## RN-RKG-008 — Colocação histórica

Uma colocação oficial pode permanecer associada ao histórico do usuário ou equipe.

---

# 21. Emblemas e Troféus

## RN-EMB-001 — Emblema criado pelo evento

O emblema deve ser criado no contexto de um evento.

## RN-EMB-002 — Evento define significado

O evento é responsável por definir o significado do emblema.

## RN-EMB-003 — Concessão pela plataforma

A plataforma registra a concessão do emblema ao usuário.

## RN-EMB-004 — Usuário não concede emblemas

Usuários comuns não podem conceder emblemas oficiais a si próprios.

## RN-EMB-005 — Origem obrigatória

Um emblema concedido deve manter referência ao evento que o originou.

## RN-EMB-006 — Histórico permanente

A concessão deve permanecer registrada mesmo após o encerramento do evento.

## RN-EMB-007 — Alteração posterior

Mudanças futuras na definição do emblema não devem apagar o fato histórico de que ele foi concedido.

## RN-EMB-008 — Emblemas exclusivos

Um evento pode possuir emblemas exclusivos.

## RN-EMB-009 — Diferentes tipos de conquista

Um evento pode criar emblemas para diferentes conquistas.

Exemplos:

* participante;
* finalista;
* campeão;
* segundo lugar;
* terceiro lugar;
* melhor projeto;
* categoria especial.

---

# 22. Certificados

## RN-CER-001 — Certificado ligado ao evento

Todo certificado deve possuir relação com o evento que o originou.

## RN-CER-002 — Emissão controlada

Somente a organização ou a plataforma dentro das permissões definidas pode emitir certificados oficiais.

## RN-CER-003 — Usuário elegível

Certificados somente devem ser emitidos para usuários que atendam aos critérios definidos pelo evento.

## RN-CER-004 — Histórico

Certificados emitidos devem permanecer vinculados ao usuário.

## RN-CER-005 — Evento encerrado

O encerramento do evento não remove certificados já emitidos.

## RN-CER-006 — Certificado e emblema são conceitos diferentes

Certificado representa comprovação formal, enquanto emblema representa reconhecimento visual ou conquista.

---

# 23. Patrocinadores

## RN-PAT-001 — Empresa patrocinadora

Somente uma empresa cadastrada pode ser associada formalmente como patrocinadora.

## RN-PAT-002 — Múltiplos patrocinadores

Um evento pode possuir vários patrocinadores.

## RN-PAT-003 — Múltiplos eventos

Uma empresa pode patrocinar diferentes eventos.

## RN-PAT-004 — Organizador e patrocinador são papéis distintos

Uma empresa organizadora não deve ser automaticamente considerada patrocinadora.

## RN-PAT-005 — Mesmo ator, papéis diferentes

Uma empresa pode exercer ambos os papéis quando isso for explicitamente definido.

## RN-PAT-006 — Categorias configuráveis

Categorias de patrocínio podem ser definidas pelo próprio evento.

Exemplos:

* Platinum;
* Gold;
* Silver;
* Apoio.

## RN-PAT-007 — Categoria não obrigatória

A plataforma não deve exigir uma classificação fixa de patrocinadores.

---

# 24. Estandes

## RN-EST-001 — Estande relacionado a evento

Um estande deve estar vinculado a um evento.

## RN-EST-002 — Patrocinador relacionado

Um estande pode estar associado a um patrocinador.

## RN-EST-003 — Estande físico ou virtual

O estande pode representar presença física ou virtual.

## RN-EST-004 — Localização

Quando aplicável, o estande pode possuir localização própria dentro do evento.

---

# 25. Ofertas

## RN-OFE-001 — Oferta relacionada ao evento

Uma oferta deve estar associada a um evento.

## RN-OFE-002 — Oferta de patrocinador

Uma oferta pode estar vinculada a um patrocinador.

## RN-OFE-003 — Oferta não obrigatória

Patrocinadores não são obrigados a disponibilizar ofertas.

## RN-OFE-004 — Escopo promocional

Ofertas representam benefícios ou promoções e não alteram automaticamente inscrições ou resultados do evento.

---

# 26. Comunicação

## RN-COM-001 — Comunicado do organizador

O organizador pode emitir comunicados relacionados ao evento.

## RN-COM-002 — Público geral

Um comunicado pode ser direcionado a todos os participantes.

## RN-COM-003 — Público segmentado

Um comunicado pode ser direcionado a um grupo específico.

## RN-COM-004 — Segmentação por atividade

Participantes de determinada atividade podem receber comunicados específicos.

## RN-COM-005 — Segmentação por hackathon

Participantes de determinado hackathon podem receber comunicados específicos.

## RN-COM-006 — Segmentação por equipe

Equipes podem receber comunicados direcionados quando necessário.

## RN-COM-007 — Lista de espera

Participantes em lista de espera podem receber comunicação específica.

## RN-COM-008 — Comunicação vinculada ao contexto

Um comunicado deve possuir relação com o evento ou contexto que o originou.

---

# 27. Notificações

## RN-NTF-001 — Preferências personalizáveis

O usuário pode escolher quais categorias opcionais de notificação deseja receber.

## RN-NTF-002 — Categorias

As notificações podem ser classificadas como:

* essenciais;
* operacionais;
* sociais;
* promocionais.

## RN-NTF-003 — Notificações essenciais

Notificações essenciais podem permanecer ativas independentemente das preferências opcionais do usuário.

## RN-NTF-004 — Notificação de cancelamento

Usuários afetados devem poder ser informados quando um evento for cancelado.

## RN-NTF-005 — Mudança importante

Alterações relevantes de horário ou local podem gerar notificação.

## RN-NTF-006 — Atividade próxima

O sistema pode gerar lembrete de atividade próxima.

## RN-NTF-007 — Mudança de fase

A abertura ou encerramento de fase de hackathon pode gerar notificação.

## RN-NTF-008 — Convite para equipe

Convites de equipe devem poder gerar notificação ao usuário convidado.

## RN-NTF-009 — Solicitação para equipe

Solicitações de entrada devem poder gerar notificação ao responsável.

## RN-NTF-010 — Vaga disponível

Usuários em lista de espera podem ser notificados quando uma vaga for oferecida.

## RN-NTF-011 — Resultado publicado

A publicação de resultado pode gerar notificação.

## RN-NTF-012 — Emblema recebido

A concessão de um emblema pode gerar notificação.

## RN-NTF-013 — Certificado emitido

A emissão de certificado pode gerar notificação.

## RN-NTF-014 — Empresa seguida

A publicação de novo evento por empresa seguida pode gerar notificação.

## RN-NTF-015 — Lida e não lida

Uma notificação deve possuir estado que permita identificar se já foi visualizada.

## RN-NTF-016 — Preferências promocionais independentes

Notificações promocionais devem ser configuráveis separadamente das notificações operacionais.

---

# 28. Administração

## RN-ADM-001 — Papel administrativo

Administradores representam usuários com responsabilidades de gestão da plataforma.

## RN-ADM-002 — Verificação de empresa

A aprovação ou rejeição de empresas é uma responsabilidade administrativa.

## RN-ADM-003 — Aprovação de evento

A aprovação ou rejeição inicial de eventos é uma responsabilidade administrativa.

## RN-ADM-004 — Decisões registráveis

Decisões administrativas relevantes devem possuir resultado identificável.

## RN-ADM-005 — Rejeições justificadas

Rejeições administrativas de empresa ou evento devem permitir registro de justificativa.

---

# 29. Histórico e Preservação de Dados

## RN-HIS-001 — Eventos cancelados

Eventos cancelados devem permanecer como fatos históricos.

## RN-HIS-002 — Emblemas concedidos

Emblemas já concedidos devem permanecer no histórico.

## RN-HIS-003 — Certificados emitidos

Certificados emitidos devem permanecer no histórico.

## RN-HIS-004 — Submissões anteriores

Versões antigas de submissão devem permanecer disponíveis para histórico.

## RN-HIS-005 — Resultados

Resultados oficiais devem permanecer associados ao evento.

## RN-HIS-006 — Colocações

Colocações oficiais podem permanecer vinculadas ao perfil do participante.

## RN-HIS-007 — Desclassificação

A desclassificação de equipe deve ser registrada em vez de simplesmente apagar a equipe.

---

# 30. Coerência de Estados

## RN-ESTADO-001 — Estado válido

Toda entidade que possuir ciclo de vida deve assumir apenas estados definidos para ela.

## RN-ESTADO-002 — Estado coerente

O estado armazenado deve representar a situação real da entidade.

## RN-ESTADO-003 — Evento cancelado

Um evento cancelado não deve retornar automaticamente ao fluxo normal sem uma regra específica futura que permita isso.

## RN-ESTADO-004 — Equipe desclassificada

Uma equipe desclassificada não deve continuar sendo considerada competidora válida.

## RN-ESTADO-005 — Inscrição cancelada

Uma inscrição cancelada deixa de representar participação ativa.

## RN-ESTADO-006 — Inscrição rejeitada

Uma inscrição rejeitada não deve ser tratada como confirmada.

## RN-ESTADO-007 — Lista de espera

Participante em lista de espera não deve ser tratado como participante confirmado.

## RN-ESTADO-008 — Evento encerrado

Evento encerrado representa evento já concluído.

---

# 31. Regras de Consistência Geral

## RN-GER-001 — Integridade entre entidades

Uma entidade dependente não deve existir sem sua entidade principal quando a relação exigir isso.

## RN-GER-002 — Evento inexistente

Não pode existir inscrição associada a evento inexistente.

## RN-GER-003 — Atividade inexistente

Não pode existir inscrição em atividade inexistente.

## RN-GER-004 — Equipe inexistente

Não pode existir membro associado a equipe inexistente.

## RN-GER-005 — Hackathon inexistente

Não pode existir fase, desafio ou equipe vinculada a hackathon inexistente.

## RN-GER-006 — Emblema inexistente

Não pode existir concessão de emblema sem emblema correspondente.

## RN-GER-007 — Usuário inexistente

Não pode existir participação, certificado ou conquista ligada a usuário inexistente.

## RN-GER-008 — Empresa inexistente

Não pode existir vínculo de organização ou patrocínio com empresa inexistente.

---

# 32. Funcionalidades Fora do Escopo Atual

As regras abaixo ainda não serão detalhadas nesta fase porque dependem de uma decisão futura de escopo.

## Carteira interna

A ideia futura prevê:

* créditos por evento;
* saldo;
* compras internas;
* histórico de movimentações;
* estornos.

## Pagamentos internos

A ideia futura prevê:

* uso de créditos em produtos ou serviços;
* pagamentos dentro do evento;
* integração futura com meios de pagamento.

Esses módulos deverão receber um conjunto próprio de regras antes de serem implementados.

---

# 33. Resumo das Áreas Cobertas

Este documento possui regras relacionadas a:

* usuários;
* perfis;
* seguidores;
* empresas;
* verificação de empresas;
* eventos;
* descoberta;
* inscrições;
* programação;
* atividades;
* check-in;
* hackathons;
* fases;
* desafios;
* equipes;
* submissões;
* critérios;
* jurados;
* avaliações;
* ranking;
* emblemas;
* certificados;
* patrocinadores;
* estandes;
* ofertas;
* comunicação;
* notificações;
* administração;
* histórico;
* estados;
* integridade do domínio.

---

# 34. Regra de Manutenção do Documento

Sempre que uma funcionalidade alterar:

* comportamento;
* condição;
* restrição;
* permissão;
* estado;
* relacionamento;
* elegibilidade;

as regras afetadas neste documento devem ser revisadas.

Requisitos descrevem **o que o sistema oferece**.

Regras de negócio descrevem **sob quais condições essas funcionalidades podem acontecer**.
