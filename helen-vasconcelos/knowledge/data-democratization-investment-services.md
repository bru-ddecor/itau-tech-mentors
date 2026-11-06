# Conhecimento Técnico e Cultural: Democratização de Dados em Investment Services

## 1. Contexto e Estratégia da Comunidade de Investment Services

A comunidade de **Investment Services** do Itaú Unibanco opera sobre três frentes de infraestrutura de mercado:

- **Administração Fiduciária de Fundos de Investimento**
- **Custódia de Ativos**
- **Controladoria**

A estratégia da área é sustentada por **3 pilares fundamentais**:

1. **Cliente no centro**: toda decisão parte da experiência do cliente e dos parceiros de negócio, não da conveniência técnica;
2. **Jornada estruturada**: processos claros com SLEs (Service Level Expectations) definidos e mensuráveis;
3. **Governança**: rastreabilidade, auditabilidade e conformidade como requisitos não-negociáveis em toda a cadeia de dados.

---

## 2. O Problema Original: Dispersão de Dados e Dependência Tech → Negócio

Antes da iniciativa de democratização, os sintomas eram claros:

| Sintoma | Impacto |
|---|---|
| Dados dispersos em múltiplos sistemas legados | Nenhuma visão integrada ou confiável |
| Decisões dependiam de extração manual por TI | Latência de dias para análises simples |
| Times de negócio sem autonomia analítica | Gargalo crônico no time de tecnologia |
| Nenhum self-service de dados | Baixa velocidade de resposta ao mercado |

**Objetivo da iniciativa**: Eliminar a dependência e colocar os dados nas mãos de quem precisa deles, no momento certo, com qualidade e governança.

---

## 3. Arquitetura Técnica Completa

### 3.1 Fluxo de Dados — Pipeline End-to-End

```
[Sistemas Legados / Fontes de Dados]
           ↓
       Apache Kafka
    (Ingestão em Tempo Real)
           ↓
      Orange Flow (OR Flow)
  (Framework Interno de Orquestração)
           ↓
    AWS Step Functions + Lambda
   (Orquestração + Processamento Serverless)
           ↓
       Apache Iceberg
    (Open Table Format — OTF)
           ↓
         Data Mesh
  (Domínios de Dados com Ownership Descentralizado)
           ↓
  [Consumidores: Analytics, APIs, GenAI, Self-service]
```

**SLE (Service Level Expectation) de ponta a ponta: 10 minutos.**

### 3.2 Componentes e Papéis

| Componente | Função |
|---|---|
| **Apache Kafka** | Ingestão de eventos em streaming com desacoplamento entre produtores e consumidores |
| **Orange Flow (OR Flow)** | Framework interno de orquestração sobre Step Functions (ver seção 4) |
| **AWS Step Functions** | Motor de orquestração dos workflows de dados (350.000 execuções/dia) |
| **AWS Lambda** | Processamento serverless das transformações (2,8 milhões de invocações/dia na camada base) |
| **AWS Glue** | Jobs ETL de maior complexidade, suportados nativamente pelo Orange Flow |
| **Apache Iceberg** | Armazenamento em OTF com schema evolution, time travel e compatibilidade multi-engine |
| **Data Mesh** | Arquitetura de domínios autônomos com governança centralizada |

---

## 4. Orange Flow (OR Flow) — Detalhamento Técnico

### 4.1 O que é o Orange Flow?

O **Orange Flow** (também referenciado como **OR Flow**) é um **framework de orquestração de dados desenvolvido internamente** pelo time de Investment Services do Itaú Unibanco. Seu propósito principal é **abstrair a complexidade do AWS Step Functions**, permitindo que os engenheiros de dados foquem na lógica de negócio e não na complexidade de orquestração de workflows.

### 4.2 Funcionalidades Detalhadas

1. **Reúso de Componentes**
   - Biblioteca de componentes reutilizáveis de transformação, validação e integração;
   - Redução de código duplicado e padronização dos pipelines da comunidade.

2. **Monitoramento em Tempo Real**
   - Visibilidade do estado de cada execução em tempo real;
   - Alertas e notificações configuráveis por pipeline.

3. **Suporte a Fluxos Event-Driven e Agendados**
   - Pipelines acionados por eventos do Kafka (event-driven);
   - Pipelines com execução agendada (cron-based);
   - Flexibilidade para combinar os dois modos.

4. **Suporte a AWS Glue e Lambda**
   - Abstração unificada para diferentes engines de processamento;
   - O desenvolvedor escolhe o engine mais adequado para cada etapa sem mudar o modelo mental de orquestração.

5. **Replay a partir do Ponto de Falha**
   - Capacidade crítica de idempotência: em caso de falha, o pipeline pode ser reexecutado a partir do passo que falhou, sem reprocessar dados já processados com sucesso;
   - Elimina retrabalho e reduz o risco de duplicação de dados.

6. **Portal / Cockpit de Observabilidade**
   - Interface visual (portal web interno) para acompanhamento operacional de todos os fluxos;
   - Permite que analistas de operações monitorem o status de pipelines sem precisar acessar o console AWS.

### 4.3 HR Flow — Validação com IA Integrada

O **HR Flow** é uma nova funcionalidade construída sobre o Orange Flow que incorpora **validação por Inteligência Artificial diretamente dentro do pipeline de dados**:

- Regras de qualidade e conformidade verificadas de forma automatizada e inteligente;
- A IA atua como uma camada de validação integrada ao fluxo, sem necessidade de intervenção manual;
- Permite detectar anomalias, inconsistências e desvios de qualidade antes que os dados cheguem aos consumidores.

---

## 5. Apache Iceberg — Decisão e Justificativa

### 5.1 Comparativo de Open Table Formats

| Critério | Apache Iceberg | Delta Lake | Apache Hudi |
|---|---|---|---|
| **Compatibilidade com Data Mesh do Itaú** | ✅ Alta | ⚠️ Média | ⚠️ Média |
| **Interoperabilidade multi-engine** | ✅ Athena, Spark, Trino, Flink | ⚠️ Foco Databricks | ⚠️ Foco Hive/Spark |
| **Schema Evolution** | ✅ Nativa e robusta | ✅ Suportada | ✅ Suportada |
| **Time Travel** | ✅ Nativo | ✅ Nativo | ✅ Suportado |
| **Decisão** | ✅ **Escolhido** | ❌ | ❌ |

### 5.2 Por que Iceberg no Data Mesh?

O Data Mesh exige que domínios diferentes possam consumir dados uns dos outros sem forte acoplamento. O Iceberg oferece:

- **Abertura de ecossistema**: qualquer engine pode ler/escrever dados Iceberg sem vendor lock-in;
- **Metadados ricos**: catalogo de partições e snapshots que permitem auditoria e rastreabilidade;
- **Evolução sem downtime**: schema evolution e partition evolution sem quebrar consumers existentes.

---

## 6. Os Grandes Números da Operação

| Métrica | Valor Oficial |
|---|---|
| **Tabelas democratizadas** | **3.100 tabelas** |
| **Cobertura de dados relevantes** | **40% dos dados relevantes** |
| **Cobertura de fundos de investimento** | **100% dos dados de fundos** |
| **Volume de eventos/dia** | **600.000 eventos/dia** |
| **Execuções de Step Functions/dia** | **350.000 execuções/dia** |
| **Linhas brutas processadas** | **4.000.000 de linhas brutas** |
| **Invocações de Lambda/dia (camada base)** | **2.800.000 Lambdas/dia** |
| **Invocações de Lambda/dia (camada especializada)** | **~5.600.000 Lambdas/dia** (dobro da camada base) |
| **SLE de ponta a ponta** | **10 minutos** |

> **Nota**: Os valores da camada especializada são inferidos pela declaração de que ela "dobra" os números da camada base.

---

## 7. Jornada Dados & IA — Programa Cultural de Democratização

### 7.1 Conceito e Objetivo

A **Jornada Dados & IA** é o braço cultural da iniciativa de democratização. Enquanto a arquitetura técnica resolve o problema de acesso aos dados, a Jornada resolve o problema de **engajamento e capacitação dos colaboradores** para usar esses dados.

A premissa é simples: **tecnologia sem cultura não gera resultado**. Ter 3.100 tabelas disponíveis não adianta se os times de negócio não souberem ou não quiserem usá-las.

### 7.2 Mecânica de Gamificação

- **Ranking de colaboradores** com pontuação pública dentro da comunidade;
- **Pontos por etapa do case**: cada fase de desenvolvimento de um caso de uso (da ideia à produção) gera pontos;
- **Visibilidade e reconhecimento**: os "campeões de dados" ganham destaque na comunidade interna;
- **Estímulo à progressão**: a mecânica encoraja colaboradores a levar seus casos adiante, não parar na fase de ideia.

### 7.3 Métricas da Jornada Dados & IA

| Métrica | Valor Oficial |
|---|---|
| **Casos em pipeline de produção** | **255 casos** |
| **Casos em desenvolvimento** | **35%** |
| **Casos concluídos** | **27%** |
| **Colaboradores treinados em GenAI e dados** | **97%** |
| **Colaboradores ativamente construindo casos** | **41%** |

---

## 8. Os 4 Pilares de Acesso a Dados e IA

A jornada foi estruturada com 4 níveis de acesso progressivos, do mais acessível ao mais estratégico:

### Pilar 1 — Simple AI Journey (Baixa Complexidade Técnica)
- **Ferramentas**: Microsoft Copilot, StackSpot AI, Power Automate
- **Perfil de usuário**: Qualquer colaborador, sem necessidade de programação
- **Objetivo**: Automação de tarefas repetitivas, sumarização de documentos, geração de e-mails e relatórios

### Pilar 2 — Analytics & Data Visualization
- **Ferramentas**: Amazon Athena (SQL) + Amazon QuickSight (dashboards)
- **Perfil de usuário**: Analistas de negócio e gestores com noção de SQL
- **Objetivo**: Consultas autônomas às tabelas democratizadas, criação de dashboards sem depender de TI

### Pilar 3 — Self-Service com APIs e GenAI (Integração Não-Sistêmica)
- **Ferramentas**: APIs internas, modelos de linguagem generativos
- **Perfil de usuário**: Profissionais com conhecimento técnico moderado
- **Objetivo**: Automações e integrações com linguagem natural, sem desenvolvimento de sistemas formais

### Pilar 4 — Jornada Estratégica (Cases Complexos com Suporte de Squad)
- **Ferramentas**: Squads especializados de dados e IA
- **Perfil de usuário**: Líderes de negócio com casos de alto impacto
- **Objetivo**: Modelos preditivos, pipelines complexos, produtos de dados estratégicos com suporte técnico dedicado

---

## 9. Cases de Negócio Produzidos

### 9.1 OCR para Documentos de Fundos (PDF)
- **Problema**: Documentos de fundos de investimento chegam em PDF e precisavam de extração manual de dados;
- **Solução**: OCR com IA para extração automatizada e estruturada das informações relevantes;
- **Impacto**: Eliminação de trabalho manual e redução de erros de digitação.

### 9.2 Monitoramento de Sentimento em Notícias Financeiras
- **Problema**: Necessidade de monitorar notícias sobre ativos do portfólio de fundos em tempo real;
- **Solução**: Pipeline de coleta de notícias + classificação de sentimento (positivo/negativo/neutro) com GenAI;
- **Impacto**: Alertas automáticos sobre eventos de mercado que afetam ativos monitorados.

### 9.3 Conciliação de Cotas de Fundos
- **Problema**: Processo manual e sujeito a erros de conciliação de cotas entre sistemas;
- **Solução**: Automação com validação inteligente do processo de conciliação;
- **Impacto**: Redução de erros operacionais e ganho de velocidade no fechamento.

### 9.4 Auditoria de Despesas por Leitura de Imagem
- **Problema**: Comprovantes de despesas chegavam em formato de imagem (fotos, scans), exigindo conferência manual;
- **Solução**: Leitura automatizada de imagens com IA para extração e validação de dados de despesas;
- **Impacto**: Auditoria mais ágil, rastreável e com menor dependência de revisão humana item a item.

---

## 10. A Equipe — Os "YouTubers"

O time de dados de Investment Services ganhou o apelido de **"YouTubers"** por sua postura de criadores de conteúdo e evangelizadores da cultura de dados — criando tutoriais, compartilhando aprendizados e engajando a comunidade interna.

| Fase | Tamanho da Equipe |
|---|---|
| Início | 3 pessoas |
| Fase intermediária | 5 pessoas |
| Equipe atual | **8 "YouTubers"** |

A evolução da equipe acompanhou o crescimento do impacto: de 3 pessoas democratizando as primeiras tabelas à equipe de 8 responsável por 3.100 tabelas e 600 mil eventos/dia.

---

## 11. Decisões Arquiteturais e Suas Justificativas

| Decisão | Alternativas Avaliadas | Justificativa da Escolha |
|---|---|---|
| **Apache Iceberg como OTF** | Delta Lake, Apache Hudi | Maior interoperabilidade com o Data Mesh do Itaú, sem vendor lock-in, schema evolution robusta |
| **Orange Flow como orquestrador** | Step Functions puro | Abstração de complexidade, reúso de componentes, replay de falhas, observabilidade integrada |
| **Kafka para ingestão** | Polling, batch tradicional | Event-driven real-time, desacoplamento produtor/consumidor, suporte a 600 mil eventos/dia |
| **Lambda para processamento** | EC2, ECS, Glue puro | Serverless = custo proporcional ao uso, escalabilidade automática, 2,8M invocações/dia sem gestão de servidor |
| **Gamificação na jornada cultural** | Treinamento tradicional | Engajamento ativo: 41% construindo casos vs. consumo passivo de conteúdo |

---

## 12. Pontos de Conexão com o Ecossistema do Itaú

- **Plataforma IARA** (Ricardo Coelho): Os casos de GenAI da Jornada Dados & IA podem ser potencializados com os modelos e orquestração da IARA;
- **Data Mesh do Itaú** (Ricardo Coelho): A implementação de Investment Services é um exemplo prático de Data Mesh em um domínio de alta complexidade regulatória;
- **Academia de IA** (Mariana — RH): O treinamento de 97% dos colaboradores em GenAI conecta-se com a Academia de IA do banco;
- **StackSpot AI** (Gabriel Pegorelli — DevEx): Ferramenta presente no Pilar 1 (Simple AI Journey), conectando democratização de dados com developer experience.
