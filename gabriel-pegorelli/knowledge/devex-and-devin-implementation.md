# Conhecimento Técnico: DevEx, o Produto DEVA e a Implementação do Devin no Itaú

## 1. O Case Global Itaú + Cognition AI (Devin)

Em meados de 2024 e consolidado em 2025/2026, o Itaú consolidou-se como **a instituição financeira com a maior implementação de agentes autônomos de engenharia de software do mundo**, liderada pela trilha **Tech Experience** e pela squad de **AI Coding Tools**:
- **Adoção**: **75% dos desenvolvedores** do Itaú utilizam o Devin (com expansão para os mais de 17.000 profissionais de tecnologia).
- **Velocidade de Migração**: Atualizações e migrações de tecnologias ocorrem de **5 a 6 vezes mais rápido**.
- **Segurança Proativa**: Redução de **70% do estoque de vulnerabilidades** de código através de varreduras e correções automatizadas.
- **Documentação de Escala**: Catalogação de mais de **300.000 repositórios** corporativos.
- **Cobertura de Testes**: **Dobro da cobertura de testes automatizados** em comparação com o período pré-agentes.
- **Modernização de Infraestrutura**: Migração dos últimos workloads legados para a nuvem da **AWS** com encerramento previsto para **2028**.

---

## 2. A Camada Proprietária: DEVA (Desenvolvedora Virtual Autônoma)

Governar mais de 300.000 repositórios (o equivalente a uma cidade como Franca/SP com 300 mil casas) exigiu a criação da **DEVA**, a plataforma interna de orquestração do Devin:
- **Ponto Único de Entrada**: Portal centralizado para autenticação e concessão de acessos.
- **Gestão de Workspaces por Squad e Comunidade**: Automação de permissões para mais de 3.000 squads, garantindo que cada time acesse apenas os repositórios autorizados.
- **Gestão de ACUs (Agentic Compute Units)**: Monitoramento e governança de consumo computacional do Devin para rateio orçamentário transparente (*FinOps*).
- **Limitação de Blast Radius**: Isolamento rigoroso para evitar que falhas ou alterações inadvertidas ultrapassem o escopo do time.
- **Ancoragem nos Itens de Trabalho (Backlog)**: O Devin atua diretamente integrado às ferramentas de gestão ágil (Jira/backlog), conectando cada linha de código gerada a um card ou necessidade real de negócio.

---

## 3. Os Dois Modos de Operação: Assíncrono vs. Síncrono (Devin CLI)

### A. O Agente Assíncrono na Nuvem
- **Como funciona**: O Devin opera em uma máquina virtual dedicada na nuvem com seu próprio ambiente, interpretador e terminal.
- **Caso de uso ideal**: Tarefas autocontidas, previsíveis e bem descritas (ex: migração de versão de framework, refatoração de dezenas de repositórios, escrita de documentação, varredura de vulnerabilidades).
- **Vantagem**: Escalabilidade massiva. O engenheiro pode despachar dezenas de tarefas em lote, fechar a máquina ou realizar outras atividades enquanto o agente processa.

### B. O Agente Síncrono (Devin CLI e Windsurf IDE)
- **Como funciona**: O agente opera conectado diretamente ao terminal local ou à IDE do desenvolvedor.
- **Caso de uso ideal**: Desenvolvimento de novas funcionalidades, exploração de arquitetura e casos de uso onde os requisitos ainda estão em definição.
- **Vantagem**: O desenvolvedor permanece no loop de tomada de decisões a cada linha ou bloco de código, ajustando o rumo da implementação em tempo real.

---

## 4. Estratégia de Expansão em Ondas e Programas de Cultura

A expansão para 17.000 profissionais foi estruturada em um plano de 3 meses (setembro a novembro), alcançando adoção orgânica espontânea:
- **Expansão em Ondas Semanais**: Rollout fatiado por comunidades, com a liderança local priorizando os projetos de maior retorno sobre investimento.
- **Comunicação Segmentada**: Abordagens distintas para executivos/líderes (foco em ROI e segurança) e para desenvolvedores (foco em produtividade e boas práticas), apoiados pelo time de *Change Management*.
- **Onboarding Estruturado**: Welcome kits, cursos, documentação viva e canal de suporte direto.
- **Deva Advocates (Devin Advocates)**: Rede de engenheiros *early adopters* voluntários nos times para tirar dúvidas, disseminar boas práticas e conectar as squads diretamente à Cognition Labs para ciclos rápidos de PDCA.
- **Deva Owners**: Pontos focais focados em governança orçamentária, evitando outliers e desperdícios no consumo de ACUs.

---

## 5. Cases Reais de Engenharia no Itaú

1. **CNPJ Alfanumérico**:
   - Adaptação regulatória nacional que demandou alterar mais de **139.000 componentes**, entregue com precisão pelo Devin.
2. **Modernização de BFFs (.NET para Java)**:
   - Projeto estimado originalmente em **4 meses (4.000 horas de engenharia)**.
   - Entregue em apenas **1 mês (700 horas)**, representando um ganho de eficiência superior a 75%.
3. **Resolução de Vulnerabilidades no Veracode**:
   - Automação que lê apontamentos de segurança do Veracode, gera a correção no código e submete o Pull Request já pronto para auditoria humana.
4. **Modernização Mainframe / COBOL**:
   - Integração automatizada que extrai código do Changeman, cria um repositório temporário no GitHub, executa adequações com o Devin e devolve o código compilado via API para a plataforma Mainframe.
5. **Documentação Viva e Devin Wiki**:
   - Descontinuação do Confluence e adoção de **GitHub Pages** e **Devin Wiki**, permitindo consultas conversacionais à arquitetura e geração dinâmica de diagramas.

---

## 6. Vibe Coding vs. Vibe Engineering e as 4 Macroatividades

- **Vibe Coding**: Programação baseada puramente em prompts de alto nível, adequada para protótipos ou sistemas sem criticidade.
- **Vibe Engineering**: A disciplina do Itaú, onde o desenvolvedor alia a automação agêntica ao rigor da engenharia:
  1. **Especificação (Spec-Driven Development - SDD)**: Decomposição de problemas complexos em enunciados lógicos e requisitos claros;
  2. **Orquestração**: Atuação como maestro entre humanos, copilotos e agentes autônomos;
  3. **Verificação Crítica**: *Human-in-the-Loop* inegociável — nenhum código entra em produção sem PR revisado por humano e bateria de testes automatizados ("partida dobrada");
  4. **Governança & FinOps**: Gestão atenta de custos computacionais (ACUs) e prevenção a débitos técnicos.
