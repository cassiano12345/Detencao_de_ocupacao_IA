### 🧠Projeto de deteção automatica de ocupação de espaço

A deteção automática da ocupação em edifícios pode ser usada com sucesso na implementação de estratégias de
poupança de energia. Como, por razões de privacidade, não é viável, na maior parte das vezes, a instalação de
câmaras de vigilância, é necessário que a presença de ocupantes num espaço interior se faça através duma
monotorização mais indireta. Para o efeito foram colocados num espaço a monitorizar sensores para a medição da
humidade, temperatura, luz e dióxido de carbono. Durante um período de tempo foram então recolhidos, em vários
momentos do dia, os dados registados por esses sensores, juntamente com a indicação da presença ou não de
ocupantes. <br/>

O objetivo do projeto foi criar um modelo que permita detetar automaticamente a ocupação do espaço, com base na informação dos sensores de humidade, temperatura, luz e dióxido de carbono. Na construção do modelo foram exploradas 3 técnicas de Machine Learning que são: Regressão Logística, Os K Vizinhos Mais Próximos e Árvore de Decisão. Para a realização do projeto foi usada a linguagem Python.

### Algumas funcionalidades a destacar
***Tabela com dados dos sensores*** <br/>
Na imagem a baixo é possivel observar a tabela com os dados obtidos dos sensores.

<p align="center">
  <img src="Imagens/Dados dos sensores.png" alt="OpenMontage" width="700">
</p>

***Relação das variaveis independentes com a variável alvo*** <br/>
Na imagem a baixo é possivel ver a relação das variáveis que contém os dados dos sensores com a variável ocupado.
<p align="center">
  <img src="Imagens/Relação entre variaveis.png" alt="OpenMontage" width="700">
</p>

***Grafico Heatmap*** <br/>
Na imagem a baixo é possivel observar o grafico Heatmap.
<p align="center">
  <img src="Imagens/Grafico pandas.png" alt="OpenMontage" width="700">
</p>

***Particionando os dados***
Para particionar os dados foi usado o train_test_split, na imagem a baixo é possível observar a partições a serem criadas ondde foi dado 25% do dataset aos dados de teste e foi dado para o Random_state 1, e foi usado o stratify com a variável alvo de forma a mantes o equilíbrio entre os valores ocupados e não ocupados nas partições criadas. 
<p align="center">
  <img src="Imagens/Particionando a Tabela.png" alt="OpenMontage" width="700">
</p>

***Arvores de decisão***
Na imagem a baixo é possível observar a importação do algoritmo Arvores de decisão, que foi graças a esse algoritmo que permitiu criar um modelo com o melhor score. É possível também observar na imagem  o modelo a treinar com os dados de treino (Xtreino, e ytreino).
<p align="center">
  <img src="Imagens/Arvores de decisão.png" alt="OpenMontage" width="700">
</p>

***Arvores de decisão***

### Variáveis
- Xtreino:
- Xrest:
- ytreino:
- yrest:
