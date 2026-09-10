# MAPA DA FASE 1

## Estrutura Prevista

```text
projeto/
│
├── README.md
├── package.json
├── next.config.js
├── .env
├── .env.example
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
    ├── app/
    │   ├── api/
    │   │   ├── auth/
    │   │   ├── usuarios/
    │   │   ├── empresas/
    │   │   ├── eventos/
    │   │   ├── inscricoes/
    │   │   ├── atividades/
    │   │   ├── hackathons/
    │   │   ├── equipes/
    │   │   ├── submissoes/
    │   │   ├── ranking/
    │   │   ├── emblemas/
    │   │   ├── certificados/
    │   │   └── notificacoes/
    │   │
    │   └── ...
    │
    ├── services/
    │   ├── usuario/
    │   ├── empresa/
    │   ├── evento/
    │   ├── inscricao/
    │   ├── atividade/
    │   ├── hackathon/
    │   ├── equipe/
    │   └── notificacao/
    │
    ├── repositories/
    │
    ├── models/
    │
    ├── dto/
    │
    ├── validators/
    │
    ├── utils/
    │
    └── config/
```

## Observação

Este mapa representa a estrutura prevista.

Os arquivos de código devem ser criados de forma incremental, conforme as Sprints.

Não é necessário criar antecipadamente todos os arquivos representados neste mapa.
