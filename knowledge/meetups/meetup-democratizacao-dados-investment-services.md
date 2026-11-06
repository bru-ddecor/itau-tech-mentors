# Síntese Oficial: Itaú Tech Meetup — Investment Services: Democratização de Dados

**Evento**: Itaú Tech Meetup  
**Tema**: Democratização de Dados na Comunidade de Investment Services  
**Participantes**:
- **Helen Vasconcelos**: Gerente de Tecnologia — Dados (Investment Services, Itaú Unibanco)
- **Fábio Alves Rocha**: Chapter de Engenharia de Dados (Investment Services, Itaú Unibanco)
- **Maria Emília Gomes**: Data Product Manager (Investment Services, Itaú Unibanco)

---

## 1. Contexto: A Comunidade de Investment Services

A área de **Investment Services** do Itaú Unibanco é responsável pela infraestrutura de mercado do banco, operando sobre três grandes frentes:

- **Fundos de Investimento** (Administração Fiduciária)
- **Custódia de Ativos**
- **Controladoria**

A estratégia da área se estrutura sobre **3 pilares fundamentais**:

1. **Cliente no centro** — toda decisão arquitetural e cultural parte da experiência do cliente e dos parceiros de negócio;
2. **Jornada estruturada** — processos claros, mensuráveis e com SLEs (Service Level Expectations) definidos;
3. **Governança** — rastreabilidade, auditabilidade e conformidade como requisitos não-negociáveis.

---

## 2. O Desafio: Dados Dispersos e Dependência Tecnológica

Antes da iniciativa de democratização, o cenário era:

- **Dados dispersos** em múltiplos sistemas legados sem integração centralizada;
- **Decisões demoravam dias** para serem tomadas, pois dependiam de extração manual de dados por equipes técnicas;
- **Times de negócio sem autonomia** — para qualquer análise, era necessário abrir chamado e aguardar o time de TI;
- **Alta dependência tech → negócio**, gerando gargalo de entrega e baixa velocidade de resposta ao mercado.

O objetivo da iniciativa foi inverter essa dinâmica: **colocar os dados nas mãos de quem precisa deles, no momento em que precisam**, com qualidade, governança e rastreabilidade.

---

## 3. A Arquitetura Construída

### Pipeline de Dados — Fluxo Completo

```
Sistemas Legados
      ↓
   Kafka (Ingestão de Eventos em Tempo Real)
      ↓
  Orange Flow (OR Flow — Framework Interno)
      ↓
  AWS Step Functions + Lambda
      ↓
  Apache Iceberg (Open Table Format)
      ↓
  Data Mesh (Domínios de Dados)
      ↓
  Consumidores (Analytics, APIs, GenAI, Self-service)
```

**SLE (Service Level Expectation) de ponta a ponta: 10 minutos.**

### Componentes Técnicos

| Componente | Papel na Arquitetura |
|---|---|
| **Apache Kafka** | Ingestão de eventos em tempo real, desacoplamento entre produtores e consumidores |
| **Orange Flow (OR Flow)** | Framework interno de orquestração sobre Step Functions (ver seção 4) |
| **AWS Step Functions** | Orquestração dos fluxos de dados (350 mil execuções/dia) |
| **AWS Lambda** | Processamento serverless das transformações de dados (2,8 milhões/dia na camada base; dobra na camada especializada) |
| **AWS Glue** | Suportado pelo Orange Flow para jobs de ETL mais pesados |
| **Apache Iceberg** | Formato de tabela aberto (OTF) para armazenamento no Data Mesh |
| **Data Mesh** | Arquitetura de domínios de dados com ownership descentralizado |

---

## 4. Orange Flow (OR Flow) — O Framework Interno

O **Orange Flow** (também chamado de **OR Flow**) é um framework de orquestração desenvolvido internamente pelo time de Investment Services para **abstrair a complexidade do AWS Step Functions**, tornando o desenvolvimento de pipelines mais simples, padronizado e reutilizável.

### Funcionalidades do Orange Flow

1. **Reúso de Componentes** — componentes prontos de transformação e integração reutilizáveis entre pipelines;
2. **Monitoramento em Tempo Real** — visibilidade do estado de cada execução em produção;
3. **Fluxos Event-Driven e Agendados** — suporte a pipelines acionados por eventos (Kafka) e por agendamento (cron);
4. **Suporte a Glue e Lambda** — abstração unificada para diferentes engines de processamento;
5. **Replay a partir do Ponto de Falha** — capacidade de reprocessar execuções falhas sem reiniciar do zero, garantindo idempotência;
6. **Portal/Cockpit de Observabilidade** — interface visual para acompanhamento operacional dos fluxos em produção.

### HR Flow — Validação com IA Integrada

Uma evolução recente do Orange Flow é o **HR Flow**, uma nova funcionalidade que incorpora **validação com Inteligência Artificial diretamente dentro do pipeline de dados**. Isso permite que regras de qualidade e conformidade sejam verificadas de forma automatizada e inteligente ao longo da jornada de processamento, sem intervenção manual.

---

## 5. Apache Iceberg — A Escolha do Formato

### Por que Apache Iceberg?

O time avaliou os três principais **Open Table Formats (OTF)** do mercado:

| Formato | Decisão |
|---|---|
| **Apache Iceberg** | ✅ **Escolhido** |
| **Delta Lake** | ❌ Não escolhido |
| **Apache Hudi** | ❌ Não escolhido |

O Apache Iceberg foi escolhido por ser o mais alinhado aos requisitos do **Data Mesh** da Itaú, especialmente no que tange à interoperabilidade entre domínios, suporte a schema evolution, time travel e compatibilidade com múltiplos engines de consulta (Athena, Spark, Trino).

---

## 6. Os Grandes Números da Democratização

| Métrica | Valor |
|---|---|
| **Tabelas democratizadas** | **3.100 tabelas** (40% dos dados relevantes; 100% dos dados de fundos de investimento) |
| **Eventos processados por dia** | **600 mil eventos/dia** |
| **Execuções de Step Functions por dia** | **350 mil execuções/dia** |
| **Linhas brutas processadas** | **4 milhões de linhas brutas** |
| **Invocações de Lambda por dia** | **2,8 milhões/dia** (camada base; a camada especializada dobra esse número) |
| **SLE de ponta a ponta** | **10 minutos** |

---

## 7. Jornada Dados & IA — A Camada Cultural

A dimensão técnica foi acompanhada por uma profunda **transformação cultural** chamada **"Jornada Dados & IA"**, liderada pela equipe com gamificação para engajar os colaboradores na construção de casos de uso com dados e IA.

### Mecânica de Gamificação

- **Ranking e pontuação por etapa do caso**: cada estágio de desenvolvimento de um caso de uso (da ideia ao piloto, do piloto à produção) gera pontos para o colaborador;
- **Visibilidade e reconhecimento** dos "campeões de dados" na comunidade interna.

### Números da Jornada Dados & IA

| Métrica | Valor |
|---|---|
| **Casos em pipeline de produção** | **255 casos** |
| **Casos em desenvolvimento** | **35%** do total |
| **Casos concluídos** | **27%** do total |
| **Colaboradores treinados em GenAI e fundamentos de dados** | **97%** |
| **Colaboradores ativamente construindo casos** | **41%** |

---

## 8. Os 4 Pilares da Jornada de Dados & IA

A jornada foi estruturada em **4 pilares de acesso** aos dados e à IA, do mais simples ao mais estratégico:

### Pilar 1 — Simple AI Journey (Low-Code)
- Ferramentas: **Microsoft Copilot**, **StackSpot AI**, **Power Automate**
- Perfil: Qualquer colaborador sem conhecimento técnico profundo
- Objetivo: Automação de tarefas do dia a dia, geração de conteúdo, sumarização de documentos

### Pilar 2 — Analytics & Data Visualization
- Ferramentas: **Amazon Athena** (consultas SQL) + **Amazon QuickSight** (visualização e dashboards)
- Perfil: Analistas de negócio e gestores com noção de SQL
- Objetivo: Consultas autônomas às tabelas democratizadas, criação de dashboards e relatórios sem dependência de TI

### Pilar 3 — Self-Service com APIs e GenAI (Integração Não-Sistêmica)
- Ferramentas: APIs internas, modelos de linguagem generativos
- Perfil: Profissionais com conhecimento técnico moderado
- Objetivo: Criação de automações e integrações não-sistêmicas com dados em linguagem natural

### Pilar 4 — Jornada Estratégica (Casos Complexos com Suporte de Squad)
- Ferramentas: Squads especializados de dados e IA
- Perfil: Líderes de negócio com casos de alto impacto e complexidade
- Objetivo: Desenvolvimento de modelos preditivos, pipelines complexos e produtos de dados estratégicos

---

## 9. Cases de Negócio Produzidos

| Case | Descrição |
|---|---|
| **OCR para documentos de fundos** | Extração automatizada de dados de documentos PDF de fundos de investimento com OCR + IA |
| **Monitoramento de sentimento em notícias** | Classificação de notícias financeiras com GenAI para medir sentimento sobre ativos monitorados |
| **Conciliação de cotas** | Automação do processo de conciliação de cotas de fundos com validação inteligente |
| **Auditoria de despesas por imagem** | Leitura e validação automatizada de comprovantes e imagens de despesas |

---

## 10. Evolução da Equipe — Os "YouTubers"

O time responsável pela iniciativa ficou conhecido internamente pelo apelido carinhoso de **"YouTubers"** — uma referência à sua postura de criadores de conteúdo e evangelizadores da cultura de dados dentro da comunidade de Investment Services.

| Fase | Tamanho da Equipe |
|---|---|
| Início da iniciativa | 3 pessoas |
| Fase intermediária | 5 pessoas |
| Equipe atual | **8 "YouTubers"** |

---

## 11. Principais Aprendizados e Mensagens do Meetup

1. **Dados não são problema de TI — são problema de negócio.** A democratização só funciona quando os times de negócio assumem ownership dos seus domínios de dados.
2. **Abstração é habilitadora.** O Orange Flow existe para remover a complexidade do Step Functions do dia a dia dos engenheiros, acelerando a entrega e padronizando a operação.
3. **A cultura come a estratégia no café da manhã.** A Jornada Dados & IA com gamificação foi tão importante quanto a arquitetura técnica. Ter 97% dos colaboradores treinados e 41% ativamente construindo casos é o resultado de um programa cultural consistente.
4. **Comece pelo problema de negócio, não pela tecnologia.** Cada case nasceu de uma dor real do negócio, não de uma vontade de testar uma tecnologia nova.
5. **Governança e autonomia não são opostos.** O Data Mesh com Apache Iceberg permite que domínios sejam autônomos sem abrir mão da rastreabilidade e da conformidade.
6. **Equipes pequenas com propósito claro constroem muito.** De 3 para 8 pessoas, o time democratizou 3.100 tabelas e processou 600 mil eventos por dia.
