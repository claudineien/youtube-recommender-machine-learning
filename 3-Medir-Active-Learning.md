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
<p>É importante sabermos qual resultado o Active Learning esta trazendo ao nosso projeto. Isto nos ajuda a acompanhar melhor e mais rápido sobre a qualidade dos dados, se há necessidade de termos mais dados para trabalhar, identificar a performance dos modelos em teste e talvez aplicar alguma mudança em um ou mais processos do desenvolvimento do modelo machine learning.<br>
</p>

<p>
Nós temos poucos dados sob treino e teste e isto faz o average precision e o auc-roc variar muito rapidamente a cada pequena alteração. Este também é um motivo de medirmos o resultado do active learning e faremos aplicando as seguintes técnicas :<br>
<ol>
    <li>aumentando apenas os dados de validação</li>
    <li>aumentando apenas os dados de treino</li>
    <li>aumentando os dados de validação e de treino</li>
</ol>
Depois será importante executar as métricas roc_auc_score e average_precision_score.
</p>

<h3>PROCESSO : APLICANDO A MÉTRICA</h3>
<p>Nesta etapa vamos aplicar o labelling, criar mais exemplos para treino e teste, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo RandomForestClassifier, analisar sua probabilidade de acerto de predição e sua precisão curva <a href="blank_">ROC</a> e comparar com a nossa <em>baseline</em>, gerada no notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-Decision-Tree-Classifier.md">1-Decision-Tree-Classifier.md</a>
</p>

<h3>PROCESSO : LABELLING</h3>
<p>
    <ol>
        <li>Abrir o arquivo <a href=".\file-csv">active_labels.csv</a> em uma planilha eletrônica como ms excel, <a href="https://gsuite.google.com/intl/pt-BR/products/sheets/">google sheets</a> ou <a href="https://pt-br.libreoffice.org/descubra/calc/"> LibreOffice</a> através da opção de importar um arquivo .csv</li>
        <li>Criar a coluna Y (*1)</li>
        <li>Inserir na coluna Y o número 0 nas linhas cujo título do vídeo, provavelmente, não vamos assistir ou inserir 1 nas linhas cujo vídeo provavelmente, vamos assistir.</li><br>
        <p><strong>Importante:</strong><br>
        Baixar o arquivo <a href=".\file-csv">active_labels.csv</a>, cujo o labelling foi aplicado para agilizar e facilitar nosso entendimento em cada técnica executada.</p>
    </ol>
</p>

<p>
Com o notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/3_Medir_Active_Learning.ipynb" >3_Medir_Active_Learning.ipynb</a> :
<p>
Vamos pegar os dados do dataset <a href="\file-csv">raw_data_with_labels.csv</a>, com aproximadamente 1182 registros com 498 anotações (labelling) no campo Y, no qual 1 para vídeos que gosto ou 0 para vídeos que não gosto.<br>
</p>

<p>
Vamos pegar o <a href="\file-csv" >active_labels.csv</a>, com aproximadamente 100 exemplos gerados pelo notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2_Random_Forest_Classifier.ipynb">2_Random_Forest_Classifier.ipynb</a>. Este arquivo contém a coluna p com a probabilidade gerado pelo algorítmo RandomForestClassifier no notebook mencionado a pouco e adicionada pela técnica Active Learning.
</p>

<p>
Agora receberá através do notebook <a href="3_Medir_Active_Learning.ipynb" >3_Medir_Active_Learning.ipynb</a> coluna Novo preenchida com 1 para indicar que são os 100 exemplos que o algoritmo esta com dificuldade em classificar.
</p>

<p>Se aplicarmos as métricas roc_auc_score e average_precision_score sob a probabilidade gerado pelo modelo RandomForestClassifier x labelling gravados no arquivo <a href="\file-csv" >active_labels.csv</a> gerado pelo notebook <a href=".\file-csv">2_Random_Forest_Classifier.ipynb</a> sob as técnicas Active Learning, tentamos responder as seguintes perguntas :<br>
01 Quais são as métricas ?<br>
02 Qual é o erro ?<br>
03 Qual o average_precision_score ?<br>
04 Qual é o roc_auc_score ? <br>
Bom... por ser a primeira vez que aplicamos este procedimento não teremos parâmetro para avaliar, mas é possível comparar com o resultado do modelo anterior e entender se esta perto ou longe do objetivo de ter um bom modelo machine learning
</p>

<p>Ao aplicar average_precision_score e roc_auc_score no dataset  <a href="\file-csv" >active_labels.csv</a> no notebook <a href="3_Medir_Active_Learning.ipynb" >3_Medir_Active_Learning.ipynb</a> antes de iniciarmos a limpeza dos dados, comparando com o dataset criado pelo modelo RandomForestClassifier gerado no notebook  <a href=".\file-csv">2_Random_Forest_Classifier.ipynb</a> percebemos que a alteração é mínima em ambos. Atenção ao AUC que esta sensível por que estamos trabalhando com uma quantidade muito pequena de dados.
</p>

<p>Uma técnica que ajudará a medir do Active Learning é :</p>
<p>Criar um novo dataframe no notebook <a href=".\file-csv">3_Medir_Active_Learning.ipynb</a>.<br>
Este dataframe vai unir o dataset <a href=".\file-csv">active_labels.csv</a> contendo 100 exemplos mais uma nova coluna [Novo] igual a 1 ao dataframe original <a href=".\file-csv">raw_data_with_labels.csv</a>.<br>
Após esta união de datasets atualizaremos para 0 os dados da coluna [Novo] que são diferentes dos 100 exemplos que estão com 1 (*1)<br>
Eliminar a coluna p relacionada a probabilidade de acerto dos vídeos, por que não será usada nos próximos textes.<br>
</p>
<p>A seguir passos a executar :</p>

<h3>ABRIR .CSV, LIMPAR E TRANSFORMAR DADOS</h3>
<p>
    <ul>
        <li>Abrir o arquivo <a href="\file-csv">raw_data_with_labels.csv</a></li>
        <li>Abrir o arquivo <a href="\file-csv" >active_labels.csv</a></li>
        <li>Em ambos os arquivos pegar somente as linhas cuja coluna Y é diferente de nula</li>
        <li>Aplicar o algoritmo fillna() para eliminar o conteúdo nan (*2)
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
</p>

<p><strong>Atenção :</strong><br>
    <a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a>
</p>

<p><strong>Nota :</strong><br>
(*1) Conteúdo na coluna Novo :<br>
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
