<h5><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a>
</h5>
<h5>
<div>
  <table>
    <tr>
      <th>PROJETO</th>
      <th>OBJETIVO</th>
      <th>TIPO DE DADOS</th>
      <th>TIPO MACHINE LEARNING</th>
    </tr>
    <tr>
      <td>Recomendador de vídeos do youtube</td>
      <td>Entender Ciência de dados na prática</td>
      <td>Time Series</td>
      <td>Supervisionado</td>
    </tr>
    <tr>
        <td colspan="4">LinkedIn : https://www.linkedin.com/in/claudineien/</td>
    </tr>
  </table>
</div>
</h5>

<h1 align='center'>1o Modelo Machine Learning - DecisionTreeClassifier</h1>
<p>Nesta etapa aprenderemos a fazer um labelling, ler um dataset que esta em um arquivo .csv, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo DecisionTreeClassifier, analisar sua probabilidade de acerto de predição e sua precisão curva <a href="blank_">ROC</a>
</p>

<hr>
<h3>LABELLING</h3>
<p>
<ol>
    <li>Abrir o arquivo <a href="/2-dataset">raw_data_sem_labels.csv</a> em uma planilha eletrônica como ms excel, <a href="https://gsuite.google.com/intl/pt-BR/products/sheets/">google sheets</a> ou <a href="https://pt-br.libreoffice.org/descubra/calc/"> LibreOffice</a> através da opção de importar um arquivo .csv</li>
    <li>Criar a coluna Y (*1)</li>
    <li>Inserir na coluna Y o número 0 nas linhas cujo título do vídeo, provavelmente, não vamos assistir ou inserir 1 nas linhas cujo vídeo provavelmente, vamos assistir.</li><br>
    <p><strong>Importante:</strong><br>
    Baixar o arquivo <a href="/2-dataset">raw_data_with_labels.csv</a>, cujo o labelling foi aplicado para facilitar nosso entendimento em cada técnica executada</p>
</ol>
</p>

<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
<p>Primeiramente abrir o notebook <a href="/file-ipynb/2_Decision_Tree_Classifier.ipynb">2_Decision_Tree_Classifier.ipynb</a> e executar as linhas com os códigos para :
    <ol>
        <li>armazenar os dados do dataset em um dataframe utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (*2)</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
        <li>Plotar - Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
    </ol>
</p>

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.
</p>

<hr>
<h3>PLOTAR - EXIBIR DADOS EM GRÁFICO</h3>
    <ul>
        <li>Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
        <li>Permite analisar os dados para ajudar a desenhar o melhor cenário de para o modelo machine learning</li>
    </ul>

<p>O gráfico quantidade de vídeos por ano-mês, a seguir: mostra um grande volume muito alto de vídeos no final do período, em relação aos meses anteriores. Isto merece muita atenção, por que pode significar que o youtube deixou de trazer exatamente os últimos vídeos que solicitamos e com estas informações podemos evitaremos grande desbalanceamento na definição do dataset para treino e dataset para teste, consequentemente aumentarremos a otimização nos ajustes do modelo de predição machine learning.<br>
E uma das forma de aumentar a qualidade dos dataset é criar features por visualizações totais e visualizações por dia, por data de upload.<br>
<img src="/3-images/grafico_video_ano_mes.png">
</p>

<hr>
<h3>MODELO MACHINE LEARNING</h3>
Neste primeiro utilizaremos a Decision tree (Árvore de decisão para analisar rapidamente a influência da predição do modelo machine learning apenas com features view e view_por_dia por data de upload.
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

<br>
<p><strong>Dica :</strong><br>
50% para treino e 50% para teste : Por ser uma time series, é quase 100% certeza que os dados de treino serão diferentes dos dados de validação, e a metodologia mais eficiente é dividir os dados o mais próximo possível de 50%<br>
Arvore de decisão : Uma das melhores maneiras de entender a relação das features (recursos) com o target (alvo)<br>
</p>

<h3>INTERPRETAR A DECISION TREE</h3>
<p>Esta é uma boa forma de entender rapidamente como o as features (recursos) se relacionam ao target (alvo)
<img src="/3-images/decisiontree.png">
</p>

<p>
Aplicamos balanceamento (class_weight="balanced") no peso dos vídeos, e o nó raiz exibe dentro do total 15110.0 visualizações, amostra de 228 vídeos, heterogeneidade em 50% (gini) e os valores com peso balanceado em 114.0 exemplos negativos e 114.0 positivos. Então :<br>
<ol>
    <li>quando inferior ao nó raiz (à esquerda), no 1o nível do nó vemos que a quantidade por dia é inferior a 1 visualização por dia para 133 amostras de vídeo, no 2o nó à esquerda as 14 amostras são exemplos negativos 0.0, não interessantes. No nó a direita há mais amostras e estes provavelmente são vídeos que interessam por ter uma pontuação positiva de 92.625.
    </li>
    <li>quando superior ao nó raiz (à direita), no 1o nível de nó vemos que a quantidade pode ser menor ou igual ou superior a 26712.0. Se inferior temos 20 amostas negativas 0.0, não interessantes. A direita há muita amostra porem pela classificação 21.375 provavelmente são vídeos que não interessam.</li>
</ol>
</p>

<p><strong>Nota :</strong><br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y (Youtube) para facilitar nosso entendimento.<br>
(*2) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Este atrapalha a eficiência do modelo machine learning.<br>
(*3) Há bibliotecas com métodos para separar os dados de treino e os dados de teste, que pode ser em percentual e/ou em quantidade.<br>
(*4) A probabilidade mostra o valor provavel de positivo 1-vídeos que quer assistir e/ou negativo 0-vídeos que não quer assistir. Queremos somente a probabilidade de ser 1.<br>
(*5) Métrica de média de precisão : o método average_precision_score será nossa referencia inicial e seja qual for o modelo machine learning, tanto a average precision (average_precision_score) quanto a curva roc (roc_auc_score) devem estar o mais próximo possível de 1.0, que poderá ser a nossa <em>baseline</em> machine learning. Esta serve para melhor visualizarmos o ranking dos vídeos : dos mais interessantes para os menos interessantes. Em cada ponto de corte definido ao calcular precision e recall aparecerá uma curva, a área sobre a curva é a average precision.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<br>
<hr>
<p>Fontes de estudo :
    <ul>
        <li>Curso <a href="https://curso.mariofilho.com/">   
        Solução Completa de Data Science</a> - Instrutor Mario Filho-Kagle Gran Master</li>
        <li><a href="https://www.youtube.com/watch?v=Y1XAP6omGzo">Entendiendo las Curvas ROC</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/generated/sklearn.tree.plot_tree.html">Método plot_tree</a></li>
        <li><a href="https://strftime.org/">Tabela de códigos para converter strings em datas no Python</a></li>
        <li><a href="http://gskinner.com/RegExr/">Testador de expressões regulares</a></li>
        <li><a href="https://numpy.org/doc/stable/reference/arrays.datetime.html">Numpy : Timedelta</a></li>
        <li><a href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html">Pandas : Time/Date</a></li>
        <li><a href="https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html#sphx-glr-auto-examples-model-selection-plot-precision-recall-py">Curva de Precision/Recall</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a></li>
        <li><a href="https://pypi.org/project/feather-format/">feather-format</a></li>
    </ul>
</p>
