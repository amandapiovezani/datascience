# TESTE 1


## Exercício 1
Suponha que você possui uma base de dados rotulada com 10 classes não balanceadas, essa base é formada por 40 features de metadados e mais 3 de dados textuais abertos.
Para todos os itens: Informe as bibliotecas usadas, se necessário, o motivo de cada decisão, explore as possibilidades.


   a) Descreva como faria a modelagem dessas classes.
   R: Partindo da premissa de uma base rotulada, podemos utilizar um modelo supervisionado para modelagem das classes. As etapas para modelagem incluem:
       i) Análise exploratória dos dados: para visualizar e entender a distribuição das classes, tratar dados ausentes, normalizar e/ou padronizar os dados. Pandas, Numpy, Matplotlib, Seaborn, Plotly são algumas das bibliotecas clássicas que podem ser utilizadas nessa etapa. Scikit-learn também oferece funcionalidades para o pré-processamento e é uma opção, por exemplo, para imputação (preenchimento de valores ausentes), codificação de variáveis categóricas, etc.;
       ii) Extração de características: para extrair as mais relevantes dentro do total de 40 features de metadados;
       iii) Processamento textual: para processamento dos dados textuais abertos, com objetivo de convertê-los em formato numérico. SpaCy é a biblioteca do python sugerida para essa etapa;
       iv) Modelagem e treinamento do modelo de classificação: aqui podemos explorar diferentes algoritmos de classificação, como o Random Forest, SVM, redes neurais, etc. As bibliotecas do python sugeridas são Scikit-learn, TensorFlow, PyTorch;
       v) Ajuste de parâmetros do modelo escolhido: para otimizar o desempenho do modelo, podemos ajustar os hiper parâmetros;
      


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



