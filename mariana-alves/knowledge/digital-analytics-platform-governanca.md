# Conhecimento Profundo: Plataforma de Digital Analytics, Tagueamento e Governança no Itaú Unibanco

Este documento consolida a arquitetura, governança, produtos internos, lições e métricas de impacto da plataforma de Digital Analytics desenvolvida no Itaú Unibanco, liderada tecnicamente por **Mariana Alves** e **Isabela Rangel**.

---

## 1. O Problema Histórico e a Oportunidade da Migração GA4

### 1.1 O Cenário Caótico Anterior
- **SuperApp:** Mais de 6 milhões de nomes de eventos distintos distribuídos em 23.000 telas únicas.
- **Despadronização Extrema:** Emojis tagueados, grafias divergentes para um mesmo botão (ex: "continuar", "BtnContinuar", "btn_next"), valores vazios e erros de exceção persistidos como dados.
- **Sobrecarga Cognitiva:** Engenheiros precisavam conhecer e integrar SDKs de terceiros individualmente em cada squad.
- **Latência Crítica:** Processamento de terceiros (Google Universal Analytics) levava de 24h a 48h para disponibilizar dados brutos consolidados, impedindo reações ágeis de negócio.
- **Encerramento do Universal Analytics (Julho/2024):** A virada mandatória para o Google Analytics 4 (GA4) foi encarada não como uma migração técnica de "lift-and-shift", mas como a oportunidade de reconstruir toda a estratégia analítica com qualidade desde a origem (*quality by design*).

---

## 2. Pilares Arquiteturais da Solução

### 2.1 SDK Analytics (Coleta Padronizada)
- **Tag Única:** O desenvolvedor invoca apenas a API do SDK Analytics unificado.
- **Desacoplamento Tecnológico:** Ferramentas de terceiros tornam-se plugins configuráveis no backend, permitindo plugar ou desplugar soluções analíticas sem alterações no front-end mobile ou web.
- **Allowlist & Sanitização:** Bloqueio ativo de eventos fora da taxonomia na borda, impedindo tráfego de dados inválidos ou malformados.
- **Eficiência:** Redução de 50% do footprint/tamanho do SDK dentro das aplicações do banco.

### 2.2 Data Maestro (Orquestração e Governança de Roteamento)
- Roteador inteligente que decide quais eventos devem ir para quais destinos (CRM, ferramentas de mídia paga, Digital Analytics, ferramentas de experiência de usuário).
- Autonomia para as áreas de negócio decidirem a distribuição estratégica de seus dados, evitando custos excessivos de tráfego e licenças.

### 2.3 PIT (Padrão Itaú de Taguear) & Matriz de Taxonomia
- Redução de 6.000.000 para **47 tipos de eventos únicos** validados em tempo de execução.
- Tipagem rigorosa com 4 categorias de atributos:
  1. Parâmetros obrigatórios por tipo de evento;
  2. Parâmetros opcionais contextuais;
  3. Variáveis mínimas de sessão de usuário;
  4. Variáveis globais persistentes auto-coletadas pelo canal.
- Comitê de Taxonomia para avaliar e aprovar novos eventos de forma ágil.

### 2.4 Tool Kit Analytics & Texpacks
- **Tool Kit:** Interface unificada (front-end da governança) para especificação, controle e homologação de tagueamento.
- **Texpack (Mapa de Métricas):** Documento técnico que detalha quais eventos e parâmetros uma funcionalidade deve disparar.
- **Amarração com CEX:** Toda Texpack é indexada pelo ID oficial da jornada do cliente governada pelo time de CEX (Customer Experience), garantindo rastreabilidade do design de telas até o data warehouse.
- **Homologator:** Camada automatizada de validação antes de subidas em produção.

### 2.5 Datadiva (IA Multiagente em Autoatendimento)
- Ecossistema de múltiplos agentes de IA generativa para democratizar o suporte:
  - Ajuda desenvolvedores na redação de Texpacks e dúvidas de tagueamento.
  - Oferece dicas de queries SQL, boas práticas de consumo das tabelas analíticas e dicionário de dados interativo.

### 2.6 Arquitetura de Distribuição Multi-Cloud (GCP → AWS)
- **Ingestão Cross-Cloud:** Coleta inicial em GCP (ecossistema Google Analytics) com streaming/batch transfer para buckets na AWS.
- **Processamento Amazon EMR:** Transformação massiva e estruturação em camadas:
  - **Camada SOR (System of Record):** Tabela bruta completa com todos os eventos.
  - **Camada ST (Standard / Tratada):** Tabela refinada pronta para consumo rápido, enriquecida com Session ID, timestamps em milissegundos convertidos e o ID interno único do correntista (ID "três").
  - **Camada SPEC:** Tabelas especializadas com regras de negócios de domínios específicos.
- **Tempestividade a cada 30 minutos (D-Zero):** Atualização da tabela ST do SuperApp e Bankline a cada 30 minutos, viabilizando monitoramento quase em tempo real.

---

## 3. Grandes Números Oficiais do Case

- **84% de redução** no tempo de carregamento da plataforma no SuperApp.
- **50% de redução** no tamanho do SDK instalado nos apps.
- **47% de redução** no custo de processamento por evento na AWS.
- **70 bilhões de hits** de dados coletados mensalmente com governança ativa.
- **4,5 bilhões de eventos** processados em um único dia de pico (quinto dia útil — 5 de setembro).
- **65% de aumento** de usuários acessando as bases analíticas da área ano contra ano.
- **86.000 usuários** consumindo as bases produtizadas da área.
- **3ª tabela mais consultada do banco:** A tabela ST é a terceira mais acessada em nível de squads únicas em todo o Itaú.
- **30+ tabelas produtizadas** atendendo SuperApp, App Empresas, Íon e canais internos.
- **Time de 50+ especialistas** em Digital Analytics.

---

## 4. Casos de Uso e Valor Gerado para o Negócio

1. **Prevenção a Fraudes:** Modelos de Machine Learning consomem as tabelas ST atualizadas a cada 30 minutos para identificar padrões de comportamento atípico e mitigar transações fraudulentas.
2. **Otimização de Mídia e Redução de CAC:** Sinais comportamentais refinam a atribuição e investimento em canais de mídia paga, reduzindo o Custo de Aquisição de Clientes.
3. **Personalização e Vitrines Digitais:** Monitoramento de taxas de clique (CTR), abandono e conversão nas vitrines (carrosséis) do SuperApp e produtos do Itaú Shop, viabilizando ajustes imediatos de copy e oferta.
4. **Mapeamento de Abandono de Jornadas:** Identificação precisa do passo onde o cliente encontra atrito ou erro técnico após o deploy de novas features.
