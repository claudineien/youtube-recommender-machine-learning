<h5><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a></h5>

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

<h1 align='center'>Medir Resultado do Active Learning</h1>
<p>É importante sabermos qual resultado o Active Learning esta trazendo ao nosso projeto. Isto nos ajuda a acompanhar melhor e mais rápido a qualidade dos dados, entender se há necessidade de termos mais dados para trabalhar, identificar a performance dos modelos em teste e talvez aplicar alguma mudança em um ou mais processos do desenvolvimento do modelo machine learning.<br>
</p>

<p>
Nós temos poucos dados sob treino e teste e isto faz o average precision e o auc-roc variar com facilidade a cada pequena alteração. Este também é um motivo de medirmos o resultado do active learning e faremos aplicando as seguintes técnicas :<br>
    <ol>
        <li>aumentando apenas os dados de validação</li>
        <li>aumentando apenas os dados de treino</li>
        <li>aumentando os dados de validação e de treino</li>
    </ol>
</p>

<hr>
<h3>RESUMINDO</h3>
<p>
Nesta etapa vamos aplicar o labelling, criar mais exemplos para treino e teste, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo RandomForestClassifier, analisar sua probabilidade, executar as métricas roc_auc_score e average_precision_score, comparar com a <em>baseline</em> obtida no notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1_Decision_Tree_Classifier.ipynb">1_Decision_Tree_Classifier.ipynb</a> e comparar com os resultados gerados no notebook  <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2_Random_Forest_Classifier.ipynb">2_Random_Forest_Classifier.ipynb</a>.
</p>

<hr>
<h3>PROCESSO : LABELLING</h3>
<p>
    <ol>
        <li>Abrir o arquivo <a href=".\file-csv">active_labels.csv</a> através da opção de importar um arquivo .csv, em um dos seguintes programas como : planilha eletrônica ms excel, <a href="https://gsuite.google.com/intl/pt-BR/products/sheets/">google sheets</a> ou <a href="https://pt-br.libreoffice.org/descubra/calc/"> LibreOffice</a> </li>
        <li>Criar a coluna Y (*1)</li>
        <li>Inserir na coluna Y o número 0 nas linhas cujo título do vídeo, provavelmente, não vamos assistir ou inserir 1 nas linhas cujo vídeo provavelmente, vamos assistir.</li><br>
        <p><strong>Importante:</strong><br>
        Baixar o arquivo <a href=".\file-csv">active_labels.csv</a>, cujo o labelling foi aplicado para agilizar e facilitar nosso entendimento em cada técnica executada.</p>
    </ol>
</p>

<hr>
<h3>PROCESSO : ANALISE BÁSICA DAS MÉTRICAS</h3>
<p>
Antes de iniciar o trabalho da métrica do active learning,  vamos, sem entrar e pormenores, com o notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/3_Medir_Active_Learning.ipynb" >3_Medir_Active_Learning.ipynb</a>, importar o <a href="\file-csv" >active_labels.csv</a>, com aproximadamente 100 exemplos gerados pelo notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2_Random_Forest_Classifier.ipynb">2_Random_Forest_Classifier.ipynb</a> e aplicaremos as métricas average_precision_score e roc_auc_score, considerando as colunas y (labelling) e p (probabilidade), esta última adicionada pela técnica Active Learning.<br>
Com esta ação tentaremos responder as seguintes perguntas :<br>
01 Quais são as métricas ?<br>
02 Qual é o erro ?<br>
03 Qual o average_precision_score ?<br>
04 Qual é o roc_auc_score ?<br>
05 O modelo esta melhorando ?
06 Quais ações executar para melhorar o modelo ?
</p>

<p>
Não temos parâmetros para comparar os valores de métricas referente para os 100 exemplos gerados pelo notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2_Random_Forest_Classifier.ipynb">2_Random_Forest_Classifier.ipynb</a>, mas podemos concluir que :<br>
- As métricas apontam uma grande sensibilidade nos resultados average_precision_score e roc_auc_score.<br>
- Com estes valores entendemos que falta alguns ajustes para termos um bom modelo machine learning.<br>
- Analisando o dataframe do arquivo <a href="\file-csv" >active_labels.csv</a> identificamos que a coluna p contém a probabilidade que o modelo machine learning dá ao item 579 de ser 37,5% positivo e ao item 846 de ser 82,6% positivo.<br>
Se usarmos um ponto de corte de 50%, sendo acima positivo e abaixo negativo, então o item ...<br>
- 579 seria um Falso Negativo (37,5% < 50%)<br>
- 846 seria um Falso Positivo (82,6% > 50%)
</p>

<hr>
<h3>PROCESSO : LIMPAR E TRANSFORMAR DADOS</h3>
<p>
    <ul>
        <li>
        Vamos incluir o número 1 na coluna [Novo] no dataframe com os aproximadamente 100 exemplos. O número 1 indica que são os 100 exemplos que o algoritmo esta com dificuldade em classificar.
        </li>
        <li>
        Vamos importar aproximadamente 498 registros do dataset <a href="\file-csv">raw_data_with_labels.csv</a>, cujo o campo y seja diferente de nulo/vazio, estão com anotações (labelling) 1 para vídeos que gosto ou 0 para vídeos que não gosto.
        </li>
        <li>
        Vamos unir os dois dataframes importados gerando um novo dataframe com aproximadamento 600 registros. Na coluna [Novo] estaram gravados 1 indicando dataset do dataframe que continha 100 registros e gravará nan's para os outros 500 registros.
        </li>
        <li>
        Vamos substituir o conteúdo nan por 0 na coluna [Novo] referente aos 500 registros que estão com nan's (*2).
        </li>
        <li>
        Vamos eliminar a coluna p relacionada a probabilidade de acerto dos vídeos, por que não será usada nos próximos textes.
        </li>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
    </ul>
</p>

<hr>
<h3>AUMENTAR DATASET DE VALIDAÇÃO</h3>
<p>É o procedimento menos utilizado. Esta sendo utilizado por que a quantidade de dados é muito pouca é uma boa técnica para analisarmos melhor a probabilidade, média de precisão e o AUC. É indicado que o dataset de validação não seja alterado. Aqui os dados de validação são novos e os dados de treino antigos.
<br>
    <ul>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*3)</li>
        <li>Concatenar matriz densa e matriz sparsa (*4)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*5)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>

<hr>
<h3>AUMENTAR DATASET DE TREINO</h3>
<p>Este é o procedimento mais tradicional/utilizado. Também utilizada a análise da probabilidade, média de precisão e o AUC. Aqui os dados de validção são antigos e os dados de treino novos.
<br>
    <ul>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*3)</li>
        <li>Concatenar matriz densa e matriz sparsa (*4)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*5)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>

<hr>
<h3>AUMENTAR DATASET DE VALIDAÇÃO E O DATASET DE TREINO</h3>
    <ul>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*3)</li>
        <li>Concatenar matriz densa e matriz sparsa (*4)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*5)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>

<p>A precisão da pontuação entre a probabilidade dos dados de treino e dados de validação infelizmente diminuiu mas o AUC melhorou -esta mais próximo de 1. Entendemos que ambos estão bem sensíveis, por conta da pouca quantidade de dados.
</p>

<p><strong>Aprender mais :</strong><br>
    <a href="https://strftime.org/">Tabela de códigos para converter strings em datas no Python</a><br>
    <a href="http://gskinner.com/RegExr/">Testador de expressões regulares</a><br>
    <a href="https://numpy.org/doc/stable/reference/arrays.datetime.html">Numpy : Timedelta</a><br> 
    <a href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html">Pandas : Time/Date</a><br>
    <a href="https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html#sphx-glr-auto-examples-model-selection-plot-precision-recall-py">Curva de Precision/Recall</a><br>
    <a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a><br>
    <a href="">Dados train and test</a><br>
    <a href="https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction">Bag of Words (e TF-IDF)</a><br>
    <a href="https://docs.scipy.org/doc/scipy/reference/sparse.html">Sparse matrices</a><br>
</p>

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Novo dataframe : Evite alterar os dados no dataframe principal, trabalhe sempre com a cópia. Esta prática agiliza o processo de manipulação dos dados e se algo der errado basta executar a instção de cópia do dataframe novamente, alem de evitar que alguma rotina que utiliza o dataframe principal funcione indevidamente.
</p>

<p><strong>Atenção :</strong><br>
    <a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a>
</p>

<p><strong>Nota :</strong><br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y (Youtube) para facilitar nosso entendimento.<br>

(*2) Conteúdo na coluna Novo :<br>
1-Relacionados aos 100 exemplos do dataset <a href=".\file-csv">active_labels1_done.csv</a><br>
0-Relacionados aos exemplos do dataset <a href=".\file-csv">raw_data_with_labels.csv</a>

(*2) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Conteúdo nan atrapalha a eficiência do modelo machine learning.<br>
(*3) TfidfVectorizer dá mais peso as palavras que aparecem bastante em determinado exemplo mas não aparece tanto no dadtaset como um todo. Palavras que aparecem pouco entre todos os videos mas aparecerem muito em um video tem mais peso. Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor
Há uma forma mais simples que é criar matriz com contagem de palavras em que em cada linha tem um video, e cada coluna é uma palavra e coloca a quantas vezes a palavra aparece no cruzamento da linha do video com a palavra do titulo do vídeo<br>
(*4) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.<br>
(*5) A probabilidade é o percentual de acerto que o modelo machine learning alcançou.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<p>Importante :<br>
Na maior parte das vezes quanto mais conteúdo estiver no dataset, melhor será modelo machine learning.
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
