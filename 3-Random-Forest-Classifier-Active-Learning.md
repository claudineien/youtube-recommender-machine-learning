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
<p>Primeiramente abrir o notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb.</a>
</p>

<p>Este modelo é igual ao <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>, do processo Labelling à criação das features.<br>
</p>
<p><strong>Prática ideal do Data Scientist :</strong><br>
Utilizar o mesmo dataset durante os testes de escolha dos modelos machine learning nos ajuda detectar o modelo ideal.
</p>

<hr>
<h3>MODELO MACHINE LEARNING</h3>
O objetivo neste processo é aplicar o algorítimo RandomForestClassifier para predizer quais vídeos provavelmente assistiremos.<br>
Mas antes, vamos aplicar a técnica Active Learning que vai nos ajudar a :
<ol>
    <li>selecionar os melhores exemplos-dados em datasets para fazermos anotações</li>
    <li>agilizar na coleta das anotações em projetos com prazo curto para fazer anotações</li>
    <li>facilitar a coleta das anotações de profissionais especialistas como médicos, biólogos, astronomos, entre outros</li>
    <li>desenvolver modelos machine learning mais performáticos</li>
    <li>evitar altos custos em qualquer projeto</li>
    <li>economizar investimentos financeiros em qualquer projeto</li>
    <li>agilizar no desenvolvimento de testes em modelos preditivos machine learning</li>
</ol>
</p>

<p>Dependendo do projeto, fazer anotações pode aumentar muito o seu custo e/ou tempo para finalizar o projeto, e realizar anotações aleatórias sem um conhecimento qualificado pode prejudicar o modelo preditivo de machine learning. Por exemplo :<br>
Imagens radiográficas, ressonância magnética e similares precisam de especialistas médicos para fazer anotações de tumor maligno, tumor benigno, não tumor. Estes especialistas são caros e o active learning ajuda a reduzir custos na coleta das anotações com estes profissionais.
</p>

<p>Para realizar a técnica active learning primeiramente aplicaremos as técnicas :<br>
    <ul>
        <li>Term-frequency :
        Utilizaremos o algorítmo TfidfVectorizer (1*) para transformar strings em uma representação numérica significativa criando uma matriz esparsa (2*).<br>
        </li>
        <li>Concatenaremos variáveis com dados numéricos a variáveis com dados string.</li>
        <li>Concatenaremos matriz densa a uma matriz esparsa</li>
    </ul>
</p>

<p><strong>Atenção :</strong><br>
No notebook <a href="/file-ipynb/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb</a> criaremos uma linha com resultados average precision e auc-roc, referente a alguns experimentos alterando o argumento mindf do TfidfVectorizer (*1) que serão utilizados pelo algorítimo RandomForestClassifier. Desta forma vamos entender como esta o nosso modelo em relação a <em>baseline</em> gerada no notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>.
</p>

<hr>
<h3>ACTIVE LEARNING</h3>
<p>
A técnica active learning de forma rápida nos ajudará a selecionar e disponibilizar os dados muito difíceis do modelo machine learning predizer, ou seja, se o vídeo é o que vamos assistir ou não.<br>
Depois vamos fazer as anotações necessárias manualmente e unir estes dados ao dataset <a href=".\file-csv">raw_data_with_labels.csv</a> (criado no inicio de nosso trabalho).<br>
Também vamos aprender a verificar se o active learning esta produzindo bons resultados.<br>
</p>

<p>
Através do notebook <a href="/file-ipynb/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb</a> vamos :<br>
<p>
    <ol>
        <li>abrir o arquivo <a href=".\file-csv">raw_data_with_labels.csv</a> utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li></li>
        <li>selecionar os dados cujo Y é nulo e por linha haja pelo menos uma coluna preenchida com um dado válido.</li>
        <li>armazenar os dados do dataset em um dataframe utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>gravar o dataset em outro dataframe para termos mais liberdade nas alterações</li>
        <li>extrair os titulos dos vídeos</li>
        <li>extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>extrair apenas o número de uma coluna tipo objeto, com strings e número</li>
        <li>criar Features - Tratamentos específicos nos dados</li>
        <li>aplicar o TfidfVectorizer (*1), treinado anteriormente, sobre os títulos dos vídeos difíceis de serem preditos</li>
        <li>concatenar conteúdo denso com conteúdo esparso utilizando a função hstack</li>
    </ol>
</p>

<p>
Neste momento temos um dataframe cujo dataset contém o total de views e o total de views por dia somente dos títulos que o modelo esta com dificuldade em predizer.
</p>

<p>
Perceba que a predição foi realizada pelo algorítmo TfidfVectorizer (*1), treinado neste mesmo notebook sob os títulos de vídeos que provavelmente vamos assistir. Criamos o campo p (probabilidade) e este será preenchido com a predição deste algorítmo.
</p>

<p>
Uma boa prática para selecionarmos os exemplos difíceis do modelo predizer, é pegar os vídeos mais próximos da fronteira dos 50% positivo e 50% negativo (verdadeiro ou falso).<br>
Mas muita atenção ! Dependendo da quantidade de dados no dataset, será necessário considerar dados mais distantes da fronteira 50-50.<br>
Outro detalhe é que amostras muito distantes da fronteira, provavelmente são vídeos que realmente não assistiremos.
</p>

<p>
Neste processo nós programaremos um intervalo fixo para pegar entre 70 e 75 registros e deixaremos aleatório entre 30 e 35 registros, desconsiderando os já selecionados, é claro.
</p>

<p>
Por fim, será gerado o arquivo active_labels.csv disponibilizado <a href=".\file-csv">aqui</a>. Neste devemos aplicar o labelling na coluna Y -Youtube.
</p>


<p><strong>Atenção : </strong><br>
O processo de separação de dados, limpeza de dados, transformação de dados são ações, instruções, scripts 99% iguais aos que aprendemos nos notebooks <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-dataset-collect-clean.md">1-dataset-collect-clean.md</a> e <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>
</p>

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
(*1) TfidfVectorizer reduzirá o impacto de tokens que ocorrem com muita frequência dando mais peso as palavras que aparecem com menor frequência por linha de vídeo, considerando todas as linhas do dataset e vai ignorar as palavras que repetem em todas as linhas de vídeos, dentro do dataset.<br>
Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor.<br><br>
O argumento min_df do algoritmo TfidfVectorizer :<br>
-> min_df=2 : o algorítmo vai considerar significante as palavras que aparecerem o mínimo possível por linha dentro do conjunto de linhas dentro do dataset.<br>
-> min_df=1 : o algorítmo vai considerar significante cada palavra diferente encontrada, por linha dentro do conjunto de linhas dentro do dataset. Uma palavra considerada única em uma linha, pode estar na linha seguinte e será considerada incorretamente como difrentes, então dependendo do projeto esta configuração pode prejudicar.<br><br>
(*2) Matriz esparsa armazena valores diferentes de zero e isto significa matriz mais otimizada.<br></p>

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
