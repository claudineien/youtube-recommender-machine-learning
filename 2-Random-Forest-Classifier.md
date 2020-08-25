<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>

<h1 align='center'>2o Modelo Machine Learning - RandomForestClassifier</h1>
<p>Neste modelo você aprenderá a fazer um labelling, ler um dataset que esta em um arquivo .csv, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, utilizar a predição do algoritmo RandomForestClassifier, analisar sua probabilidade de acerto de predição e sua precisão curva <a href="blank_">ROC</a>
</p>

<p>Neste modelo é demonstrado como gerar mais conteúdo de dados para treinar o modelo machine learning.</p>

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
Há uma forma mais simples que é criar matriz com contagem de palavras em que em cada linha tem um video, e cada coluna é uma palavra e coloca a quantas vezes a palavra aparece no cruzamento da linha do video com a palavra do titulo do vídeo<br>
(*5) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.<br>
(*6) A probabilidade o percentual de acerto dos títulos acertados no teste.<br>
(*7) Métrica de média de precisão : o método average_precision_score, nos dará o nosso baseline, e seja qual for o modelo machine learning a average_precision deve ser o mais próximo possível de 1.0.<br>
Em cada ponto de corte definido ao calcular precision e recall aparecerá uma curva, a área sobre a curva é a average precision.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<hr>
<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>

<h1 align='center'>Active Learning</h1>
<p>Active Learning é uma técnica que ajuda a escolher melhor quais dados devem receber anotação em um dataset, para desenvolvermos um modelo com melhor performance.</p>
<p>Normalmente utilizado em pequenos projetos, em projetos com orçamento baixo e/ou em projetos com pouco tempo para fazer anotações em dados que serão treinados.<p>
<p>Dependendo do projeto, fazer anotações pode aumentar muito o seu custo, e realizar anotações aleatórias sem um conhecimento qualificado pode prejudicar o modelo preditivo de machine learning.</p>
<p>Por exemplo:<br>
Em projetos de tratamento de imagem radiográfica, ressonância magnética, e similares, que exige experiência médica especializada para anotar nos datasets uma situação de tumor benigno ou maligno ou nenhum dos dois, o Active Learning nos ajuda a separar com maior qualidade os dados que precisamos que recebam as anotações destes especialistas.
</p>

<p><strong>Dica :</strong><br>
Pegar uma quantidade de exemplos que o modelo esta com problema em classificar, selecionar entre 65% e 70% manualmente e deixar entre 35% e 30% automaticamente aleatório, para identificarmos mais alguns exemplos que o modelo esteja com dificuldade em classificar.<br>
Uma boa prática para selecionarmos os exemplos difíceis do modelo classificar é pegar os exemplos entre 45% e 55% (próximos à fronteira 50%-50%) e identificar os exemplos falsos positivo. Exemplos inferiores a 20% de probabilidade de ser Verdadeiro Positivo provavelmente são irrelevantes a este processo.
</p>

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
</p>

<p><strong>Nota :</strong><br>
(*1) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Este atrapalha a eficiência do modelo machine learning.<br>
</p>

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
(*2) TfidfVectorizer dá mais peso as palavras que aparecem bastante em determinado exemplo mas não aparece tanto no dadtaset como um todo. Palavras que aparecem pouco entre todos os videos mas aparecerem muito em um video tem mais peso. Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor
Há uma forma mais simples que é criar matriz com contagem de palavras em que em cada linha tem um video, e cada coluna é uma palavra e coloca a quantas vezes a palavra aparece no cruzamento da linha do video com a palavra do titulo do vídeo<br>
(*3) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.<br>
(*4) A probabilidade o percentual de acerto dos títulos acertados no teste.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<hr>
<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>

<h1 align='center'>Medir Impacto do Active Learning</h1>
<p>
01 df1 com aproximadamente 500 anotações e labelling e df2 com 100 novos exemplos com labels.<br>
O df2 possui a mais, a coluna p com a probabilidade do modelo treinado pelo algorítmo RandomForestClassifier, adicionada no momento do Active Learning, e receberá a nova coluna Novo <br>
? Curioso ?<br>
Se usar as probabilidades geradas pelo modelo RandomForestClassifier Quais são as métricas, qual o erro, qual o average_precision, qual é o auc no dataset que acabou de fazer as labels se utilizar a probabilidade do modelo RandomForestClassifier ? Objetivo é entender se esta perto ou longe do objetivo de ter um bom modelo machine learning<br>
Ao aplicar average_precision_score e roc_auc_score neste ultimo dataset comparando com o dataset criado para o modelo RandomForestClassifier percebemos que a alteração é mínima.
O auc esta sensível ao número de exemplos, por que em 100 exemplos apenas 14 são verdadeiros positivo
<br>

02
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
