<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
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
O arquivo <a href="\file-csv">raw_data_with_labels.csv</a> terá aproximadamente 500 anotações e esta com labelling 1-Vídeos Que Gosto, 0-Vídeos Que Não Gosto no campo Y.<br>
O arquivo <a href="\file-csv" >active_labels1_done.csv</a> contém 100 exemplos com labels gerados pelo notebook <a href=".\file-csv">2_Random_Forest_Classifier.ipynb</a> mais a coluna p com a probabilidade gerado pelo algorítmo RandomForestClassifier no mesmo notebook, adicionada pela técnica Active Learning, e receberá agora a nova coluna Novo com valor 1.
</p>

<p>Se aplicarmos as métricas roc_auc_score e average_precision_score sob a probabilidade gerado pelo modelo RandomForestClassifier x labelling gravados no arquivo <a href="\file-csv" >active_labels1_done.csv</a> gerado pelo notebook <a href=".\file-csv">2_Random_Forest_Classifier.ipynb</a> sob as técnicas Active Learning, então :<br>
01 Quais são as métricas ?<br>
02 Qual é o erro ?<br>
03 Qual o average_precision_score ?<br>
04 Qual é o roc_auc_score ? <br>
Bom... por ser a primeira vez que aplicamos este procedimento não teremos parâmetro para avaliar, mas é possível entender se esta perto ou longe do objetivo de ter um bom modelo machine learning.
</p>

<p>Ao aplicar average_precision_score e roc_auc_score neste ultimo dataset comparando com o dataset criado para o modelo RandomForestClassifier percebemos que a alteração é mínima em ambos, mas uma informação é certa : o auc esta sensível por que estamos trabalhando com uma quantidade muito pequena de dados.
</p>

<hr>
<h3>ABRIR .CSV, LIMPAR E TRANSFORMAR DADOS</h3>
<p>
    <ul>
        <li>Abrir o arquivo <a href="\file-csv">raw_data_with_labels.csv</a></li>
        <li>Abrir o arquivo <a href="\file-csv" >active_labels1_done.csv</a></li>
        <li>Em ambos os arquivos pegar somente linhas cuja coluna Y é diferente de nula</li>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (*1)</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*2)</li>
        <li>Concatenar matriz densa e matriz sparsa (*3)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*4)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>

<p>Uma prática que ajudará a medir do Active Learning é comparar:</p>
<p>Criar um novo dataframe no notebook <a href=".\file-csv">3_Medir_Active_Learning.ipynb</a>.<br>
Este dataframe vai unir o dataset <a href=".\file-csv">active_labels1_done.csv</a> contendo 100 exemplos mais uma nova coluna [Novo] igual a 1 ao dataframe original <a href=".\file-csv">raw_data_with_labels.csv</a>.<br>
Após esta união de datasets atualizaremos para 0 os dados da coluna [Novo] que são diferentes dos 100 exemplos que estão com 1.<br>
Eliminar a coluna p relacionada a probabilidade de acerto dos vídeos.<br>
Legenda :<br>
1-Relacionados aos 100 exemplos do dataset <a href=".\file-csv">active_labels1_done.csv</a><br>
0-Relacionados aos exemplos do dataset <a href=".\file-csv">raw_data_with_labels.csv</a>
</p>

<hr>
<h3>AUMENTAR DATASET DE VALIDAÇÃO</h3>
<p>Esta é a maneira menos tradicional.<br>
    <ul>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*2)</li>
        <li>Concatenar matriz densa e matriz sparsa (*3)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*4)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>

<hr>
<h3>AUMENTAR DATASET DE TREINO</h3>
<p>Esta é a maneira mais tradicional.<br>
    <ul>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*2)</li>
        <li>Concatenar matriz densa e matriz sparsa (*3)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*4)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>

<hr>
<h3>AUMENTAR DATASET DE VALIDAÇÃO E O DATASET DE TREINO</h3>
    <ul>
        <li>Selecionar um intervalo de datas mais amplo</li>
        <li>Importar o objeto TfidfVectorizer</li>
        <li>Pegar as descrições dos títulos dos vídeos</li>
        <li>Transformar os textos dos títulos com o algoritmo TfidfVectorizer (*2)</li>
        <li>Concatenar matriz densa e matriz sparsa (*3)</li>
        <li>Executar a probabilidade do RandomForestClassifier (*4)</li>
        <li>Aplicar roc_auc_score e average_precision_score</li>
    </ul>
</p>
<p>O AUC ROC varia muito facilmente, mas em nosso projeto é aceitável por conta da pouca quantidade de dados que estamos trabalhando.
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

<p><strong>Atenção</strong>:<br>
    <a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a>
</p>

<p><strong>Nota :</strong><br>
(*1) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Este atrapalha a eficiência do modelo machine learning.<br>
(*2) TfidfVectorizer dá mais peso as palavras que aparecem bastante em determinado exemplo mas não aparece tanto no dadtaset como um todo. Palavras que aparecem pouco entre todos os videos mas aparecerem muito em um video tem mais peso. Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor
Há uma forma mais simples que é criar matriz com contagem de palavras em que em cada linha tem um video, e cada coluna é uma palavra e coloca a quantas vezes a palavra aparece no cruzamento da linha do video com a palavra do titulo do vídeo<br>
(*3) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.<br>
(*4) A probabilidade o percentual de acerto dos títulos acertados no teste.<br>

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
