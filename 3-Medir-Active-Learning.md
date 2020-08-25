<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>

<h1 align='center'>Medir Impacto do Active Learning</h1>
<p>Por termos poucos dados de validação e o auc estar muito instável, aplicaremos algumas técnicas para entendermos se o active learning esta trazendo efeito podemos medir aumentando os dados de validação, os dados de treino e/ou ambos. Normalmente no active learning aumentam-se os dados para treino. Depois avaliar com as métricas roc_auc_score e average_precision_score.<br>
</p>
<p>
01 df1 com aproximadamente 500 anotações e labelling e df2 com 100 novos exemplos com labels.<br>
O df2 possui a mais, a coluna p com a probabilidade do modelo treinado pelo algorítmo RandomForestClassifier, adicionada no momento do Active Learning, e receberá a nova coluna Novo com valor 1.<br>
? Curioso ?<br>
Se usar as probabilidades geradas pelo modelo RandomForestClassifier Quais são as métricas, qual o erro, qual o average_precision, qual é o auc no dataset que acabou de fazer as labels se utilizar a probabilidade do modelo RandomForestClassifier ? Objetivo é entender se esta perto ou longe do objetivo de ter um bom modelo machine learning<br>
Ao aplicar average_precision_score e roc_auc_score neste ultimo dataset comparando com o dataset criado para o modelo RandomForestClassifier percebemos que a alteração é mínima em ambos. O auc é sensível por que estamos trabalhando com uma quantidade muito pequena de dados.
<br>
Criar um novo dataframe e juntar o dataset que acabou de criar ao dataset original.<br>
Este novo dataframe terá 100 exemplos com o campo Novo igual a 1-Exemplos que acabou de criar a anotação e igual a 0-Exemplos que já tinham as anotações. Esta prática ajudará a comparar o efeito do active learning.
</p>

<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
<p>
    <ul>
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
