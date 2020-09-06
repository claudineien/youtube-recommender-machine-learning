<h5><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a>
</h5>
<h5>
<div>
  <table>
    <tr>
      <th>PROJETO</th>
      <th>NÍVEL DE CONHECIMENTO</th>
      <th>TIPO DE DADOS</th>
      <th>TIPO MACHINE LEARNING</th>
    </tr>
    <tr>
      <td>Recomendador de vídeos do youtube</td>
      <td>Iniciante à avançado</td>
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
<p>Este modelo é igual ao <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-Decision-Tree-Classifier.md">1-Decision-Tree-Classifier.md</a>, do processo Labelling à criação das features.<br>
<strong>Importante :</strong><br>
Utilizar o mesmo dataset em todos os modelos machine learning nos ajuda detectar o modelo ideal.
</p>

<hr>
<h3>MODELO MACHINE LEARNING</h3>
Utilizaremos o algorítimo RandomForestClassifier para predizer quais vídeos provavelmente assistiremos.<br>
Mas antes, vamos aplicar a técnica Active Learning que vai nos ajudar a selecionar exemplos em datasets, para fazermos anotações e com estas anotaçãoes vamos :
<ol>
    <li>melhorar o resultado da predição do algorítmo machine learning</li>
    <li>evitar altos custos em projetos pequenos e/ou com limites de investimentos</li>
    <li>economizar investimentos financeiros em qualquer projeto</li>
    <li>economizar investimentos de tempo em qualquer projeto</li>
    <li>agilizar o desenvolvimento de testes em modelos preditivos machine learning</li>
</ol>
Ex : Dados médicos precisam de especialistas para fazer anotações de tumor maligno, tumor benigno, não tumor. Estes especialistas são caros e o active learning ajuda a reduzir custos com estes profissionais.
</p>

<p>Para realizar a técnica active learning primeiramente aplicaremos as técnicas :<br>
    <ul>
        <li>Term-frequency :
        Utilizaremos o algorítmo TfidfVectorizer para transformar strings em uma representação numérica significativa criando uma matriz esparsa (1*).<br>
        O argumento min_df do algoritmo TfidfVectorizer :<br>
        -> min_df=2 : o algorítmo vai considerar significante as palavras que aparecerem o mínimo possível por linha dentro do conjunto de linhas dentro do dataset.<br>
        -> min_df=1 : o algorítmo vai considerar significante cada palavra diferente encontrada, por linha dentro do conjunto de linhas dentro do dataset.<br>
        </li>
        <li>Concatenaremos variáveis com dados numéricos a variáveis com dados string.</li>
        <li>Concatenaremos matriz densa a uma matriz esparsa</li>
    </ul>
</p>

<hr>
<h3>ACTIVE LEARNING</h3>
<p>Active Learning é uma técnica que ajuda a escolher melhor quais dados devem receber anotação em um dataset, para desenvolvermos um modelo com melhor performance.</p>
<p>Normalmente utilizado em pequenos projetos, em projetos com orçamento baixo e/ou em projetos com pouco tempo para fazer anotações em dados que serão treinados.<p>
<p>Dependendo do projeto, fazer anotações pode aumentar muito o seu custo, e realizar anotações aleatórias sem um conhecimento qualificado pode prejudicar o modelo preditivo de machine learning.</p>
<p>Por exemplo:<br>
Em projetos de tratamento de imagem radiográfica, ressonância magnética, e similares, que exige experiência médica especializada para anotar nos datasets uma situação de tumor benigno ou maligno ou nenhum dos dois, o Active Learning nos ajuda a separar com maior qualidade os dados que precisamos que recebam as anotações destes especialistas.
</p>
<p>
Vamos Pegar uma quantidade de exemplos que o modelo esta com problema em classificar, selecionar entre 65% e 70% manualmente e deixar entre 35% e 30% automaticamente aleatório, para identificarmos mais alguns exemplos que o modelo esteja com dificuldade em classificar.<br>
Uma boa prática para selecionarmos os exemplos difíceis do modelo classificar é pegar os exemplos entre 45% e 55% (próximos à fronteira 50%-50%) e identificar os exemplos falsos positivo. Exemplos inferiores a 20% de probabilidade de ser Verdadeiro Positivo provavelmente são irrelevantes a este processo.
</p>

<p><strong>Dicas :</strong><br>
Utilizar a função scipy sparse que é muito mais performática do que a função numpy sparse.<br>
É comum concaternar matriz esparsa com matriz densa<br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto na numeração em português é diferente do em inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.<br>
Features x Banco de dados : Em um projeto real se houver muitas features, uma boa atitude é salvar em banco de dados
</p>

<p><strong>Nota :</strong><br>
(*1) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.<br>
(*2)TfidfVectorizer dá mais peso as palavras que aparecem com menor frequência por linha de vídeo, considerando todas as linhas do dataset e vai ignorar as palavras que repetem em todas as linhas de vídeos, dentro do dataset.<br>
Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor.<br>
(*3) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Conteúdo nan atrapalha a eficiência do modelo machine learning.<br>
(*4) A probabilidade é o percentual de acerto que o modelo machine learning alcançou.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<hr>
<h3>MODELO MACHINE LEARNING</h3>
Neste segundo modelo a predição será realizada sob o título do vídeo, após ser transformado pelo objeto TfidfVectorizer.A predição do modelo machine learning será com o algoritmo RandomForestClassifier.
    <ul>
        <li>Separar dados de treino e dados de teste - Aplicar validação temporal por ser uma time series (*3)</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Separar as descrições dos títulos para treino e teste</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*4)</li>
        <li>Concatenar matriz densa e matriz sparsa (*5)</li>
        <li>Treinar modelo machine learning </li>
        <li>Executar a probabilidade do RandomForestClassifier (*6)</li>
        <li>Aplicar a métrica de média de precisão (*6)</li>
        <li>Tratar o ranking dos vídeos (*7)</li>
        <li>Aplicar a curva <a href="blank_">ROC</a></li>
        <li>Exibir a Decision tree para analisar o modelo</a></li>
    </ul>

<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
    <ul>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (*1)</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*2)</li>
        <li>Concatenar matriz densa e matriz sparsa (*3)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*4)</li>
        <li>Concatenar os dataframes difíceis e aleatórios</li>
        <li>Exibir exemplos difíceis separados de classificar e os aleatórios</li>
    </ul>

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
