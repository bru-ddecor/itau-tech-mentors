# Transcrição e Síntese Oficial: Itaú Tech Meetup — Agentes de IA em Escala e DevEx

**Evento**: Itaú Tech Meetup (Edição Híbrida — CEIC Itaú)  
**Temas**: Escalando a Transformação com Agentes, O Case do Devin (Cognition) na Engenharia do Itaú, DevEx, e Arquitetura da Inteligência Itaú  
**Participantes**:
- **Raíça**: Host / Comunicação e Change (Tech, Ops e IGA)
- **Fernando Contop**: Diretor de Tecnologia no Itaú (Palestra Magna: *Agentes de IA no Itaú: Escalando a Transformação*)
- **Gabriel Pegorelli**: Gerente de Tecnologia e Líder de Developer Experience (DevEx) no Itaú
- **Guilherme ("Gui")**: Growth & Global Strategy na Cognition AI (criadora do Devin)
- **Calex Curts ("Calx")**: VP de Tecnologia no EBANX (partner Itaú/Cognition)
- **Thaís Souza**: Cientista de Dados no ICTI (mediadora do Painel de Engenharia)
- **Aline Pavan**: Superintendente de Tecnologia e Líder de Comunidade da *Inteligência Itaú*
- **Bruno Santos**: Diretor de Tecnologia e IA da Localiza
- **Isabela Prates**: Executiva de Contas no Google Cloud (Itaú Partnership)
- **Eduardo Ruska ("Edu")**: Superintendente / Head de Data Science no Itaú (mediador)

---

## 1. Números e Métricas Oficiais da Transformação de IA no Itaú (Fernando Contop)

### Escala Interna e Engenharia
- **13.000+ YouTubers** utilizam ferramentas e plataformas de IA no seu cotidiano corporativo.
- **75% dos engenheiros de software** do banco utilizam o **Devin** (Cognition AI), com destaque para o **Devin CLI**.
- **Migrações de código**: Realizadas entre **5 a 6 vezes mais rápido** com coding agents.
- **Segurança de Código**: Redução de **70% no estoque total de vulnerabilidades** mapeadas em codebases.
- **Repositórios Mapeados**: Mais de **300.000 repositórios** no banco catalogados e documentados com IA.
- **Qualidade de Testes**: **Dobro da cobertura de testes automatizados** em codebases legadas e novas.

### Métricas de Negócio e Impacto em Produção
- **Qualidade**: Redução de **98% em incidentes de alto impacto** para os clientes finais.
- **Velocidade**: Aumento de **quase 3.000% na entrega de valor ativado** (código em produção gerando impacto real para o cliente, não apenas commits).
- **Eficiência Financeira**: Redução de **44% no custo unitário de processamento de transações**.

---

## 2. A Marca "Inteligência Itaú" e Grandes Casos em Produção

O banco consolidou suas soluções de IA Generativa voltadas para o cliente sob o branding **Inteligência Itaú** (identificado pelo ícone das estrelinhas no aplicativo):

1. **Pix no WhatsApp**:
   - Permite realizar transações Pix diretamente pelo WhatsApp por texto, áudio ou foto de QR Code.
   - Elimina a necessidade de abrir o app do banco na rua, em shows ou estacionamentos, garantindo rapidez e segurança física.
2. **Inteligência Itaú para Pequenas Empresas (PJ / EMPS)**:
   - Consultoria e assessoria financeira automatizada para gestão de fluxo de caixa e recebíveis de pequenos empresários.
3. **Inteligência Itaú para Investimentos (ELF)**:
   - Mais de **5 milhões de clientes ativos**.
   - Quebra a barreira da timidez e insegurança financeira, oferecendo consultoria sob medida com a ampla prateleira de investimentos do Itaú e de parceiros.

---

## 3. DevEx, Coding Agents e o Devin na Prática (Gabriel Pegorelli & Cognition)

### A Parceria Itaú + Cognition AI
- O Itaú foi um dos primeiros *early adopters* globais a buscar a Cognition (março/2024), trabalhando em conjunto para adaptar o Devin à complexidade de uma empresa *enterprise* altamente regulada.
- **Desafios de Infraestrutura e Governança**:
  - Criação de **Service Accounts** com zonas de dano (*blast radius*) estritamente limitadas.
  - Segurança de dados: isolamento rígido entre o que repousa na infraestrutura do banco e o que trafega na nuvem da Cognition.
  - Regra de ouro da esteira: nenhum commit sobe para produção sem **validação humana no loop (*Human in the Loop*)** e autorização explícita do desenvolvedor.

### Do Agente Assíncrono ao Devin CLI
- **Devin na Nuvem (Assíncrono)**: Excelente para tarefas autocontidas e previsíveis (refatoração em massa, migração de frameworks, documentação). O dev dispara dezenas de sessões, fecha o laptop e o trabalho é executado.
- **Devin CLI & IDE (Síncrono / Windsurf)**: Ideal para explorações onde o desenvolvedor precisa tomar microdecisões contínuas durante o ciclo de escrita de código.

### Teste A/B com 100 Squads e Métricas DORA
- O Itaú validou a eficácia do Devin por meio de um teste A/B formal com **100 squads pareadas** por nível de senioridade, tamanho e modernização tecnológica.
- Acompanhamento rigoroso de métricas DORA: *Lead Time*, *Cycle Time*, *Change Failure Rate* e vazão de entregas.

### "Partida Dobrada" no Software & Novo Papel do Engenheiro
- **Calex Curts (EBANX)**: Assim como na contabilidade clássica existe a partida dobrada, no software a ética e a segurança residem em **boas suítes de testes automatizados**. O teste é a salvaguarda que permite ao agente explorar o novo sem quebrar o entorno.
- **Ressignificação do Desenvolvedor**: A engenharia deixa de ser o "decoreba de primitivas e sintaxes" (como na era do Delphi 5) para se tornar **capacidade de intenção arquitetural, pensamento crítico, curiosidade e resiliência**.
- **Acesso ao Conhecimento Cristalizado**: Áreas não-técnicas (ex: comercial) usando agentes para consultar regras de negócio escondidas em repositórios de código via linguagem natural.

---

## 4. Arquitetura de Experiências Inteligentes (Aline Pavan, Localiza & Google)

### Inversão do Paradoxo Conversacional
- **Aline Pavan**: Historicamente, chatbots eram o "canal de escape" para onde o cliente ia frustrado após falhar na navegação tradicional.
- A IA generativa inverteu essa lógica: o conversacional agora é a **porta de entrada primária e proativa**, antecipando necessidades e exterminando o *"banquês"* (jargões incompreensíveis como "CET do empréstimo").

### A IA Escancara os Problemas Legados
- Quando o modelo probabilístico entra em ação, ele amplifica drasticamente deficiências prévias: falta de documentação de processos, ausência de testes unitários, acoplamento de APIs e regras de trabalho frouxas.
- **Critério 80/20 de Priorização**: Não se deve tentar consertar todo o legado antes de usar IA. O segredo é escolher "poucos e excelentes casos de uso focados em valor para o cliente" que sirvam como catalisadores para arrumar a casa (*efeito polinizador*).

### Rigor e Confiança Absoluta em Transações Críticas
- Enquanto seres humanos são perdoados por pequenos lapsos cotidianos, a tolerância dos clientes com erros de IA é zero.
- Fluxos determinísticos (como debitar e creditar um Pix) exigem ancoragem estrita, baterias exaustivas de *Evals* e conformidade contratual estrita com fornecedores de LLMs.
- **Google Cloud & DeepMind (Isabela Prates)**: O Gemini foi arquitetado nativamente como modelo multimodal desde o dia zero. Os dados de clientes corporativos residem exclusivamente dentro de seus respectivos *tenants* privados e jamais são utilizados para treinar modelos fundacionais públicos.
