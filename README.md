# **Análise Exploratória e Limpeza de Dados: Risco de Crédito**
# **"O histórico financeiro realmente dita as regras na aprovação de crédito?"**


# **1. Objetivo do Projeto** 

Este relatório visa documentar a análise exploratória da base de dados Credit.csv. 
Tem como objetivo principal responder à pergunta orientadora de negócio: “O histórico financeiro impacta a aprovação de crédito?”, além de identificar os demais padrões socioeconômicos e financeiros que fazem parte do perfil de risco e a inadimplência. 

# **2. Preparação e Tratamento dos Dados** 

A base de dados passou por um processo extenso de limpeza. Foram tratados seguindo a ordem: seleção das colunas que são úteis e que serão utilizadas para responder à pergunta orientadora, tradução do nome das colunas e variáveis, padronizando também as mesmas (ex: status_conta, historico_credito, classificação). 
Foi criada também a coluna classificacao_binaria (1 para bom, 0 para ruim) para que cálculos estatísticos de tendência sejam criados. Após, foi realizada a remoção de Outliers separados por categoria para que os valores de empréstimo sejam condizentes com cada finalidade. 
Durante a exploração, foi identificado uma forte tendência histórica na variável perfil_pessoal. A base original agrupa mulheres casadas, separadas e divorciadas em somente uma categoria, enquanto o perfil masculino é registrado de separadas formas. Essa limitação estrutural exige cuidado na aplicação desses dados em modelos mais modernos de risco focados em igualdade de gênero. 

## **3. Análise Exploratória**
### **3.1. Distribuições Gerais** 

A distribuição da variável alvo (classificacao) mostra desbalanceamento comum no mercado de crédito: a maioria das concessões de crédito resulta na classificação “bom”. A variável idade_anos se concentra em jovens e adultos de 20 a 35 anos, com queda nas idades avançadas. O valor_emprestimo apresenta assimetria à direita, o que indica predominância de solicitações de baixo e médio valor. 

### **3.2. Matriz de Correlação (Heatmap)**

Para validar as relações do dataset, foi gerada uma Matriz de Correlação. O que 
revelou dois achados fundamentais: 
  • Coerência Operacional (0.62): Existe uma forte correlação positiva entre valor_emprestimo e duracao, provando que solicitações de alto valor exigem prazos mais flexíveis. 
  • O Risco (-0.21): A duracao apresenta uma correlação negativa com a nota de crédito do cliente, confirmando que o alongamento do prazo puxa a classificação do cliente para baixo (em direção à inadimplência). 
  
## **3.3. Relação: Finalidade do Empréstimo vs. Classificação de Risco**

O cruzamento do motivo do empréstimo com a taxa de aprovação mostrou perfis de risco diferentes que exigem políticas de crédito personalizadas: 
   • Baixo Risco: Categorias como rádio/TV e carro usado apresentam as maiores proporções de “bons pagadores”, configurando como as linhas de crédito mais seguras da agência. 
  • Alto Risco: A categoria carro novo possui o maior volume de solicitações, mas carrega a maior barra absoluta de “calotes”, sendo o maior ofensor financeiro em volume de capital perdido. 
  • Médio Risco: A categoria educação apresenta uma taxa de falha próxima a 50%, configurando-se como a finalidade mais instável e perigosa para aprovação automática. 

## **3.4. Relação Principal: Histórico Financeiro vs. Classificação**

O cruzamento do histórico financeiro responde à pergunta orientadora. Clientes com histórico de “Crítico/Outros créditos” concentram o maior volume de pagadores classificados como “bom”. Ao contrário, clientes com status “Sem crédito/Tudo pago” apresentam a classificação “ruim” mais elevada comparado ao volume total. O que significa que o modelo de aprovação prefere clientes com o financeiro ativo (mesmo com exceções) do que com risco da falta de histórico. 

## **3.5. Padrões e Tendências (Prazo e Idade)** 
A análise de tendências em gráficos de linha retornou os dois maiores ofensores do crédito: 
  • Tempo (duracao): O risco cresce de forma linear. Contratos curtos (de até 1 ano) são seguros, enquanto prazos longos (mais de 3 anos) ficam em uma área crítica, passando 50% de inadimplência. 
  • Demográfico (idade_anos): O risco é contrário à idade. O grupo de 18 a 25 anos apresenta a maior volatilidade e risco da base. À medida que o cliente atinge a faixa dos 35 a 45 anos, o risco cai de forma drástica, mostrando a estabilidade relacionada a maturidade profissional. 
  
# **4. Conclusões** 
Sim, o histórico financeiro impacta a aprovação, mas de forma contra-intuitiva. A ausência de histórico é matematicamente mais arriscada para a instituição do que um histórico longo e crítico, pois este último oferece previsibilidade de comportamento. 

Com base nos dados explorados, o perfil ideal de baixo risco da instituição é o cliente de meia idade (35 a 45 anos), que solicita créditos menores por exemplo eletrodomésticos, para pagamento em curto prazo (até 12 meses).
