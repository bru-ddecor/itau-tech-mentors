# Transcrição e Síntese Oficial: Itaú Tech Meetup — IA Generativa e Agentes em Produção

**Evento**: Itaú Tech Meetup  
**Tema**: Do Contexto à Experiência: A Nova Era da IA Generativa e Agentes (Iaí, Iara, Carreira e Governança)  
**Participantes**:
- **Raíça**: Host / Comunicação e Change (Tecnologia, Operações e IGA)
- **Ricardo Coelho ("Ricardinho")**: Superintendente de Tecnologia e Arquitetura de IA no Itaú
- **Aline Pavan**: Superintendente de Tecnologia do Itaú (Co-liderança do **Iaí**)
- **Mariana ("Mari")**: Liderança de RH/Pessoas para Tech, Dados, CEX e Operações no Itaú
- **Finer Felício ("Fer")**: Superintendente de Produtos Digitais e Estratégia de GenAI no Itaú
- **Bárbara Correa**: Gerente de Responsible AI & Data Privacy no Itaú
- **Ricardo de Almeida**: AI Specialist no Google Cloud
- **Bel Miranda**: Diretora Executiva de Tecnologia no Grupo Boticário (Case Sinfonia e Concierge)
- **Luiz Pacete**: Mediador (Jornalista Exame e LinkedIn Top Voice)
- **André Lopes**: AI Solutions Engineer na OpenAI (1º engenheiro de soluções da OpenAI no Brasil)

---

## 1. Bloco Arquitetura & Plataforma de IA — Ricardo Coelho ("Ricardinho")

### O Conceito de Agente no Itaú
- **Definição**: Entidade de software não biológica capaz de compreender contexto, planejar, replanejar e tomar ações com autonomia controlada, mantendo o humano no loop (*Human-in-the-Loop*).
- **Consumo de Modelos**: Uso de modelos de fronteira dos parceiros combinado com a necessidade crucial de modelos especializados para o negócio bancário (garantindo precisão semântica e eficiência de custo por token).
- **Padronização de Protocolos**: Interfaces e contratos rígidos para que os agentes se comuniquem com sistemas internos com segurança, governança e respeito a dados sensíveis de clientes.

### A Fundação Prévia: Data Mesh
- A IA agêntica só funciona no Itaú porque o banco decidiu, anos atrás, implementar uma arquitetura de **Data Mesh**: dados por domínio, *self-service*, com *ownership*, metadados, qualidade aferida e definição clara de *Golden Sources* (fontes únicas da verdade).
- **Problema Crítico de Contexto**: O cérebro humano consegue ler palavras com letras embaralhadas e deduzir o significado. A IA não. Se o dado estiver errado ou sem relações explícitas, o agente toma decisões erradas com extrema convicção.

### Ontologias, Taxonomias e Grafos de Conhecimento
- O banco investe pesadamente na criação de glossários de termos, taxonomias, ontologias e *Knowledge Graphs*.
- **O Caso do "Lance"**: Nos testes de um agente sobre futebol, ele sugeriu um consórcio porque associou a palavra "lance" (lance de futebol x lance de consórcio). Isso provou que ontologias e relações semânticas formais são indispensáveis para eliminar alucinações de contexto.

### Plataforma IARA
- **O que é**: O ecossistema corporativo de capacidades e plataforma de agentes do Itaú.
- **Função**: Disponibiliza modelos de mercado e treinados internamente, gerencia conexões com bases de conhecimento (*Knowledge Bases*), ontologias e grafos.
- **Resultados**: Crescimento de *double digits* em iniciativas, transição bem-sucedida de PoCs/pilotos para produção real e redução contínua e drástica do custo por token.

---

## 2. Bloco Produto & Experiência do Cliente — Aline Pavan & Finer Felício

### O Produto Iaí
- Assistente financeiro e copiloto de IA nativo no aplicativo do Itaú.
- 79% de avaliação positiva já no primeiro acesso (onboarding).
- Deixa para trás a segmentação por faixas/clusters tradicionais para tratar cada cliente como indivíduo com histórico e preferências de vida (pets, filhos, hobbies, estilo de consumo).
- **Transição Estratégica**: O banco deixa de ser estritamente transacional para se tornar **consultivo e de relacionamento**, com experiências conversacionais híbridas (telas visuais ricas + conversa fluida).

### Multimodalidade e Execução Real
- Interações por texto, voz, imagens e documentos.
- Capacidade de execução fim a fim: **Pix por voz** no aplicativo e nas maquininhas ("laranjinha").
- Foco em resolver a intenção do cliente sem obrigá-lo a navegar em menus complexos ou entender jargões de finanças (tabela regressiva, isenção de IR, etc.).

### Pesquisa e Proximidade com o Cliente (CEIC)
- A equipe de design/research do banco convida clientes reais para tomar café e comer sanduíche no CEIC para ouvir suas dores reais antes de programar qualquer agente.
- O hype tecnológico é combatido mantendo o cliente e o valor real de negócio no centro de cada decisão.

---

## 3. Bloco Governança, Risco & Responsible AI — Bárbara Correa

### Governança como Capacidade de Plataforma
- Não é viável nem escalável ter governança centralizada com comitês manuais e avaliações lentas.
- A governança foi ferramentalizada e integrada à plataforma de IA como capacidade contínua e cíclica.

### AI Red Teaming & Guardrails
- Realização de hackathons internos de *Red Teaming* para forçar a tecnologia a falhar, mapear vulnerabilidades de *prompt injection*, vieses e comportamentos inadequados.
- Criação de guardrails de negócio e de tom de voz.

### Eficácia como Pilar de Segurança
- Segurança em excesso gera a *"IA mais responsável do mundo que não responde nada"*.
- A eficácia é mensurada continuamente: se o agente perde utilidade por travas excessivas, o balanço entre risco e retorno foi perdido.

### Gestão de Memória e LGPD
- O cliente possui agência e soberania sobre seus dados: pode decidir o que a IA deve lembrar, esquecer ou apagar das conversas.
- Isolamento rígido de ambientes (*Chinese walls*) e permissões de acesso baseadas em contexto.

---

## 4. Bloco Carreira, Cultura e Pessoas — Mariana ("Mari" - RH Tech)

### A Responsabilidade Permanece Humana
- A execução de código ou tarefas pode ser delegada ao agente, mas **o mandato e a responsabilidade final continuam sendo 100% da pessoa (do colaborador / YouTuber)**.
- O pensamento crítico e o entendimento de impacto continuam insubstituíveis.

### Fundamentos Técnicos são Indispensáveis
- Se o profissional não domina os fundamentos de arquitetura e computação, não terá capacidade de criticar, avaliar e guiar o código gerado pela IA.

### Valores Culturais na Era da IA
1. **A gente trabalha para o cliente**: IA só faz sentido se resolver um problema concreto do cliente; nunca IA pela IA.
2. **A gente não sabe tudo**: Humildade para aprender, buscar benchmarks externos e construir pontes com o ecossistema.
3. **Ética é inegociável**: Responsabilidade no uso de dados, prevenção a alucinações e transparência.

### Academia de IA & ICTI
- **Academia de IA**: Mais de 14.000 profissionais já capacitados em múltiplos níveis; mais de 56.000 colaboradores usando ferramentas de IA no dia a dia.
- **ICTI (Instituto de Ciência e Tecnologia Itaú)**: Braço de P&D de ponta com mais de 50 projetos, 39 patentes, 20+ publicações científicas, mais de 200 pesquisadores e parcerias globais com **MIT** e **Stanford**.

---

## 5. Bloco Lições Técnicas de Agentes — André Lopes (OpenAI)

### Anatomia do Harness de Agentes
- Modelo Cognitivo (LLM de fronteira / raciocínio)
- Memória de Curto e Longo Prazo (com invalidação temporal e escrita cirúrgica)
- Ferramentas & Ações (APIs, Webhooks, MCPs, Knowledge Bases)
- Canais Multimodais (Texto, Voz, Visão, Omnichannel com preservação de estado)
- Motor de Raciocínio (*Reasoning Loop*)

### Avaliações (Evals) Offline e Online
- **Evals Offline**: Baterias de teste automatizadas com agente gerador de personas e agente juiz (*LLM-as-a-Judge*), sempre calibrados por humanos especialistas para balancear concisão e educação.
- **Evals Online**: Monitoramento em tempo real de logs de produção.
- **Atenção aos Falsos Positivos**: Exemplo real de clientes de classes C/D cuja linguagem coloquial para saber o status do empréstimo disparava falso alerta de fraude. O mundo real exige entender a linguagem genuína do cliente.
