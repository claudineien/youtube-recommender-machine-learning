<h4><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a></h4>
<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
</h4>

<h1 align='center'>Medir Impacto do Active Learning</h1>
<p>Por termos poucos dados de validação e o auc estar muito instável é importante saber se o Active Learning esta trazendo bom efeito ao projeto. Podemos medir o impacto aplicando as seguintes técnicas :<br>
<ol>
    <li>aumentando apenas os dados de validação</li>
    <li>aumentando apenas os dados de treino</li>
    <li>aumentando os dados de validação e de treino</li>
</ol>
Depois será importante executar as métricas roc_auc_score e average_precision_score.
</p>

<p>
O arquivo <a href="\file-csv">raw_data_with_labels.csv</a> tem aproximadamente 500 anotações e estão com labelling 1-Vídeos Que Gosto, 0-Vídeos Que Não Gosto no campo Y.<br>
O arquivo <a href="\file-csv" >active_labels.csv</a> contém 100 exemplos gerados pelo notebook <a href=".\file-csv">2_Random_Forest_Classifier.ipynb</a>, e através do excel foram feitas os labelling na coluna y : 1-Vídeos Que Gosto, 0-Vídeos Que Não Gosto. Este arquivo .csv também contém a coluna p com a probabilidade gerado pelo algorítmo RandomForestClassifier do mesmo notebook adicionada pela técnica Active Learning. Agora receberá através do notebook <a href="3_Medir_Active_Learning.ipynb" >3_Medir_Active_Learning.ipynb</a> coluna Novo preenchida com 1 para indicar que são os 100 exemplos que o algoritmo esta com dificuldade em classificar.
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
