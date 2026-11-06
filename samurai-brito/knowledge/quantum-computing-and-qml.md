# Conhecimento Técnico: Computação Quântica e Quantum Machine Learning no Itaú

## 1. Visão Geral e Posicionamento Estratégico

A área de Computação Quântica do Itaú Unibanco, integrada ao **ICTI (Instituto de Ciência e Tecnologia Itaú)**, atua na vanguarda da pesquisa aplicada com o objetivo de preparar a instituição financeira para a chegada dos computadores quânticos comerciais:

- **Adoção Antecipada ("Não ao Wait-and-See")**: O banco iniciou sua estratégia em 2019 e hoje lidera o ecossistema brasileiro de Quantum aplicado ao setor financeiro.
- **Produção vs. Preparação**: O Itaú não roda sistemas em produção comercial em hardware quântico real hoje, devido às limitações físicas da era NISQ (*Noisy Intermediate-Scale Quantum*). A atuação concentra-se em:
  1. Simulações exaustivas de algoritmos quânticos;
  2. Execuções experimentais em processadores quânticos na nuvem via **IBM Quantum Network**;
  3. Desenvolvimento de algoritmos inspirados em quântica (*quantum-inspired*) que já rodam no ambiente clássico atual gerando ganhos mensuráveis.

---

## 2. O Tripé da Física Quântica Aplicada

A computação quântica baseia-se em três princípios fundamentais da mecânica quântica:

1. **Superposição**:
   - Enquanto o bit clássico é estático como uma moeda parada (0 ou 1), o qubit é análogo a uma moeda girando, com uma distribuição probabilística contínua entre 0 e 1.
   - Enquanto 4 bits clássicos armazenam 1 estado por vez, 4 qubits em superposição processam **16 configurações simultaneamente**.
   - Com apenas **300 qubits em superposição**, o número de estados representáveis supera o **total de átomos no universo observável**.
2. **Emaranhamento (*Entanglement*)**:
   - Correlação não-local exclusiva do universo quântico, onde o estado de um qubit dita instantaneamente o estado de outro, permitindo que circuitos parametrizados processem interações de altíssima complexidade.
3. **Interferência Quântica**:
   - Manipulação das fases das amplitudes de probabilidade para amplificar os caminhos que levam à resposta correta e cancelar por interferência destrutiva as respostas erradas.

---

## 3. Os Três Pilares de Quantum no Setor Financeiro

- **Simulação de Monte Carlo Quântica**: Aplicação em precificação de derivativos complexos, análise de risco de mercado e gestão de liquidez com aceleração quadrática de processamento em relação aos métodos clássicos.
- **Otimização Combinatória**: Resolução de problemas de alta dimensionalidade em balanceamento de carteiras (*portfolio optimization*) e alocação eficiente de capital regulatório.
- **Quantum Machine Learning (QML)**: Utilização de espaços de Hilbert de alta dimensionalidade para melhorar a separabilidade de dados complexos em problemas preditivos.

---

## 4. Casos Reais com Publicações Científicas Internacionais do Itaú

O time do ICTI/Itaú publicou artigos em periódicos internacionais comprovando vantagens teóricas e práticas:

### A. Previsão de Evasão de Clientes (Churn Predição)
- **Desafio**: Prever quais clientes possuem propensão a evadir ou sacar recursos nos 3 meses subsequentes.
- **Resultado de Negócio**: O modelo inspirado em quântica superou o melhor benchmark clássico de Machine Learning da área em **+2% de assertividade**.
- **Redução Computacional Provada**: Redução de **1.000.000 de operações clássicas para apenas 100 operações quânticas** durante o treinamento do modelo.

### B. Propensão a Crédito para Pequenas e Médias Empresas (PJ / PMEs)
- **Desafio**: Avaliação de risco e concessão de crédito para micro e pequenas empresas.
- **Resultado de Negócio**: Uso de Redes Neurais Quânticas (QNN) simuladas elevou o *Gini Score* de **53,7% (melhor modelo clássico existente) para 54,1%**.

---

## 5. Arquitetura de um Classificador Quântico Variacional (VQC)

O **VQC (Variational Quantum Classifier)** é um algoritmo quântico híbrido amplamente explorado no ICTI:

1. **Data Encoding (Feature Map)**: O vetor de dados clássicos $x$ é mapeado em um estado quântico $|\phi(x)\rangle$ através de portas de rotação quântica ($R_x, R_y, R_z$).
2. **Ansatz (Circuito Parametrizado)**: O análogo à arquitetura da rede neural. Possui parâmetros treináveis $\theta$ e portas de entrelaçamento (CNOT, CZ) que capturam relações não-lineares complexas.
3. **Medição Quântica**: O colapso da função de onda gera uma distribuição de probabilidades associada às classes (ex: label 0 e label 1 mapeadas no valor esperado $\langle Z \rangle \in [-1, 1]$).
4. **Otimizador Clássico no Loop**: Um algoritmo clássico (gradiente descendente, COBYLA, Adam) avalia a função de perda (*loss function*) e recalibra os parâmetros $\theta$ do Ansatz.
- **Nota Teórica Crucial**: Na computação quântica **ainda não existe análogo direto ao algoritmo de Backpropagation**, o que torna a otimização de circuitos quânticos uma área de intensa pesquisa acadêmica aberta.

---

## 6. O Kit Essencial para Começar em Quantum

Para atuar com computação quântica aplicada e QML, o candidato não precisa de formação em física teórica:
- **Álgebra Linear**: Espaços vetoriais, produtos internos, autovalores/autovetores e matrizes complexas.
- **Python e SDKs Quânticos**: Domínio de **Qiskit** (IBM Quantum), **PennyLane** (Xanadu) e **Cirq** (Google).
- **Acesso Gratuito**: Plataforma IBM Quantum (disponibiliza 10 minutos de computação em hardware real gratuito por mês) e o *Circuit Composer* visual.
