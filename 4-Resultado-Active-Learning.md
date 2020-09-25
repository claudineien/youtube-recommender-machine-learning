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

<h1 align='center'>Resultado com Active Learning</h1>
<p>O objetivo nesta fase é entender aonde o Active Learning vai trazer ou não melhorias ao nosso modelo machine learning. Nesta etapa identificaremos se houve melhoria ou não através das métricas average precision e auc-roc. Esta análise também nos ajudará a acompanhar mais rápidamente a qualidade do dataset, entender se há necessidade de termos mais dados para treinar e testar e aplicar uma ou mais mudanças em um ou mais processos do desenvolvimento deste projeto de ciência de dados.</p>
<p>Utilizaremos o notebook <a href="/1-source-code/4_Resultado_Active_Learning.ipynb" >4_Resultado_Active_Learning.ipynb</a> para entendermos um pouco de como este processo funciona.</p>
<p>Nesta etapa vamos aplicar a técnica Labelling, aplicaremos limpezas no dataset, criaremos algumas Features, trabalharemos com matriz esparsas, term frequency, faremos tuning no algorítmo machine learning, treinaremos o algorítmo RandomForestClassifier e por fim teremos o resultados das métricas.</p>

<hr>
<h3>PROCEDIMENTOS QUE APLICAREMOS NO DATASET</h3>
<h4>LABELLING</h4>
No final do notebook <a href="/1-source-code/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb</a> nós aplicamos a técnica active learning e criamos o arquivo <a href="/2-dataset">active_labels.csv</a> para fazermos o labelling.</p>
<p>Vamos fazer o labelling conforme documentado em <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>.</p>
<p>Importante :<br>
Baixar o arquivo <a href="/2-dataset">active_labels.csv</a>, cujo labelling já foi aplicado para facilitar nosso entendimento em cada técnica executada.</p>

<hr>
<h4>COM NOTEBOOK <a href="/1-source-code/4_Resultado_Active_Learning.ipynb" >4_Resultado_Active_Learning.ipynb</a></h4>
<h4>A PRIMEIRA MÉTRICA</h4>
<p>Ao aplicarmos as métricas average precision e auc-roc sobre o arquivo <a href="/2-dataset">active_labels.csv</a> considerando
as colunas y (labelling) e p (probabilidade) com o percentual de probabilidade de ser 1 (Video que provavelmente vamos assistir), vamos obter o seguinte resultado :<br>
<img src="/3-images/3rand_for_activ_learn.png"><br>
<p>Esta primeira métrica realizada sobre o dataset com 100 exemplos que o modelo machine learning esta com dificuldade em classificar, indica que :<br>
- As métricas average_precision_score e roc_auc_score estão sensíveis com relação a pequena quantidade de dados que temos.<br>
- O dataset provavelmente deve receber mais tratamento e/ou mais dados para melhorarmos o modelo machine learning.<br>
- O modelo parece estar melhorando com o Active Learning</p>
<p>Analisando um pouco do dataframe do arquivo <a href="/2-dataset" >active_labels.csv</a>, identificamos que a coluna p contém a probabilidade que o modelo machine learning dá ao item 579 de ser 37,5% positivo e ao item 846 de ser 82,6% positivo.<br>
Se usarmos um ponto de corte de 50%, sendo acima positivo e abaixo negativo, significa que o item :<br>
- 579 seria um Falso Negativo (37,5% < 50%)<br>
- 846 seria um Falso Positivo (82,6% > 50%)</p>

<hr>
<h3>ANALISAR RESULTADO DO ACTIVE LEARNING</h3>
<p>Neste etapa nós aprenderemos como aplicar algumas técnicas para entendermos aonde o active learning nos esta ajudando.</p>
<p>Inciaremos pela limpeza e tratamento nos dados e logo em seguida aplicaremos três técnicas : aumentar dataset de validação, aumentar dataset de treino e aumentar dataset de validação e o dataset de treino.</p>

<h4>LIMPAR E TRANSFORMAR DADOS</h4>
<p>
    <ul>
        <li>Vamos incluir a coluna [Novo] no dataframe com os 100 exemplos separados pelo active learning e incluir o número 1 nesta coluna.</li>
        <li>Vamos importar aproximadamente 498 registros do dataset <a href="\file-csv">raw_data_with_labels.csv</a>, cujo o campo y seja diferente de nulo/vazio, que estão com anotações 1 ou 0.</li>
        <li>Vamos concatenar os arquivos <a href="/2-dataset">active_labels.csv</a> com 100 exemplos e com a nova coluna [Novo] ao <a href="/2-dataset">raw_data_with_labels.csv</a> com aproximadamento 500 exemplos. Ambos com labelling realizado. E teremos com um dataset com 600 registros, para melhorar o treinamento de nosso modelo machine learning.</li>
        <li>O novo dataset terá a coluna [Novo] com 1 indicando os 100 registros e gravará nan's para os outros 500 registros.</li>
        <li>Vamos eliminar a coluna p, por que será desnecessária aos testes.</li>
        <li>Vamos substituir o conteúdo nan por 0 na coluna [Novo] referente aos 500 registros que estão com nan's.</li>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas.</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número.</li>
        <li>Criar Features necessárias.</li>
    </ul>
</p>

<h4>AUMENTAR DATASET DE VALIDAÇÃO</h4>
<p>Aumentar o dataset de validação é a técnica menos utilizada, mas a utilizaremos por que temos poucos dados e esta técnica é mais uma opção para analisarmos melhor a probabilidade, average precision e o auc roc.</p>
<p>Nos dados de treino selecionaremos os primeiros 50% dos dados dos 500 exemplos antigos e nos dados de validação selecionaremos os outros 50% dos dados antigos mais os 100 exemplos dos dados separados pelo active learning.</p>
<p>A seguir estão os valores average precision e auc-roc sob a probabilidade relacionada aos títulos :</p>
<img src="/3-images/3rand_for_activ_learn1.png">
<p>Comparando com as métricas do algorítmo DecicionTreeClassifier nós tivemos uma melhoria nas métricas.</p>

<h4>AUMENTAR DATASET DE TREINO</h4>
<p>Esta técnica é a mais comumente utilizada.</p>
<p>Nos dados de treino selecionaremos os primeiros 50% dos dados dos 500 exemplos antigos mais os 100 exemplos dos dados separados pelo active learning e nos dados de validação selecionaremos a outra parte dos 50% dos dados antigos.</p>
<p>A seguir estão os valores average precision e auc-roc sob a probabilidade relacionada aos títulos :</p>
<img src="/3-images/3rand_for_activ_learn2.png">
<p>Comparando com as métricas do algorítmo DecicionTreeClassifier nós continuamos com melhoria nas métricas, porém menor que o anterior.</p>

<h4>AUMENTAR DATASET DE VALIDAÇÃO E O DATASET DE TREINO</h4>
Nos dados de treino selecionaremos os primeiros 50% dos dados dos 500 exemplos antigos mais os 100 exemplos dos dados separados pelo active learning e nos dados de validação selecionaremos a outra parte dos 50% dos dados antigos</p>
<img src="/3-images/3rand_for_activ_learn3.png">
<p>Comparando com as métricas do algorítmo DecicionTreeClassifier nós continuamos com melhoria nas métricas.</p>
<p>Algumas informações importantes a saber :<br>
1 Em todas as técnicas aplicaremos o algorítmo TfidfVectorizer o scipy.sparse, executaremos o algorítmo RandomForestClassifier, seu algorítmo de probabilidade, o average precision e auc-roc da biblioteca sklearn.metrics.<br>
2 As métricas estão muito sensíveis, alterando a cada pequena alteração.<br>
3 Na maior parte das vezes quanto mais conteúdo no dataset, melhor será modelo machine learning.</p>

<p>A precisão da pontuação entre a probabilidade dos dados de treino e dados de validação infelizmente diminuiu mas o AUC melhorou -esta mais próximo de 1. Entendemos que ambos estão bem sensíveis, por conta da pouca quantidade de dados.</p>

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Novo dataframe : Evite alterar os dados no dataframe principal, trabalhe sempre com a cópia. Esta prática agiliza o processo de manipulação dos dados e se algo der errado basta executar a instção de cópia do dataframe novamente, alem de evitar que alguma rotina que utiliza o dataframe principal funcione indevidamente.</p>

<p>Issue github :<br>
    <a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a>
</p>

<br>
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
        <li><a href="https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html">TfidfVectorizer - Term Frequency</a></li>
        <li><a href="https://medium.com/@cmukesh8688/tf-idf-vectorizer-scikit-learn-dbc0244a911a">TF-IDF Vectorizer scikit-learn</a></li>
        <li><a href="https://docs.scipy.org/doc/scipy/reference/generated/scipy.sparse.csc_matrix.html">sparse matrix</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction">Bag of Words (e TF-IDF)</a></li>
        <li><a href="https://docs.scipy.org/doc/scipy/reference/sparse.html">Sparse matrices</a></li>
        <li><a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a></li>
    </ul>
</p>

<!--Mensagens aos familiares e amigos pelo whatsapp
Muita paz à vocês meus amores.
Muita felicidade amores.
Muita sabedoria a cada um de vocês família amores.
Que você sempre tenha forças para lutar contra o pode destruir você e a quem você quer bem.
Desejo que tenham saúde mental e física para você compartilhar todas as boas ações e intenções com as pessoas que você quer bem
Desejo que a paciência aumenta em vossa vida e na vida de todas as pessoas que convivem com você para que construam uma relação de confiança.
Desejo que você alcance a vitória que lhe fará feliz, e que esta vitória seja a vitória também façam as pessoas que você gosta ser felizes e una a todos vocês para sempre.
. Bom dia.
-->
