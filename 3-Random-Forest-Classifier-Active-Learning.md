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

<h1 align='center'>2o Modelo Machine Learning - RandomForestClassifier</h1>

<p>Nesta etapa o objetivo é aprendermos algumas técnicas para obter um modelo machine learning melhor que o anterior.</p>
<p>Para alcançar este objetivo vamos aprender a utilizar o algoritmo RandomForestClassifier, aprender os algoritmos TfidfVectorizer da sklearn.feature_extraction.text e scipy.sparse e também aprenderemos como aplicar a técnica Active Learning.</p>

<hr>
<h3>COM NOTEBOOK <a href="/1-source-code/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb</a></h3>
<p>Utilizaremos o arquivo <a href="/2-dataset">raw_data_with_labels.csv</a> e faremos conforme documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a> até a criação das features.</p>

<h4>MODELO MACHINE LEARNING</h4>
<p>Após criamos as features, vamos separar o dataset de treino e dataset teste por data de publicação/upload, por ser uma time series.</p>
<p>Vamos transformar as strings dos títulos dos vídeos dos datasets treino e dataset teste em uma representação numérica significativa criando uma matriz esparsa (*1) com o algoritmo Term-frequency TfidfVectorizer (*2), para reduzir de forma inteligente a quantidade de elementos a consultar. As figuras a seguir nos mostram que reduziremos de 44004 elementos para 1277 elementos :<br>
Linha 24 do notebook<br>
<img src="/3-images/2rand_fores_tfid0.png"><br>
Linha 25 do notebook<br>
<img src="/3-images/2rand_fores_tfid1.png"></p>
<p>Outra boa e comum prática é concatenaremos dados numéricos com dados string ou concatenarmos matriz densa com matriz esparsa, e para isto utilizaremos a biblioteca scipy.sparse</p>
<p>Após estas técnicas vamos treinar o algorítmo RandomForestClassifier configurando o argumento class_weight="balanced" (mesmo objetivo do explicado no documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>).</p>

<h4>AS MÉTRICAS DE AVALIAÇÃO</h4>
<p>Visualizaremos a métrica <strong>predict_proba</strong> do algorítmo RandomForestClassifier para verificar a distribuição da probabilidade prevista da classe label 1 do dataset. Esta é importante para calcular a pontuação no auc-roc conforme imagem a seguir :<br>
<img src="/3-images/2rand_fores_proba0.png"><br>
<a href="https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html">roc_auc_score - probability estimates which sum to 1</a> </p>
<p>A métrica <strong>average precision</strong> da biblioteca sklearn.metrics conforme imagem a seguir informa que o algorítmo teve um percentual de 19,49% de exemplos positivos, que representa vídeos cujo labelling é 1 (*3).<br>
<img src="/3-images/2rand_fores_aver_prec.png"></p>
<p>A métrica <strong>auc-roc</strong> da biblioteca sklearn.metrics conforme imagem a seguir informa que o algorítmo teve uma probabilidade percentual de 59,58% de selecionar os exemplos positivos, que representa vídeos cujo labelling é 1 (*3).<br>
<img src="/3-images/2rand_fores_auc_roc.png"></p>
<p>Esta serve para melhor visualizarmos o ranking dos vídeos : dos mais interessantes para os menos interessantes.</p>
<p>Importante :<br>
O objetivo em ambos métricas average precision e auc-roc é alcançar 1.0 ou o valor mais próximo possível, sendo esta a nossa baseline técnica em machine learning.</p>
<p>Aqui vamos perceber que houve uma pequena melhora nas métricas com o mesmo tuning aplicado no algorítmo DecisionTreeClassifier e RandomForestClassifier. Vamos aplicar a técnica active learning para melhorar mais as métricas.</p>

<h4>ACTIVE LEARNING</h4>
<p>Dependendo do projeto, fazer anotações pode aumentar desnecessariamente o investimento financeiro e/ou tempo para finalizá-lo, e realizar anotações aleatórias sem um conhecimento qualificado pode prejudicar o modelo preditivo de machine learning. Por exemplo :<br>
Imagens radiográficas, ressonância magnética e similares precisam de especialistas médicos para fazer anotações de tumor maligno, tumor benigno, não tumor. Estes especialistas são caros e o active learning ajuda a reduzir investimentos na coleta das anotações com estes profissionais.</p>
<p>A técnica Active Learning de forma rápida vai nos ajudar a :
    <ol>
        <li>selecionar e disponibilizar os dados mais difíceis do modelo machine learning predizer</li>
        <li>selecionar os melhores exemplos-dados em datasets para fazermos as anotações</li>
        <li>agilizar na coleta das anotações em projetos com prazo curto para fazer anotações</li>
        <li>facilitar a coleta das anotações de profissionais especialistas como médicos, biólogos, astronomos, entre outros</li>
        <li>desenvolver modelos machine learning mais performáticos</li>
        <li>evitar altos custos em qualquer projeto</li>
        <li>economizar investimentos financeiros em qualquer projeto</li>
        <li>agilizar no desenvolvimento de testes em modelos preditivos machine learning</li>
    </ol>
</p>
<p>Vamos pegar o dataset original <a href="/2-dataset">raw_data_with_labels.csv</a>, executar o processo de separação de dados, limpeza de dados, transformação de dados, que são 99% iguais aos que aprendemos nos notebooks <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-dataset-collect-clean.md">1-dataset-collect-clean.md</a> e <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>, vamos trazer apenas os registros cuja coluna Y seja nula, aplicaremos o algorítmo predict_proba do algorítmo RandomForestClassifier sob os títulos de vídeos e gravaremos o resultado no dataset, em um novo campo p (probabilidade). Então selecionaremos os vídeos mais próximos da fronteira dos 50% positivo e 50% negativo (verdadeiro ou falso), por que são os mais prováveis de acertar mesmo sendo difíceis do modelo predizer.</p>
<p>Atenção :<br>
Dependendo da quantidade de dados no dataset, será necessário considerar dados mais distantes da fronteira 50-50.<br>
Outro detalhe é que amostras muito distantes da fronteira, provavelmente são vídeos que realmente não assistiremos.</p>
<p>Neste processo nós programaremos um intervalo fixo para pegar entre 70 e 75 registros e deixaremos aleatório entre 30 e 25 registros, desconsiderando os já selecionados, é claro.</p>
<p>Por fim, geraremos o arquivo active_labels.csv com estes aproximadamente 100 registros a mais, para fazermos as anotações e melhorar nosso modelo machine learning.</p>
<p><strong>Dicas :</strong><br>
    <ul>
        <li>Utilizar a função scipy sparse que é muito mais performática do que a função numpy sparse.</li>
        <li>É comum concaternar matriz esparsa com matriz densa</li>
        <li>Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa.</li>
        <li>Número : O local do ponto na numeração em português é diferente do em inglês.</li>
        <li>Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning.</li>
        <li>Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo.</li>
        <li>Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.</li>
        <li>Features x Banco de dados : Em um projeto real se houver muitas features, uma boa atitude é salvar em banco de dados.</li>
    </ul>
</p>
<p><strong>Nota :</strong><br>
(*1) Matriz esparsa é aquela que armazena valores diferentes de zero e isto significa matriz mais otimizada.<br>
(*2) TfidfVectorizer reduz o impacto de tokens que ocorrem com muita frequência dando mais peso as palavras que aparecem com menor frequência por linha de vídeo, considerando todas as linhas do dataset e vai ignorar as palavras que repetem em todas as linhas de vídeos, dentro do dataset.<br>
Utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo DecisionTreeClassifier, analisar sua probabilidade de acerto de predição e sua precisão curva ROC.<br>
Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor.<br>
O argumento min_df do algoritmo TfidfVectorizer :<br>
-> min_df=2 : o algorítmo vai considerar significante as palavras que aparecerem o mínimo possível por linha dentro do conjunto de linhas dentro do dataset.<br>
-> min_df=1 : o algorítmo vai considerar significante cada palavra diferente encontrada, por linha dentro do conjunto de linhas dentro do dataset. Uma palavra considerada única em uma linha, pode estar na linha seguinte e será considerada incorretamente como difrentes, então dependendo do projeto esta configuração pode prejudicar.<br>
(*3) Labelling 0 -Vídeo que provavelmente não vamos assistir; Labelling 1 -Vídeos que provavelmente vamos assistir

<br>
<br>
<br>
<hr>
<p>Fontes de estudo :
    <ul>
        <li>Curso <a href="https://curso.mariofilho.com/">   
        Solução Completa de Data Science</a> - Instrutor Mario Filho-Kagle Gran Master</li>
        <li><a href="https://towardsdatascience.com/my-random-forest-classifier-cheat-sheet-in-python-fedb84f8cf4f">predict_proba</a></li>
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
