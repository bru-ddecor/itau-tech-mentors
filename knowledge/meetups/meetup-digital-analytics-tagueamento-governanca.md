# Meetup Itaú Tech — Digital Analytics, SDK Analytics, Tagueamento e Governança de Dados

**Evento:** Itaú Tech Meetup — 6ª Edição  
**Tema:** Como o Itaú construiu uma plataforma completa de Digital Analytics do zero  
**Apresentadoras:**
- **Mariana Alves** — Líder/Especialista de Digital Analytics
- **Isabela Rangel (Isa)** — Especialista de Digital Analytics

---

## 1. Contexto Estratégico

O time de Digital Analytics do Itaú opera em um cenário de escala sem precedentes:

- **95%** das interações de clientes Pessoa Física são digitais
- **88%** das interações de clientes Pessoa Jurídica são digitais
- **72%** das interações de atendimento já utilizam IA
- O Digital Analytics é a espinha dorsal de dados comportamentais que alimenta decisões de produto, personalização, prevenção de fraudes e otimização de campanhas

Essa realidade coloca o time como peça central na estratégia "Um Itaú" / "Antaú": banco unificado, experiência integrada e inteligente, com dados como produto de primeira classe.

---

## 2. O Ponto de Partida — O Problema

### Escala do Caos

Antes da plataforma atual, o SuperApp do Itaú carregava:

- **6 milhões de nomes de eventos distintos** em apenas um app
- **23.000 telas únicas** mapeadas no ecossistema
- Eventos genéricos (botões nomeados de múltiplas formas, taxonomias variadas sem padrão)
- Valores sistêmicos, valores inválidos e até **emojis** tagueados como dados
- Ecossistema completamente fragmentado: sem padronização, sem governança

### Problemas Operacionais

| Dimensão | Problema |
|---|---|
| **Governança** | Nenhum padrão de nomenclatura ou estrutura de dados |
| **Developer Experience** | Alta sobrecarga cognitiva — múltiplas ferramentas não integradas, cada squad reinventando a roda |
| **Latência** | Alta dependência do Google para entrega de dados → dados chegavam com **até 2 dias de atraso** |
| **Timeliness** | Sem dados em tempo próximo ao real (*near-real-time*) |
| **Escala** | **4 bilhões de hits/dia** exigiam infraestrutura robusta e resiliente |
| **Pressão externa** | Deadline de migração do GA4 (encerramento do Google Universal Analytics em 1º de julho de 2024) |

---

## 3. A Solução — 4 Pilares da Plataforma

A plataforma foi construída sobre 4 pilares interdependentes:

```
┌──────────────────────────────────────────────────────────────┐
│                   PLATAFORMA DIGITAL ANALYTICS               │
│                                                              │
│  Pilar 1: SDK Analytics      Pilar 2: Data Maestro          │
│  (coleta padronizada)         (roteamento inteligente)       │
│                                                              │
│  Pilar 3: Governança          Pilar 4: Arquitetura de       │
│  (PIT + ToolKit + Datadiva)   Distribuição (Cross-Cloud)    │
└──────────────────────────────────────────────────────────────┘
```

---

### Pilar 1 — SDK Analytics: Simples, Escalável, Desacoplado

#### O que é
Um SDK modular conectado a **todos os canais do banco** — SuperApp, Bankline, App Empresas, ION e demais canais digitais. É o ponto único de coleta de dados comportamentais.

#### Princípio Central
> **"Um único tag → distribui dados para múltiplos destinos"**

O desenvolvedor envia um evento uma única vez. O SDK cuida de rotear para todas as ferramentas e destinos configurados.

#### Benefícios para Desenvolvedores
- Elimina a necessidade de expertise em ferramentas específicas de analytics
- Elimina dependência de ferramentas de terceiros (adicionar ou remover uma ferramenta não requer mudança no código da aplicação)
- **Minimum data sanitization:** funcionalidade que **bloqueia dados fora do padrão na origem da coleta**, antes de qualquer processamento downstream

#### Resultado Técnico
- **Redução de 50% no tamanho do SDK**
- **Redução de 84% no tempo de carregamento da plataforma do SuperApp**

---

### Pilar 2 — Data Maestro: Orquestrador de Roteamento de Dados

#### O que é
O **Data Maestro** é o orquestrador responsável por definir para onde cada dado vai — qual ferramenta recebe qual sinal.

#### Princípio
> Times de negócio decidem quais dados vão para quais ferramentas. Nem todos os dados precisam ir para todas as ferramentas.

#### Destinos Suportados
- Ferramentas de **CRM**
- Plataformas de **mídia e publicidade**
- Ferramentas de **digital analytics**
- Plataformas de **analytics de experiência**
- Outros destinos customizados

O Data Maestro desacopla a lógica de negócio (o que coletar e para quem enviar) da lógica técnica (como coletar), habilitando times de produto a tomarem decisões de roteamento sem depender de engenharia.

---

### Pilar 3 — Governança: A Tríade PIT + ToolKit Analytics + Datadiva

#### 3.1 — Padrão Itaú de Taguear (PIT)

O PIT é o framework de padronização que definiu as **regras do jogo** para todo o ecossistema de coleta.

**A transformação central:**
> De **6 milhões de nomes de eventos distintos** para **47 tipos de eventos** validados em tempo de execução.

**Estrutura do PIT:**
| Categoria | Descrição |
|---|---|
| **47 tipos de eventos** | Nomenclatura padronizada e validada em real-time na execução |
| **Parâmetros obrigatórios** | Campos que toda tag deve conter, sem exceção |
| **Parâmetros opcionais** | Campos contextuais disponíveis quando aplicável |
| **Variáveis de sessão** | Capturadas automaticamente dentro de cada sessão |
| **Variáveis globais persistentes** | Coletadas automaticamente em todos os eventos |

O **guard rail** do PIT opera no SDK: dados que não estejam no padrão são bloqueados na coleta, não chegando às camadas downstream.

#### 3.2 — Tool Kit Analytics: O Front-End da Plataforma

O Tool Kit Analytics é a interface de governança para squads e times de produto — o **facilitador técnico** que torna a governança operacional no dia a dia.

**Funções principais:**
- **Automatização de processos**: reduz trabalho manual repetitivo na gestão de tagueamento
- **Gestão de Textpacks (Texpack)**: o "mapa de métricas" (documento de especificação técnica) de cada jornada — no Itaú, chamado de **Texpack**. Especifica quais eventos e parâmetros devem ser coletados em cada tela/interação
- **Centralização da visão de dados**: um único ponto de verdade sobre o que está sendo tagueado
- **Aceleração de insights**: times chegam mais rápido às perguntas de negócio
- **Conexão com controle de jornadas**: integrado ao time de CEX (Customer Experience), vinculado a **IDs de jornada** específicos
- **Camada de homologação**: em evolução contínua para validar implementações antes de produção

> O Tool Kit Analytics é o **front-end** da plataforma de governança. O SDK Analytics é o **back-end**.

#### 3.3 — Datadiva: Plataforma de IA Multi-Agente para Self-Service

O **Datadiva** é a camada de democratização e inteligência que acompanha o usuário do início ao fim da sua jornada com dados de analytics.

**Cobertura da jornada:**
```
[Momento do Tagueamento] → [Documentação] → [Guia de Texpack] → [Consulta de Tabelas] → [Sugestão de Bases Analíticas]
```

**Como funciona:**
- Plataforma de **IA com múltiplos agentes** especializados em cada etapa
- Dicas de query e como consumir tabelas de dados
- Sugestão de **bases analíticas** relevantes para cada pergunta de negócio
- Foco em **democratização do acesso a dados com autonomia do usuário**

**Resultado:**
- **65% de aumento no número de usuários acessando as bases da área** (ano a ano)
- **86.000 usuários** consumindo bases productizadas

#### 3.4 — Scorecard do PIT (Padrão Itaú de Taguear)

Ferramenta de auto-avaliação da saúde do tagueamento de cada squad. Composto por 4 pilares:

| Pilar | O que avalia |
|---|---|
| **1. Versão do SDK** | Se o squad está usando a versão atual/correta do SDK |
| **2. Completude dos dados** | Se os campos obrigatórios estão sendo preenchidos |
| **3. Padronização / Guard Rails** | Se os dados respeitam o PIT (nomes, tipos, formatos) |
| **4. Conexão com Jornada** | Se o tagueamento está vinculado ao ID de jornada correto |

> **Princípio de Ownership:** O Scorecard transfere a responsabilidade pela qualidade dos dados para o próprio squad — governança escalável sem o modelo "um-a-um" (spoke).

#### 3.5 — Qualidade de Dados (Data Quality)

Monitoramento contínuo com base nos pilares do framework **DAMA**:

- **Unicidade**: garantia de que eventos não são duplicados
- **Integridade**: garantia de completude e consistência dos dados
- **Velocidade (Velocity)**: monitoramento da latência de chegada dos dados

Alertas automáticos são disparados quando há **queda de campos** (field drops) — detectando problemas de implementação antes que impactem análises.

---

### Pilar 4 — Arquitetura de Distribuição: Cross-Cloud, Near-Real-Time

#### Visão Geral

A arquitetura é **cross-cloud**: dados coletados no ecossistema Google (GA4) são distribuídos para AWS, onde vivem as camadas de consumo e análise.

```
Canais (SuperApp, Bankline, App Empresas, ION)
        ↓
   SDK Analytics (coleta padronizada, guard rails)
        ↓
   Data Maestro (roteamento)
        ↓
   GCP / Google Analytics 4
        ↓ (pipeline cross-cloud)
   AWS — Camadas de Dados
        ↓
   Consumidores (Squads, Times de Negócio, Datadiva, ML)
```

#### Camadas de Tabelas

| Camada | Nome | Descrição |
|---|---|---|
| **Raw** | SOR | Dados brutos, sem transformação |
| **Treated** | ST | Simplificada, tratada, pronta para consumo |
| **Enriched** | SPEC | Com regras de negócio aplicadas |

#### Tabela ST — O Coração do Consumo

A tabela **ST (SuperApp + Bankline)** é a referência de consumo mais ampla da plataforma:

- Atualização a cada **30 minutos** (lançada em março) — near-real-time
- **3ª tabela mais consultada do banco no nível de squads**
- Campos pré-tratados incluídos:
  - **Session ID** (identificador de sessão)
  - **Timestamp** padronizado
  - **ID interno cruzado do usuário** ("três") — vinculando dados digitais ao perfil do cliente

#### Decisões Arquiteturais

- Uso de **componentes de baixo custo** nas etapas intermediárias do pipeline
- **Redundância** nos pontos críticos de processamento
- Uso de **EMAR** para robustez e carregamento rápido com menor custo de processamento
- Resultado: **47% de redução no custo por unidade de evento processado na AWS**

#### Escala da Distribuição

- **30+ tabelas diferentes** servindo os canais do banco (SuperApp, App Empresas, ION)
- **70 bilhões de hits/mês** coletados com consistência e qualidade
- Pico histórico: **4,5 bilhões de eventos em um único dia** (5 de setembro)

---

## 4. Resultados — Os Grandes Números

| Métrica | Resultado |
|---|---|
| **Redução no tempo de carregamento do SuperApp** | **84%** |
| **Redução no tamanho do SDK** | **50%** |
| **Redução no custo por evento processado na AWS** | **47%** |
| **Hits coletados por mês** | **70 bilhões** |
| **Aumento de usuários acessando as bases** | **65%** (YoY) |
| **Usuários consumindo bases productizadas** | **86.000** |
| **Ranking da tabela ST no banco (consultas por squad)** | **3ª mais consultada** |
| **Pico de eventos em um dia** | **4,5 bilhões** (5 de setembro) |
| **Tabelas servindo os canais do banco** | **30+** |
| **Pessoas no time de Digital Analytics** | **50+** |
| **Redução de tipos de eventos distintos** | De 6 milhões → **47 tipos** |

---

## 5. Casos de Uso Habilitados pela Plataforma

### Prevenção de Fraudes com ML
Uso das bases near-real-time (tabela ST com atualização de 30 minutos) para modelos de machine learning que detectam comportamentos anômalos e previnem fraudes em tempo quase real.

### Personalização de Ofertas Digitais (Vitrines e Itaú Shop)
Dados de comportamento digital (telas visitadas, produtos visualizados, jornadas completadas) alimentam motores de recomendação para personalizar vitrines de produtos e ofertas no Itaú Shop e no SuperApp.

### Mapeamento de Abandono de Jornada
Identificação de exatamente em qual tela, etapa ou interação clientes abandonam fluxos críticos (abertura de conta, contratação de produto, transferências), permitindo times de produto otimizarem os pontos de fricção.

### Monitoramento de Erros e Sucesso em Implementações
Squads conseguem validar em near-real-time se uma nova funcionalidade está sendo corretamente tagueada, se há erros de implementação e qual o impacto no funil de dados.

### Monitoramento de Versão do SDK
O Scorecard do PIT permite que times de engenharia monitorem a adoção da versão mais recente do SDK em produção, identificando squads com versões desatualizadas antes que se tornem problemas.

### Otimização de Campanhas (Redução de CAC)
Dados de comportamento digital permitem análise de atribuição mais precisa, otimizando investimento em mídia paga e reduzindo o Custo de Aquisição de Clientes (CAC).

### Análise de Performance de Vitrines
Análise do desempenho de produtos em carousel de ofertas no SuperApp — quais vitrines geram conversão, quais são ignoradas, em qual posição do carousel a CTR cai.

---

## 6. Lições Aprendidas

### Padronização como Fundação
> "Sem padronização, você não consegue medir. Sem medição, você não consegue melhorar."

A redução de 6 milhões para 47 tipos de eventos não foi apenas uma conquista técnica — foi a virada de chave que tornou todas as outras iniciativas possíveis.

### Ownership de Dados por Squads
O **Scorecard do PIT** foi a resposta ao problema de escala da governança. O modelo antigo de "governança por spoke" (um especialista para cada squad) não escalava. O Scorecard criou **responsabilidade distribuída**: cada squad monitora e responde pela qualidade dos próprios dados.

### Dados como Produto
Tratar os dados com o mesmo rigor de um ativo de software comercial: pesquisa com usuários, piloto com grupo de adoção, feedback estruturado, lançamento em massa. Essa abordagem de **productização** foi aplicada em todas as iniciativas da plataforma.

### Estratégia de Adoção em Estágios
1. **Pesquisa:** entender as dores reais dos consumidores de dados
2. **Grupo piloto:** lançar com early adopters e coletar feedback
3. **Ajuste:** iterar com base no feedback antes do lançamento amplo
4. **Lançamento em massa:** rollout com suporte estruturado
5. **Monitoramento de churn:** acompanhar usuários que deixam de usar as bases e entender o porquê

### Canais de Adoção
- **Grupos no Microsoft Teams** para suporte e comunidade de usuários das bases
- **Executive summaries** para liderança — traduzindo dados técnicos em linguagem de negócio

### Governança Não Escala com Modelo Um-a-Um
A abordagem de spokes (um especialista para cada squad) funcionou no começo, mas não escala. O Scorecard automatizou a governança e transferiu ownership sem criar dependência.

### Cultura de Experimentação
> Testar, medir, ajustar. O mesmo rigor científico aplicado ao produto deve ser aplicado à plataforma de dados que o sustenta.

---

## 7. Conexão com a Estratégia "Um Itaú"

A plataforma de Digital Analytics não existe isolada — ela é infraestrutura central da estratégia de banco unificado:

- **Inteligência Itaú**: os dados comportamentais digitais alimentam o Pix no WhatsApp, o assistente de investimentos com IA e o app Itaú Empresa
- **IARA (Plataforma de IA)**: consome dados de comportamento digital para personalização em escala
- **CEX (Customer Experience)**: a conexão do ToolKit Analytics com IDs de jornada do CEX garante que dados de analytics e dados de experiência falam a mesma língua
- **Prevenção de Fraudes**: integração com times de segurança via bases near-real-time

---

## 8. Glossário Técnico

| Termo | Definição |
|---|---|
| **SDK Analytics** | Software Development Kit de coleta de dados — único ponto de instrumentação para todos os canais do banco |
| **Data Maestro** | Orquestrador de roteamento — define para qual ferramenta/destino cada evento deve ser enviado |
| **PIT (Padrão Itaú de Taguear)** | Framework de padronização com 47 tipos de eventos, parâmetros obrigatórios/opcionais e variáveis de sessão/globais |
| **Texpack / Textpack** | Documento de especificação técnica de tagueamento — o "mapa de métricas" de cada jornada |
| **Datadiva** | Plataforma de IA multi-agente para self-service de dados de analytics, do tagueamento ao consumo |
| **ToolKit Analytics** | Interface de governança para squads — gerencia Textpacks, centraliza visão de dados, conecta com jornadas |
| **Scorecard PIT** | Ferramenta de auto-avaliação da saúde do tagueamento de cada squad (4 pilares) |
| **SOR** | Source of Record — camada de dados brutos sem transformação |
| **ST** | Tabela Simplificada/Tratada — pronta para consumo, com session ID, timestamp e ID cruzado do usuário |
| **SPEC** | Tabela com regras de negócio aplicadas — camada enriquecida |
| **Guard Rails** | Regras de bloqueio no SDK que impedem dados fora do padrão de serem coletados |
| **EMAR** | Componente arquitetural usado para robustez e carregamento rápido com menor custo |
| **CAC** | Custo de Aquisição de Clientes |
| **DAMA** | Framework de gestão de qualidade de dados (unicidade, integridade, velocidade) |
| **Hit** | Evento individual de interação coletado pelo SDK |
