# 🧠 Itaú Tech Coaches

> Ecossistema multiagente de mentoria técnica, arquitetural e de carreira — baseado em conteúdo público dos Itaú Tech Meetups.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Knowledge Base](https://img.shields.io/badge/Knowledge%20Base-9%20Mentors-blue)]()
[![Meetups](https://img.shields.io/badge/Meetups%20Processed-5-green)]()

---

## ✨ O que é este projeto?

O **Itaú Tech Coaches** é uma base de conhecimento estruturada para agentes de IA, construída a partir de gravações públicas dos **Itaú Tech Meetups**. Ele define personas de lideranças reais do Itaú Unibanco que atuam como mentores especializados em diferentes domínios de tecnologia, dados e carreira.

Você pode usar este repositório como:
- 📚 **Base de conhecimento** para treinar ou instruir agentes de IA
- 🤖 **Sistema multiagente** com roteamento por especialidade
- 🎓 **Material de estudo** para quem quer entrar e crescer em tech no Itaú

---

## 👥 Os 9 Mentores

| # | Mentor | Especialidade |
|---|--------|--------------|
| 1 | 🧑‍💻 **Priscila Silveira Rocha** | Engenharia de Software · Java · AWS · Microsserviços |
| 2 | 🎯 **Arthur de Azevedo** | Carreira · Recrutamento · Gupy · LinkedIn |
| 3 | 🏗️ **Ricardo Coelho** | Plataforma IARA · Data Mesh · Ontologias · AI Architecture |
| 4 | 💬 **Aline Pavan** | Iaí · Inteligência Itaú · Produtos Conversacionais · CX |
| 5 | ⚡ **Gabriel Pegorelli** | DevEx · Devin · Plataforma DEVA · Vibe Engineering · DORA |
| 6 | 🛡️ **Bárbara Correa** | Responsible AI · AI Red Teaming · LGPD · Guardrails |
| 7 | 🌱 **Mariana (Mari)** | Carreira na Era da IA · Academia de IA · ICTI · Cultura |
| 8 | ⚛️ **Dra. Samuraí Brito** | Computação Quântica · QML · VQC · IBM Quantum Network |
| 9 | 📊 **Helen Vasconcelos** | Data Mesh · Orange Flow · Apache Iceberg · Democratização de Dados |

---

## 🗂️ Estrutura do Repositório

```
itau-tech-coaches/
├── AGENTS.md                          # Orquestrador — roteamento por especialidade
├── README.md                          # Este arquivo
│
├── knowledge/
│   └── meetups/                       # Sínteses dos Itaú Tech Meetups
│       ├── meetup-ia-agentica-iai-iara.md
│       ├── meetup-devin-devex-inteligencia-itau.md
│       ├── meetup-deva-devin-escala-itau-2026.md
│       ├── meetup-quantum-computing-qml-itau.md
│       └── meetup-democratizacao-dados-investment-services.md
│
├── priscila-rocha/
│   ├── AGENTS.md
│   └── knowledge/
├── arthur-azevedo/
│   ├── AGENTS.md
│   └── knowledge/
├── ricardo-coelho/
│   ├── AGENTS.md
│   └── knowledge/
├── aline-pavan/
│   ├── AGENTS.md
│   └── knowledge/
├── gabriel-pegorelli/
│   ├── AGENTS.md
│   └── knowledge/
├── barbara-correa/
│   ├── AGENTS.md
│   └── knowledge/
├── mariana-rh/
│   ├── AGENTS.md
│   └── knowledge/
├── samurai-brito/
│   ├── AGENTS.md
│   └── knowledge/
└── helen-vasconcelos/
    ├── AGENTS.md
    └── knowledge/
```

---

## 🚀 Como usar com agentes de IA

### Com Antigravity / Google AI Studio
1. Clone este repositório no seu workspace
2. O arquivo raiz `AGENTS.md` atua como orquestrador e instrui o agente a consultar o mentor certo
3. Faça perguntas sobre Java, carreira, IA, dados, DevEx, quantum, etc.

### Com qualquer LLM via RAG
1. Indexe os arquivos `.md` em um vector store
2. Use o `AGENTS.md` raiz como system prompt base
3. Faça retrieval por especialidade

---

## 📋 Meetups Processados

| # | Título | Speakers | Temas |
|---|--------|----------|-------|
| 1 | IA Agêntica, Iaí e IARA | Ricardo Coelho, Aline Pavan, Bárbara Correa, Mariana | Agentes, Plataforma IARA, Governança |
| 2 | Devin & DevEx no Itaú | Gabriel Pegorelli, Giovana Jess, Evelyn Cristina | Coding Agents, Developer Experience |
| 3 | DEVA em Escala (2026) | Gabriel Pegorelli | Plataforma DEVA, Vibe Engineering, 17k usuários |
| 4 | Computação Quântica | Dra. Samuraí Brito, José Vittor | QML, VQC, IBM Quantum Network |
| 5 | Democratização de Dados | Helen Vasconcelos, Fábio Alves, Maria Emília | Orange Flow, Iceberg, Jornada Dados & IA |

---

## ⚠️ Aviso Legal

Este projeto é baseado em **conteúdo público** divulgado pelo Itaú Unibanco em seus canais oficiais (YouTube, meetups abertos). Não contém dados internos, sigilosos ou proprietários. As personas de líderes são construídas exclusivamente a partir de falas e apresentações públicas.

Este repositório **não é oficial** do Itaú Unibanco.

---

## 📄 Licença

MIT — sinta-se livre para usar, adaptar e contribuir.
