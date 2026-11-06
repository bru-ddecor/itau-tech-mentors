# Transcrição e Síntese Oficial: Itaú Tech & Data Hackers — Computação Quântica e Quantum Machine Learning no Itaú

**Evento**: Itaú Tech Meetup em parceria com Data Hackers  
**Tema**: A Fronteira da Computação Quântica e Quantum Machine Learning no Itaú Unibanco e no ICTI  
**Participantes**:
- **Monique**: Host / Comunicação (Data Hackers & Itaú)
- **Dra. Samuraí Brito**: Líder da área de Computação Quântica e Tecnologias Emergentes no Itaú e no ICTI. Doutora e pós-doutora em Informação Quântica (IIF/UFRN).
- **José Vitor ("Zé")**: Pesquisador do ICTI, mestre pela UFES (foco em correção de erros e algoritmos variacionais), Qiskit Advocate e astrofotógrafo amador.

---

## 1. Visão Estratégica e Posicionamento do Itaú em Quantum

- **A Coincidência Histórica**: Os 100 anos de história do Itaú coincidem com os 100 anos da formulação da mecânica quântica (1925–2025).
- **Abordagem Proativa ("Não ao Wait-and-See")**: O banco decidiu não esperar que os computadores quânticos estejam prontos no mercado para começar a aprender. Quem esperar a tecnologia amadurecer para se capacitar já terá chegado tarde demais.
- **Linha do Tempo Oficial de Quantum no Itaú**:
  - *2019*: Início do mapeamento de mercado global e benchmark com BigTechs e bancos internacionais.
  - *2020*: Estruturação de time multidisciplinar.
  - *2021*: Contratação da Dra. Samuraí Brito para liderar a estratégia institucional de Quantum e tecnologias emergentes.
  - *2022*: Primeiras PoCs em QML, otimização combinatória e simulação de Monte Carlo; fomento à educação interna.
  - *2023*: Mais de 6 casos de uso explorados; realização da 1ª Batalha de Quantum no Brasil; adesão à **IBM Quantum Network**.
  - *2025*: Lançamento oficial do **ICTI (Instituto de Ciência e Tecnologia Itaú)**.
  - *2026*: Mais de 10 casos de uso aplicados em finanças, ampliação de parcerias com UFPE, UFES, USP, MIT e Stanford.

---

## 2. A Realidade Atual: Produção vs. Pesquisa Aplicada

Samuraí Brito estabeleceu uma distinção fundamental:
- **O Itaú NÃO utiliza computação quântica de maneira produtiva em hardware real hoje.**
- **Motivo Técnico**: O hardware quântico global ainda está na era NISQ (*Noisy Intermediate-Scale Quantum*), com ruído térmico, taxas de erro elevadas e poucos *qubits lógicos* corrigidos.
- **Como o Itaú atua hoje**:
  1. *Estratégia "Research to Product"*: Focar no problema real de negócio, desafiar a melhor solução clássica do banco e testar abordagens quânticas via simulação e execuções controladas na nuvem (IBM Quantum Network).
  2. *Algoritmos Inspirados em Quântica (Quantum-Inspired)*: Modelos matemáticos que rodam na infraestrutura clássica atual trazendo ganhos imediatos de negócio.
  3. *Prontidão para a Vantagem Quântica*: Preparar a esteira para quando os processadores atingirem 800 a 1.600+ qubits lógicos (previsto nos roadmaps públicos entre 2027 e 2029).
  4. *Potencial Econômico*: Projeções da McKinsey estimam impacto de até **US$ 2 trilhões** até 2035 em valor gerado por tecnologias quânticas em diferentes indústrias.

---

## 3. Os Três Grandes Pilares de Quantum em Finanças

1. **Simulação**:
   - Aplicação de algoritmos de Monte Carlo quântico para **precificação de derivativos**, avaliação de risco de mercado e alocação de liquidez com aceleração quadrática de processamento.
2. **Otimização Combinatória**:
   - Otimização de carteiras de investimentos, balanceamento de portfólio e redução de alocação de capital regulatório.
3. **Quantum Machine Learning (QML)**:
   - Uso de propriedades quânticas (superposição, emaranhamento e interferência) para criar espaços de representação matemática superiores aos clássicos.

---

## 4. O Poder dos Conceitos Quânticos: Moedas e Superposição

- **O Bit Clássico**: A analogia da moeda parada — ou é cara (0) ou é coroa (1). Para cada nova configuração de 4 moedas, são necessárias novas moedas físicas.
- **O Qubit em Superposição**: A analogia da moeda girando com um "peteleco". Enquanto gira, existe uma distribuição contínua de probabilidades entre 0 e 1.
  - 4 moedas clássicas = 1 estado por vez;
  - 4 qubits em superposição = 16 estados processados simultaneamente;
  - **300 qubits em superposição** = capacidade de representar mais estados simultâneos do que o **número total de átomos no universo observável**.

---

## 5. Casos Reais com Artigos Científicos Publicados pelo Itaú/ICTI

1. **Predição de Evasão de Clientes (Churn)**:
   - Problema: Identificar clientes com propensão a cancelar contas ou sacar recursos nos próximos 3 meses.
   - Resultado: Modelo inspirado em quântica superou o benchmark clássico em **+2% na assertividade de churn**.
   - Redução brutal de esforço computacional: provou-se matematicamente uma redução de **1 milhão de operações clássicas para apenas 100 operações quânticas** no treinamento.
2. **Propensão a Crédito para Pequenas e Médias Empresas (PJ / PMEs)**:
   - Aplicação de Quantum Neural Networks (QNN).
   - O *Gini Score* (métrica de qualidade do modelo de crédito) subiu de **53,7% (melhor modelo clássico do banco) para 54,1%**.

---

## 6. Quantum Machine Learning na Prática: VQC (José Vitor)

- **VQC (Variational Quantum Classifier)**:
  - Algoritmo quântico **híbrido**:
    1. *Data Encoding*: Mapeamento do dado tabular clássico em estados quânticos (portas de rotação).
    2. *Ansatz*: O circuito quântico parametrizado (análogo à arquitetura e pesos/vieses de uma rede neural), onde portas de emaranhamento correlacionam os qubits.
    3. *Medição Probabilística*: Colapso da função de onda gerando uma distribuição estatística.
    4. *Loop Clássico*: Otimizador clássico (Scipy, gradiente descendente) recalibra os parâmetros $\theta$ do circuito para minimizar a função de perda (*loss function*).
- **Quantum Kernel Trick**: Mapeamento dos dados para o **Espaço de Hilbert**, permitindo separar conjuntos de dados linearmente inseparáveis no espaço clássico 2D/3D.
- **Gargalo Atual de Pesquisa**: No universo quântico **ainda não existe análogo ao Backpropagation**.

---

## 7. Como se Capacitar e Entrar na Área de Quantum no Itaú

- **"Você NÃO precisa ser físico"**: Para trabalhar com computação quântica aplicada e QML, o kit essencial é:
  1. **Álgebra Linear sólida**: Matrizes, vetores, operações com números complexos;
  2. **Python fluente**: Bibliotecas como NumPy, SciPy e SDKs quânticos;
  3. **SDKs de Mercado**: **Qiskit** (IBM Quantum), **PennyLane** (Xanadu), **Cirq** (Google);
  4. **Noções fundamentais de física quântica**: Superposição, emaranhamento, interferência e medição.
- **Livros e Materiais Recomendados**:
  - *Introduction to Classical and Quantum Computing* — Thomas G. Wong;
  - *Quantum Computing for Babies* — Chris Ferrie (didático e lúdico para abrir a mente);
  - *Introdução à Computação Quântica: Teoria e Prática com Python e Qiskit* — Marcos César de Oliveira e Felipe Fanchini (referência nacional brasileira);
  - *Quantum Computation and Quantum Information* — Nielsen & Chuang (a "bíblia" avançada);
  - Curso gratuito do SENAI Cimatec e aulas de John Watrous (IBM Quantum).
- **Portas Abertas no ICTI**: Bolsas de pesquisa científica, vagas para pesquisadores e colaborações acadêmicas abertas pelo portal `carreiras.itau.com.br` e ICTI.
