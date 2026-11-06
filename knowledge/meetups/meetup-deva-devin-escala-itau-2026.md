# Transcrição e Síntese Oficial: Itaú Tech Meetup — Implementando o Devin em Escala no Itaú (2026)

**Evento**: Itaú Tech Meetup (1ª Edição de 2026)  
**Tema**: A Implementação do Devin no Itaú: Escalando Agentes Autônomos para mais de 17.000 Profissionais de Tecnologia e o Surgimento da DEVA  
**Palestrantes**:
- **Vitória**: Host / Comunicação e Tecnologia no Itaú
- **Gabriel Pegorelli**: Líder da Trilha Tech Experience no Itaú
- **Evelyn Cristina**: Coordenadora de Produtos e Dados (Squad de *AI Coding Tools*)
- **Giovana Jess ("Gi")**: Product Manager (Squad de *AI Coding Tools*)

---

## 1. A Evolução da Engenharia de Software até os Agentes Autônomos

Gabriel Pegorelli contextualizou a jornada histórica de 70 anos de software:
- **Anos 50/60**: Mainframes, linguagens de alto nível (COBOL, Fortran).
- **Anos 70/80/90**: Computação pessoal, orientação a objetos e interfaces visuais.
- **Anos 90/2000**: Arquitetura cliente-servidor, web e frameworks formais (RUP).
- **2001**: Manifesto Ágil e a necessidade de responder rapidamente a mudanças.
- **2004/2005**: Git e versionamento distribuído.
- **2006 em diante**: Cloud Computing (AWS), microsserviços, contêineres e DevOps na década de 2010.
- **2022**: Advento do ChatGPT e da IA Generativa pública.
- **2023 (Assistência)**: Chegada do GitHub Copilot no Itaú (autocomplete e assistência rápida).
- **2024 (Copilotos Internos)**: StackSpot AI (parceria com a Zup) integrado à jornada do desenvolvedor.
- **2025/2026 (Execução Autônoma)**: Adoção do **Devin** (Cognition AI), consolidando o Itaú como **o banco com a maior implementação de agentes autônomos de engenharia de software do setor financeiro**.

---

## 2. Paradigmas Emergentes: Software 2.0, Vibe Coding e Vibe Engineering

- **Software 2.0 (Andrej Karpathy)**: Menos foco em escrever sintaxe linha a linha; mais foco em especificar intenções, validar comportamentos e governar dados e modelos.
- **Vibe Coding vs. Vibe Engineering**:
  - *Vibe Coding*: Programar puramente por prompts em alto nível de abstração. Funciona para protótipos e sistemas simples, mas é arriscado para sistemas bancários críticos.
  - *Vibe Engineering*: A abordagem adotada no Itaú. O desenvolvedor alia a abstração da IA ao rigor da engenharia: constrói pipelines, especifica contratos (SDD - *Spec-Driven Development*), faz intervenções síncronas na CLI/IDE e orquestra o agente sem acumular débitos técnicos ou criar dependências cegas.

---

## 3. O Produto DEVA (Desenvolvedora Virtual Autônoma)

O Itaú possui mais de **300.000 repositórios** (o equivalente à quantidade de casas em uma cidade inteira como Franca/SP). Para governar esse ecossistema, o banco criou uma camada proprietária chamada **DEVA**:

- **Ponto Único de Entrada**: Portal centralizado para autenticação e governança de todos os engenheiros.
- **Gestão de Espaços (Workspaces)**: Automação de permissões para mais de 3.000 squads dentro de suas respectivas comunidades no Devin.
- **Gestão de ACUs (Agentic Compute Units)**: Monitoramento em tempo real do consumo computacional do Devin para evitar desperdícios e orquestrar rateios de custo (*FinOps*).
- **Limitação de Blast Radius**: Isolamento rigoroso de permissões para evitar alterações não autorizadas.
- **Rastreabilidade e Integração Ágil**: O Devin está formalmente ancorado aos itens de trabalho e backlog das squads (Jira/ferramentas ágeis internas), garantindo que cada linha gerada tenha vínculo com uma necessidade de negócio ou enabler técnico.

---

## 4. Metodologia de Expansão em Ondas (Rollout de 3 Meses)

A expansão para 17.000 profissionais foi estruturada em ondas semanais:
1. **Comunicação Segmentada**: Mensagens específicas para lideranças locais e mensagens práticas para os desenvolvedores.
2. **Onboarding com Welcome Kit**: Links úteis, documentação técnica, cursos e canal de suporte dedicado.
3. **Ciclos Rápidos de PDCA**: Coleta contínua de feedbacks para calibrar regras e ajustar a governança da DEVA semana a semana.
4. **Resultados de Adoção**: Quase 5.000 usuários ativos e centenas de PRs integrados ao final do terceiro mês (novembro), evoluindo para **adoção orgânica espontânea** a partir de dezembro/janeiro de 2026.

---

## 5. Programas de Cultura e Multiplicação

- **Deva Advocates (Devin Advocates)**: Comunidade de engenheiros *early adopters* que atuam como embaixadores voluntários nos times, disseminando boas práticas de prompting e conectando squads diretamente à Cognition AI para rápida evolução da ferramenta.
- **Deva Owners**: Pontos focais voltados para a governança orçamentária e sustentabilidade do uso das ACUs, evitando outliers de custo.

---

## 6. Cases Reais de Engenharia com o Devin no Itaú

1. **CNPJ Alfanumérico**:
   - Adaptação regulatória crítica que exigiu alterar mais de **139.000 componentes** de software, concluída com sucesso com o Devin.
2. **Modernização de BFFs (.NET para Java)**:
   - Projeto originalmente estimado em **4 meses (4.000 horas de trabalho)**.
   - Concluído em apenas **1 mês (700 horas)** com altíssima eficiência e baixo consumo de ACUs.
3. **Saneamento Automatizado no Veracode**:
   - Correção proativa de vulnerabilidades apontadas pelo Veracode com abertura automática de PRs para revisão humana.
4. **Modernização de Mainframe / COBOL**:
   - Automação que extrai códigos COBOL do Changeman, cria repositórios temporários no GitHub, aplica refatorações com o Devin e devolve o código via API para execução no Mainframe.
5. **Documentação e Devin Wiki**:
   - Descontinuação do Confluence e migração para **GitHub Pages** e geração de documentação conversacional interativa com **Devin Wiki** (geração de diagramas e consultas em linguagem natural à arquitetura).
6. **Meta de Modernização de Infraestrutura**:
   - Migração dos últimos workloads legados para a AWS com encerramento previsto para **2028**.

---

## 7. O Perfil do Novo Engenheiro de Software

Gabriel Pegorelli, Evelyn Cristina e Giovana Jess definiram as 4 macroatividades do engenheiro contemporâneo:
1. **Especificação (Spec-Driven Development - SDD)**: Decompor problemas complexos em enunciados claros, lógicos e testáveis.
2. **Orquestração**: Atuar como maestro conectando copilotos, agentes assíncronos e pipelines de CI/CD.
3. **Verificação Crítica**:
   - Nenhum PR entra em produção sem revisão humana formal (*Human in the Loop*).
   - "Partida dobrada": testes automatizados exaustivos antes de aprovar qualquer mudança.
4. **Governança & FinOps**: Monitorar custos de tokens/ACUs e a saúde arquitetural de longo prazo para evitar débitos técnicos.

**Habilidades Essenciais de Entrada no Banco**:
- Raciocínio lógico estruturado;
- Comunicação clara e *storytelling* (capacidade de transcrever problemas mentais em especificações coesas);
- Senso crítico para não aceitar código da IA cegamente;
- Resiliência para insistir, refinar e aprender com o comportamento das ferramentas.
