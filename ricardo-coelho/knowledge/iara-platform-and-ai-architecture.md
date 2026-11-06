# Conhecimento Técnico: Plataforma IARA e Arquitetura de IA no Itaú

## 1. Visão Geral da Plataforma IARA

A **IARA** é a plataforma corporativa de agentes de Inteligência Artificial do Itaú Unibanco. Desenvolvida para resolver o gargalo da fragmentação e do custo, ela atua como a espinha dorsal de IA no banco:

- **Plataformização de Capacidades**: Em vez de cada squad criar seu próprio ecossistema de LLMs do zero, a IARA centraliza e disponibiliza modelos de fronteira (OpenAI, Google Gemini via Google Cloud, Anthropic) e modelos especializados treinados pelo próprio banco.
- **Velocidade de Disponibilização**: Quando um novo modelo de fundação é lançado no mercado global, em **até 2 dias** ele está integrado e disponível de forma segura dentro da IARA para qualquer squad ou YouTuber utilizar.
- **Transição de PoC para Produção**: Supera o "vale da morte" dos projetos de IA, garantindo que iniciativas alcancem escala real com crescimento contínuo de duplo dígito (*double digits*).
- **Eficiência Financeira (Custo por Token)**: Monitora, roteia e otimiza o consumo de tokens em tempo de execução, reduzindo continuamente o custo unitário por chamada.
- **Isolamento de Tenants e Privacidade**: Os dados dos clientes do banco residem exclusivamente dentro do tenant privado da instituição e jamais são compartilhados ou utilizados para re-treinamento de modelos públicos.

---

## 2. A Fundação em Data Mesh e Domínios

O sucesso da IA generativa no Itaú decorre de uma decisão estrutural tomada anos antes:
- **Arquitetura Descentralizada por Domínio**: Os dados não residem em um silo monolítico inalcançável; pertencem aos seus domínios de negócio com responsabilidade clara (*ownership*).
- **Consumo Self-Service**: As squads consomem dados através de produtos de dados (*Data Products*) governados.
- **Golden Sources (Fontes da Verdade)**: Definição inequívoca de qual base é a fonte autêntica de cada entidade (ex: saldo, cadastro, investimentos), prevenindo inconsistências entre sistemas e agentes.
- **Consumidores Não Biológicos**: A esteira de dados foi readaptada para ser consumida não apenas por humanos em dashboards BI, mas por agentes inteligentes autônomos.

---

## 3. Contexto, Ontologias e Grafos de Conhecimento

### A Falácia do Cérebro Humano vs. Modelo de Linguagem
Seres humanos possuem heurística biológica acumulada: conseguem ler textos com letras trocadas e preencher lacunas de ambiguidade. Agentes de IA, se alimentados com dados ambíguos, formulam alucinações assertivas.

### A Lição do Case "Lance"
Em testes internos de guardrails e contexto conversacional:
- Um usuário conversava sobre futebol com um assistente.
- O agente disparou uma resposta recomendando um **consórcio**.
- Causa-raiz: O agente fez a correlação semântica ingênua com a palavra *"lance"* (lance de futebol vs. lance de consórcio).
- Solução: Implementação de **ontologias formais, taxonomias e grafos de conhecimento (*Knowledge Graphs*)** que explicitam os relacionamentos entre termos, produtos e intenções de negócio, garantindo desambiguação precisa.

---

## 4. Anatomia do Harness e Arquitetura Agêntica

A arquitetura de agentes no Itaú adota o conceito de **Harness**, conectando:
1. **Agente Global**: O orquestrador de entrada da interação, responsável por capturar a intenção primária e rotear a conversa.
2. **Agentes Especialistas de Domínio**: Agentes dedicados com ferramentas e bases especializadas (ex: cartões, investimentos, crédito, Pix).
3. **Gerenciamento de Memória**: Mecanismo de persistência contextual de curto e longo prazo com controle explícito pelo cliente (LGPD).
4. **Tool Use & Protocolos**: Conexão com sistemas transacionais via contratos de API padronizados e barramentos seguros.
5. **Guardrails Cíclicos**: Camada de proteção em tempo de execução integrada à IARA para mitigar riscos antes de a resposta chegar ao cliente.
6. **Integração com Knowledge Bases (CABs)**: Acesso padronizado a repositórios de documentação e conhecimento curado da empresa.
