# TESTE 1


## Exercício 1
Suponha que você possui uma base de dados rotulada com 10 classes não balanceadas, essa base é formada por 40 features de metadados e mais 3 de dados textuais abertos.
Para todos os itens: Informe as bibliotecas usadas, se necessário, o motivo de cada decisão, explore as possibilidades.


   a) Descreva como faria a modelagem dessas classes.
   R: Partindo da premissa de uma base rotulada, podemos utilizar um modelo supervisionado para modelagem das classes. As etapas para modelagem incluem:
       i) Análise exploratória dos dados: para visualizar e entender a distribuição das classes, tratar dados ausentes, normalizar e/ou padronizar os dados. Pandas, Numpy, Matplotlib, Seaborn, Plotly são algumas das bibliotecas clássicas que podem ser utilizadas nessa etapa. Scikit-learn também oferece funcionalidades para o pré-processamento e é uma opção, por exemplo, para imputação (preenchimento de valores ausentes), codificação de variáveis categóricas, etc.;
       ii) Extração de características: para extrair as mais relevantes dentro do total de 40 features de metadados;
       iii) Processamento textual: para processamento dos dados textuais abertos, com objetivo de convertê-los em formato numérico. SpaCy é a biblioteca do python sugerida para essa etapa;
       v) Ajuste de parâmetros do modelo escolhido: para otimizar o desempenho do modelo, podemos ajustar os hiper parâmetros;
       iv) Modelagem e treinamento do modelo de classificação: aqui podemos explorar diferentes algoritmos de classificação, como o Random Forest, SVM, redes neurais, etc. As bibliotecas do python sugeridas são Scikit-learn, TensorFlow, PyTorch;
      


   b) Ao finalizar essa modelagem, como iria apresentar essa modelagem para a área contratante?
   R: A abordagem da apresentação muda um pouco quando consideramos o tipo de público da área contratante. Na presença apenas uma equipe comercial, a apresentação deve conter essencialmente valores, gráficos e imagens que se relacionem com o propósito do cliente. Que aponte um possível impacto positivo sobre o crescimento ou qualidade do setor em questão.
   Por outro lado, considerando que o público seja mais técnico, essa apresentação, além desses pontos acima, deve trazer também, informações mais detalhadas do modelo escolhido, por exemplo, as métricas de desempenho, como precisão, recall, F1-score, matriz de confusão. Podemos, ainda, usar técnicas como SHAP values para explicar as decisões do modelo, para destacar as features que mais influenciaram nas predições do modelo e no caso de termos um deploy do MVP (Minimum Viable Product) para testes, podemos mostrar como o modelo funciona com novos dados.


   c) Como faria a validação desse modelo?
   R: Para validação podemos começar com um método computacionalmente leve, o Hold-out, separando nossos dados em conjuntos de treinamento, o qual será usado para treinar o modelo (80% do volume total) e teste (20% do volume total), que tem o objetivo de mostrar o quanto o modelo está acertando quando recebe dados novos. Contudo uma segunda opção é rodar uma Cross-validation, ainda para avaliar o desempenho do modelo escolhido, mas utilizando uma lógica diferente. No Cross-validation, embora demande um pouco mais de tempo e recurso de máquina, temos a oportunidade de treinar nosso modelo em diferentes subgrupos de dados, ao invés de apenas um único como acontece no primeiro modelo, que deixa o score dependente da forma que foi subdividido nos 80 e 20%. No Cross-validation, o dataset inteiro é randomicamente dividido em k grupos, sendo um deles o de teste. Independente da escolha do modelo, a cada treinamento temos as métricas associadas e podemos fazer a avaliação, no caso de classificação seria olhar a precisão, recall, F1-score. Scikit-learn é a biblioteca do python que podemos utilizar nessa etapa.


   d) Supondo que esses dados são recebidos diariamente, como iria trabalhar com esse desafio?
   R: Neste caso é necessário construir uma estrutura que absorva as etapa, indo da automação do fluxo de dados, implementando pipelines de pré-processamento dos novos dados e treinamento periódico do modelo, garantindo que ele estará atualizado.


   e) Como levaria esse projeto para um ambiente produtivo?
   R: Colocar o modelo de classificação em produção requer atenção para garantir que ele funcione de forma eficiente, confiável e segura.
   Quanto ao modelo, se o treinamento não for muito recente, precisamos verificar a necessidade de atualizar o treinamento com novos dados e aqui usar as métricas de validação para avaliar o desempenho e certificar que o modelo atende aos requisitos. Então salvar o modelo no formato adequado para produção. Para essa tarefa de exportar o modelo podemos usar o pickle do python. O próximo passo é integrar o modelo na infraestrutura atual de produção, certificando sobre os servidores, APIs, etc., bem como garantir que as dependências do modelo estejam disponíveis no ambiente de produção. Neste momento, os testes já podem ser realizados no ambiente de produção buscando validar se o comportamento está dentro do esperado e aqui, os testes devem ser os mais rigorosos possíveis, incluindo teste unitário, de integração e de estresse se necessário. Precisamos ainda incluir o monitoramento contínuo para, por exemplo, acompanhar as falhas e as métricas de desempenho. Posteriormente, seria ficar atento com a atualização e sustentação do modelo, planejar o fluxo regular de treinamento, cuidar e alinhar a segurança com os requisitos do sistema atual, por exemplo, através de medidas de criptografia, autenticação, etc. Fazer a documentação do modelo, considerar escalabilidade e sistema de backup e recuperação. E uma etapa final extremamente importante é o treinamento e suporte ao usuário final, focando na comunicação efetiva das equipes que estarão utilizando ou mantendo o modelo. Disponibilizar para esse time, além do suporte, também, uma documentação técnica, se for necessário. De forma geral essa etapa é muito delicada e deve ser realizada com muita cautela.


EXTRA - Existe mais algo que gostaria de relatar sobre esse caso?
R: Este caso é um ótimo exemplo de classificação padrão, mas é importante destacar que existem aspectos específicos do setor de aplicação, que devem ser considerados neste fluxo, desde modelagem até a implementação em produção. Por exemplo, a natureza dinâmica dos dados; a possibilidade de incorporar features (feature engineering) específicas do setor, neste caso de telecomunicações; garantir a LGPD para dados sensíveis; verificar a complexidade de integração do novo modelo com sistemas legados; verificar se a classificação precisa ocorrer em tempo real ou em batch, o que pode influenciar na arquitetura da implementação; compreender a conexão que o modelo de classificação faz com outros sistemas e serviços da empresa, estando atento a possíveis conflitos; e por fim, manter um relacionamento colaborativo com as equipes de TI, operações e outros departamentos envolvidos direta ou indiretamente com o modelo.


## Exercício 2

Suponha que você tenha uma base de dados de vendas de uma loja de varejo que inclui informações sobre produtos, clientes, datas de compra e valores das vendas. A base de dados possui, em média, 10.000 registros diários.

Para todos os itens: Informe as bibliotecas usadas, se necessário, o motivo de cada decisão, explore as possibilidades.

    a) Como você iria explorar os dados para obter insights sobre o desempenho das vendas.
    R: Para esta etapa gosto de utilizar o jupyter notebook para construir o código, carregar os arquivos, aplicar estatística descritiva e fazer a visualização gráfica. Então dentro de um ambiente virtual do python, por exemplo venv ou conda, faço a instalação das bibliotecas Pandas (para manipulação e análise dos dados tabulares), Numpy (para operações numéricas), Matplotlib e Seaborn (ambos para visualização de dados), as quais serão carregadas em um arquivo notebook. Ao carregar essa base de dados como um dataframe do pandas, é possível listar a estrutura das colunas, os tipos de arquivos de cada uma, verificar e tratar os dados faltantes ou nulos e em seguida podemos explorar os dados por meio de gráficos de linhas por exemplo, tendo a coluna data no eixo x e número de produtos no eixo y, isso retornaria o desempenho das vendas ao longo do tempo. Também podemos usar gráfico de barra para visualizar os produtos mais vendidos e suas categorias. Histogramas podem ajudar na visualização da distribuição dos valores de venda. 

    b) Como você responderia as seguintes questões:
        i. Qual é o desempenho de vendas ao longo do tempo? 
        R: Faria um gráfico de linhas mostrando as tendências temporais.

        ii. Quais são os produtos mais vendidos? 
        R: Um gráfico de barras ou a própria tabela de dados ordenando de forma descendente a colunas de vendas, é capaz de mostrar os produtos mais vendidos. 

        iii. Como as vendas variam por categoria de produtos? 
        R: Assumindo que já exista a coluna categoria do produto, vamos plotar um gráfico de barras empilhadas ou pizza, para comparar as vendas por categoria. 

        iv. Qual é a distribuição dos valores de venda? 
        R: Plotar histogramas ou bloxplots pode ajudar entender essa distribuição. 

        v. Como os preços dos produtos afetam as vendas? 
        R: Podemos fazer um gráfico de dispersão para visualizar a relação entre preços e vendas. 

        vi. Qual é o perfil dos principais clientes em termos de compras?
        R: Podemos responder com uma clusterização K-means e posterior histograma das features dos clientes (explicado na questão c abaixo). Com isso será possível responder sobre o perfil de clientes que compram pouco, médio e muito, e sobre o valor dos produtos que costumam pagar. 


    c) Como você faria para identificar grupos de clientes nessa base de dados?
    R: Utilizaria um modelo de machine learning para clusterização do tipo não supervisionado como K-means por exemplo, para segmentação de clientes. No python podemos usar a biblioteca Scikit-learn para a clusterização e o Seaborn e Matplotlib para a visualização gráfica dos grupos. Considerando que fizemos o tratamento das colunas de input para formatos numéricos, treinamos o modelo e escolhemos o número de grupos igual a 4, ao final, para cada grupo apontado pelo modelo, podemos gerar histogramas das features de cada grupo e é onde teremos recursos para explicar os diferentes grupos, mas também apontar semelhanças entre eles, caso venham apresentar.   

    d) Qual teste estatístico você usaria para provar uma hipótese referente aos segmentos de clientes? e como iria aplicá-lo?
    R: A escolha de um teste estatístico vai depender da natureza dos dados e da hipótese a se validar. Neste contexto dos clientes, queremos avaliar as diferenças entre grupos e podemos usar a ANOVA (Análise de Variância) e se necessário, testes de comparação pós-hoc, caso ANOVA reporte que há diferenças significativas nas médias entre os segmentos de clientes. A aplicação do teste ocorre após o K-means e a coleta de informações relevantes. Também com python usando a biblioteca scipy.stats


EXTRA - Pensando nos dados acima, seria possível fazer mais algum tipo de análise?

## Exercício 3

Suponha que você tenha uma base de dados contendo textos jurídicos, como decisões judiciais, petições e documentos legais. A base de dados inclui informações sobre o conteúdo do texto, data, jurisdição e outras informações relevantes. Seu objetivo é criar um sistema de recomendação que sugira textos jurídicos semelhantes a um texto de referência.

Para todos os itens:  Informe as bibliotecas usadas, se necessário, o motivo de cada decisão, explore as possibilidades.

    a) Descreva como você desenvolveria o sistema de recomendação que recebe um texto de referência e sugere os textos mais semelhantes a ele na base de dados.
    R: Neste caso podemos aplicar as técnicas de processamento de linguagem natural (PLN) e modelagem de tópicos. A base programática será python onde utilizaremos a biblioteca SpaCy para o pré-processamento dos dados, fazendo a limpeza do texto, remoção de stop words, tokenização, etc. Finalizado o pré-processamento, faremos a representação/vetorização do texto e aqui podemos usar a técnica TF-IDF (Term Frequency-Inverse Document Frequency) por meio do Scikit-learn, para representar a importância relativa de cada termo em um documento em relação à um conjunto de documentos. A métrica usada nessa etapa é a similaridade cosseno e os textos com maior similaridade são recomendados. Essa etapa representa o texto em formato numérico. Então utilizamos a biblioteca gensim para a modelagem de tópicos e cálculo da similaridade de documentos. Nesta etapa já é possível exibir os textos mais semelhantes. Essa recomendação pode ser feita assim construindo o código ou com o uso de framework, como por exemplo o surprise. 
    
    b) Como você avaliaria esse sistema de recomendação?
    R: A avaliação deve considerar o desempenho do sistema em relação a diferentes métricas, buscando assim um modelo que entregue informações relevantes. Para essa tarefa existem algumas opções: Top-K Precision, Top-K Recall, F1-Score, NDCG (Normalized Discounted Cumulative Gain), MAP (Mean Average Precision), Avaliação subjetiva, Avaliação cruzada, Teste A/B. Na etapa de avaliação é importante escolher métricas que estejam alinhadas com os objetivos específicos do sistema. Talvez combinar métricas qualitativas e quantitativas pode ser uma opção para uma visão mais ampla do desempenho do sistema.  

    c) Suponha que novos textos jurídicos sejam adicionados diariamente. Como você manteria o sistema de recomendação atualizado e garantiria que ele continue a fornece recomendações relevantes?
    R: Neste caso faríamos uma combinação das técnicas de PLN com aprendizado de máquina. Tendo em vista as etapas de desenvolvimento acima, vamos incluir agora, um conjunto de novas etapas que garantirão a atualização e aprendizado contínuo, e para isso ferramentas de sistemas como o Scheduler podem ser utilizadas para programar rotinas de atualização e processamento de novos textos diariamente. Bem como o uso de bibliotecas como Scikit-learn para o aprendizado de máquina, com o objetivo de treinar o modelo frequentemente e manter assim uma base que contempla as mudanças de preferências e de conteúdo jurídico. Além disso, um monitoramemto de desempenho, backup e controle de versão dos modelos treinados e dos pipelines desenvolvidos e obtenção do feedback do usuário são boas práticas.   
