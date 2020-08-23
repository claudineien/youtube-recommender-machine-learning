<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>

<h1 align='center'>2o Modelo Machine Learning</h1>
<p>Neste modelo você aprenderá a fazer um labelling, ler um dataset que esta em um arquivo .csv, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo RandomForestClassifier, analisar sua probabilidade de acerto de predição e sua precisão curva <a href="blank_">ROC</a>
</p>

<h3>LABELLING</h3>
<p>Abrir o arquivo <a href="blank_">raw_data_sem_labels.csv</a> no excel através da opção de importar dados de um arquivo .csv, criar a coluna Y (*1) e nesta coluna inserir o número 0 nas linhas cujo título do vídeo não interesse e não quer assistir ou inserir 1 nas linhas cujo vídeo seja interessante e quer assistir.</p>

<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
    <ul>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (*2)</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
        <li>Plotar - Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
    </ul>

<p><strong>Aprender mais :</strong><br>
<a href="https://strftime.org/">Tabela de códigos para converter strings em datas no Python</a><br>
<a href="http://gskinner.com/RegExr/">Testador de expressões regulares</a><br>
<a href="https://numpy.org/doc/stable/reference/arrays.datetime.html">Numpy : Timedelta</a><br> 
<a href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html">Pandas : Time/Date</a><br>
<a href="https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html#sphx-glr-auto-examples-model-selection-plot-precision-recall-py">Curva de Precision/Recall</a><br>
<a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a><br>
<a href="">Dados train and test</a><br>
</p>

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.
</p>

<p><strong>Nota :</strong><br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y para padronizar o ensinamento<br>
(*2) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Este atrapalha a eficiência do modelo machine learning.<br>
</p>

<hr>
<h3>PLOTAR - EXIBIR DADOS EM GRÁFICO</h3>
    <ul>
        <li>Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
        <li>Permite analisar os dados para desenhar o melhor cenário de para o modelo machine learning</li>
    </ul>
<p>A amostra por data, indica que no final do período há muito mais vídeos, provavelmente a busca do youtube faz seleção aleatória específica, desobedecendo a instrução de ordem estabelecida ao <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0_dataset_collect_clean.md">COLETAR DATASET</a>, deixando a maior quantidade dos vídeos por último.</p>
<p>O pico de vídeos do final do período é um fator de atenção e que deve ser melhor analisado em um ambiente machine learning real.</p>
</p>

<hr>
<h3>MODELO MACHINE LEARNING</h3>
Este primeiro modelo será para analisar rapidamente a influência da predição do modelo machine learning com duas features. Utilizaremos a Decision tree (Árvore de decisão).
    <ul>
        <li>Separar dados de treino e dados de teste - Aplicar validação temporal por ser uma time series</li>
        <li>Executar o algoritmo Decision tree</li>
        <li>Treinar modelo machine learning (*3)</li>
        <li>Executar a probabilidade da Decision tree (*4)</li>
        <li>Aplicar a métrica de média de precisão (*5)</li>
        <li>Tratar o ranking dos vídeos (*5)</li>
        <li>Aplicar a curva <a href="blank_">ROC</a></li>
        <li>Exibir a Decision tree para analisar o modelo</a></li>
    </ul>

<p><strong>Aprender mais :</strong><br>
<a href="https://www.youtube.com/watch?v=Y1XAP6omGzo">Entendiendo las Curvas ROC</a><br>
<a href="blank_">ROC</a><br>
<a href="https://scikit-learn.org/stable/modules/generated/sklearn.tree.plot_tree.html">Método plot_tree</a><br>
</p>

<br>
<p><strong>Dica :</strong><br>
50% para treino e 50% para teste : Por ser uma time series, é quase 100% certeza que os dados de treino serão diferentes dos dados de validação, e a metodologia mais eficiente é dividir os dados o mais próximo possível de 50%<br>
Arvore de decisão : Uma das melhores maneiras de entender a relação das features (recursos) com o target (alvo)<br>
</p>

<p><strong>Nota :</strong><br>
(*3) Há bibliotecas com métodos para separar os dados de treino e os dados de teste, que pode ser em percentual e/ou em quantidade<br>
(*4) A probabilidade mostra o valor provavel de positivo 1-vídeos que quer assistir e/ou negativo 0-vídeos que não quer assistir. Queremos somente a probabilidade de ser 1.<br>
(*5) Métrica de média de precisão : o método average_precision_score, nos dará o nosso baseline, e seja qual for o modelo machine learning a average_precision deve ser o mais próximo possível de 1.0. Esta serve para melhor visualizarmos o ranking dos vídeos : dos mais interessantes para os menos interessantes. Em cada ponto de corte definido ao calcular precision e recall aparecerá uma curva, a área sobre a curva é a average precision.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<h3>INTERPRETAR A DECISION TREE</h3>
<p>Uma boa forma de entender como o as features (recursos) estão se relacionando com o target (alvo)</p>
<img src=".\notebook\dados_brutos\decisiontree.png">
</p>
<p>
Houve um balanceamento (class_weight="balanced") no peso dos vídeos, que mostra no nó raiz 15110.0 visualizações em uma amostra de vídeos de 228, índice esta em 50% (gini) e os valores balanceados [114.0,114.0]. Então :<br>
<ol>
    <li>quando inferior ao nó raiz (à esquerda), no 1o nível de nó vemos que a quantidade por dia é inferior a 1 visualização por dia para 133 amostras de vídeo, no 2o nó à esquerda as 14 amostras são exemplos negativos 0.0, não interessantes. No nó a direita há mais amostras e estes provavelmente são vídeos que interessam por ter 92.625 positivos.
    </li>
    <li>quando superior ao nó raiz (à direita), no 1o nível de nó vemos que a quantidade pode ser menor ou igual ou superior a 26712.0. Se inferior temos 20 amostas negativas 0.0, não interessantes. A direita há muita amostra porem pela classificação 21.375 provavelmente são vídeos que não interessam.</li>
</p>

<br>
<hr>
<p>Fontes :
    <ul>
        <li><a href="https://curso.mariofilho.com/">Curso Solução Completa de Data Science - Instrutor Mario Filho-Kagle Gran Master</a></li>
    </ul>
</p>

<!--
<p>labelling</p>
<p>Active learning</p>
feather-format 0.4.1
pip install feather-format
https://pypi.org/project/feather-format/
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>-->
