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

***Particionando os dados*** <br/>
Para particionar os dados foi usado o train_test_split, no codigo a baixo é possível observar a partições a serem criadas ondde foi dado 25% do dataset aos dados de teste e foi dado para o Random_state 1, e foi usado o stratify com a variável alvo de forma a mantes o equilíbrio entre os valores ocupados e não ocupados nas partições criadas. 
```text
Xtreino,Xrest,ytreino,yrest =train_test_split(data_file.drop("ocupado",axis=1),data_file[["ocupado"]],test_size=0.50, random_state=1,stratify=data_file.ocupado)
```

***Arvores de decisão*** <br/>
Na imagem a baixo é possível observar a importação do algoritmo Arvores de decisão, que foi graças a esse algoritmo que permitiu criar um modelo com o melhor score. É possível também observar na imagem  o modelo a treinar com os dados de treino (Xtreino, e ytreino).
<p align="center">
  <img src="Imagens/Arvores de decisão.png" alt="OpenMontage" width="700">
</p>

***Obtendo o score do modelo com os dados de teste*** <br/>
Na imagem a baixo é possivel observar o score obtido com os dados de teste.
<p align="center">
  <img src="Imagens/score do modelo treinado.png" alt="OpenMontage" width="700">
</p>

***Criação da grelha de valores do GridSearchCV*** <br/>
No codigo a baixo é possível observar a importação do GridSearchCV(Tuning) que serviu para procura do melhor modelo, e foram usados os hiperparâmetros: Profundidade máxima(max_depth), Amostras mínimas divididas(min_samples_split), Minimo de amostras de folha (min_samples_leaf). 
```text
grelha_valores={'criterion':['gini','entropy'],'max_depth':[2,3,4,5,10,20,30],"min_samples_split":range(1,20),"min_samples_leaf":range(1,15)}
```
***Treinando o modelo Tuning*** <br/>
Na imagem a baixo é possivel observar a procura do melhor modelo baseando-se no modelo já criado com a Arvores de decisão e com os hiperparâmetros definidos anteriormente na grelha de valores, foi também fornecido 5 partições para a CV. 

<p align="center">
  <img src="Imagens/Treinando o modelo Tuning.png" alt="OpenMontage" width="700">
</p>

***Melhores parâmetros obtidos no Tuning e o respetivo score*** <br/>
Na imagem a seguir é possivel observar os melhores parâmetros obtidos no Tuning e o respetivo score.
<p align="center">
  <img src="Imagens/Melhores parâmetros obtidos no Tuning.png" alt="OpenMontage" width="300">
</p>

***Prevendo os valores da partição Xteste*** <br/>
No codigo é possivel observar o modelo_otimo(tuning) a prever os valores de ocupação com as variáveis preditoraspresentes na partição Xteste.

```text
resultado_arvoreDecisão=modelo_otimo.predict(Xteste)
```

***Importação da métrica F1 e o respetivo score*** <br/>
Na imagem a baixo é possivel observar a importação da métrica f1_score e logo em seguida a respetiva  mplementação que foi usado os valores previstos pelo modelo_otimo(tuning), e os valores reais da variável yteste. 
<p align="center">
  <img src="Imagens/Score metrica F1.png" alt="OpenMontage" width="700">
</p>

***Matriz de confusão*** <br/>
Na imagem a baixo é possivel observar a criação da matriz de confusão que serve para avaliar o grau de Precisão e Sensibilidade do nosso modelo ótimo. 
<p align="center">
  <img src="Imagens/Matriz de confusão.png" alt="OpenMontage" width="700">
</p>

***Prevendo os dados para o dataset não classificados***<br/>
***Importar o dataset não classificados***<br/>
No final foi fornecido um dataset com dados sem os valores se estão ocupado ou não e o objetivo é prever a ocupação. Na imagem a baixo é possivel observar a importação do mesmo.
<p align="center">
  <img src="Imagens/Dataset não classificados.png" alt="OpenMontage" width="700">
</p>

***Previsão com os dados não classificados***<br/>
Na imagem a baixo é possivel observar o modelo_otimo a prever a ocupação com os dados do dataset não classificados, e é também criada uma tabela com id e os dados de ocupação previstos. É possivel também observar a tabela com o id e os valores de ocupação previstos. 
<p align="center">
  <img src="Imagens/Previsão com os dados não classificados.png" alt="OpenMontage" width="700">
</p>

