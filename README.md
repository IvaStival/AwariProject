# AwariProject
## Classificação de placas de trânsito usando Convolutional Neural Network

Este estudo tem como tema a classificação de placas de transito usando redes neurais.

O reconhecimento de sinais e placas de transito são muito utilizados em sistemas autônomos como nos carros do google ou no auxilio ao motorista como os carros Tesla.

O objetivo principal é o entendimento mais aprofundado de redes neurais convolucionais.

## Dados

Os dados foram adquiridos através de uma competição do Kaggle. São placas de transito da Alemanha e podem ser encontradas aqui:
https://www.kaggle.com/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign

Os dados já estão divididos em treino e teste, estão devidamente catalogadas e possuem apenas imagens das placas.
São mais de 50mil imagens e 43 tipos diferentes de placas.

## Manipulação

As imagens estão com uma ótima qualidade, porém suas dimensões são diferentes. Dessa forma foi necessário o seu redimensionamento
para o tamanho padrão de 32x32. Também se viu necessário a equalização do contraste, pois muitas imagens são escuras.

## Bibliotecas para Modelagem

Para o treinamento e teste foi utilizado o Tensorflow/Keras. Já para a manipulação dos arquivos .cvs (Train.csv e Test.csv) foi utilizado o pandas.
Para as métricas foram salvos os históricos de cada época que o próprio modelo escolhido do Keras (Sequential) gera e também foi feita uma analise por classe no treinamento usando as metricas do sklearn (classification_report).
Já para gerar os gráficos o matplotlib e o seaborn foram os escolhidos.

## Modelo

O objectivo era alcançar o melhor resultado com um numero pequeno de épocas, no caso 30.
Para isso a proposta foi alterar alguns parametros de configuração do modelo, que são a quantidade de filtros das camadas de convolução, o tamanho desses filtros e por fim o tamanho das camadas
densas.

A rede é dividida em 3:
  - Camada de Covolução;
  - Camada Densa;
  - Camada de resultado;

E cada uma das divisões possuem suas próprias divisões.

Camada de Convolução:
  Nessa camada é onde ocorre a obtenção de características das imagens e também a redução no tamanho das mesmas;
  Essa camada é divida em mais 5 camadas de convolução, sendo a primeira a camada de entrada no tamanho de 32x32.

Camada Densa
  Essa camada é a rede neural clássica, onde ocorre o aprendizado;
  Aqui com 2 camadas, o tamanho delas varia de acordo com o objeto dos testes.

Camada de resultado:
  Retorna um array com a probabilidade da imagem atual ser cada uma das 43 possibilidades;

## Resultados
![alt text](https://github.com/IvaStival/AwariProject/plots/Step01/Hist_Conv_2x2_3x3_3x3_Dense_64_64_Filter_4_4_8.png?raw=true)


## Trabalhos futuros
Como esse modelo apresentado consegue somente classificar imagens onde só existe a placa, um trabalho futuro é a implementação de outro modelo que consiga identificar as placas em uma imagem bruta
e assim enviar para este modelo classificar.
Outro trabalho futuro é a implementação em video em tempo real.
E por fim a criação de um aplicativo para uso geral.
