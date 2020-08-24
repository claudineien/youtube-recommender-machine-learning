<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>

<h1 align='center'>2o Modelo Machine Learning - RandomForestClassifier</h1>
<p>Neste modelo você aprenderá a fazer um labelling, ler um dataset que esta em um arquivo .csv, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo RandomForestClassifier, analisar sua probabilidade de acerto de predição e sua precisão curva <a href="blank_">ROC</a>
</p>

<p>Neste motivo é demonstrado como gerar mais conteúdo de dados para treinar o modelo machine learning.</p>

<h3>LABELLING</h3>
<p>Abrir o arquivo <a href="blank_">raw_data_sem_labels.csv</a> no excel através da opção de importar dados de um arquivo .csv, criar a coluna Y (*1) e nesta coluna inserir o número 0 nas linhas cujo título do vídeo não interesse e não quer assistir ou inserir 1 nas linhas cujo vídeo seja interessante e quer assistir.</p>

<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
    <ul>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (*2)</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
        <li>Plotar - Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
    </ul>

<p><strong>Aprender mais :</strong><br>
<a href="https://strftime.org/">Tabela de códigos para converter strings em datas no Python</a><br>
<a href="http://gskinner.com/RegExr/">Testador de expressões regulares</a><br>
<a href="https://numpy.org/doc/stable/reference/arrays.datetime.html">Numpy : Timedelta</a><br> 
<a href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html">Pandas : Time/Date</a><br>
<a href="https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html#sphx-glr-auto-examples-model-selection-plot-precision-recall-py">Curva de Precision/Recall</a><br>
<a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a><br>
<a href="">Dados train and test</a><br>
</p>

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.<br>
Features x Banco de dados : Em um projeto real se houver muitas features, uma boa atitude é salvar em banco de dados
</p>

<p><strong>Nota :</strong><br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y para padronizar o ensinamento<br>
(*2) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Este atrapalha a eficiência do modelo machine learning.<br>
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

<p><strong>Aprender mais :</strong><br>
<a href="https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction">Bag of Words (e TF-IDF)</a><br>
<a href="https://docs.scipy.org/doc/scipy/reference/sparse.html">Sparse matrices</a><br>
</p>

<p><strong>Atenção</strong>:<br>
<a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a>
</p>

<p><strong>Dica :</strong><br>
50% para treino e 50% para teste : Por ser uma time series, é quase 100% certeza que os dados de treino serão diferentes dos dados de validação, e a metodologia mais eficiente é dividir os dados o mais próximo possível de 50%<br>
Concatenar variaveis : Pode utilizar as funções hstack e/ou vstack do scipy sparse. A primeira juntará horizontalmente e a segunda verticalmente.
Não as funções de mesmo nome do objeto numpy, por que não é otimizado para lidar com matriz sparsa.
</p>

<p><strong>Nota :</strong><br>
(*3) Há bibliotecas com métodos para separar os dados de treino e os dados de teste, que pode ser em percentual e/ou em quantidade<br>
(*4) TfidfVectorizer dá mais peso palavras que aparecem bastante em determinado exemplo mas não aparece tanto no dadtaset como um todo. Palavras que aparecem pouco entre todos os videos mas aparecerem muito em um video tem mais peso. Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor
Há uma forma mais simples que é criar matriz com contagem de palavras em que em cada linha tem um video, e cada coluna é uma palavra e coloca a quantas vezes a palavra aparece no cruzamento da linha do video com a palavra do titulo do vídeo
(*5) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.
(*6) A probabilidade o percentual de acerto dos títulos acertados no teste.<br>
(*7) Métrica de média de precisão : o método average_precision_score, nos dará o nosso baseline, e seja qual for o modelo machine learning a average_precision deve ser o mais próximo possível de 1.0.<br>
Em cada ponto de corte definido ao calcular precision e recall aparecerá uma curva, a área sobre a curva é a average precision.<br>

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
