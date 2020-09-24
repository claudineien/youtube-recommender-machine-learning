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

<h1 align='center'>Resultado com Active Learning</h1>
<p>O objetivo nesta fase é entender se o Active Learning vai trazer ou não melhorias ao nosso modelo machine learning. No primeiro momento identificaremos as melhorias através das métricas average precision e auc-roc. Esta análise também nos ajudará a acompanhar mais rápido a qualidade do dataset, entender se há necessidade de termos mais dados para treinar e testar e aplicar uma ou mais mudanças em um ou mais processos do desenvolvimento deste projeto de ciência de dados.</p>
<p>Utilizaremos o notebook <a href="/1-source-code/4_Resultado_Active_Learning.ipynb" >4_Resultado_Active_Learning.ipynb</a> para entendermos um pouco de como este processo funciona.</p>
<p>Nesta etapa vamos aplicar a técnica Labelling, aplicaremos limpezas no dataset, criaremos algumas Features, trabalharemos com matriz esparsas, term frequency, faremos tuning no algorítmo machine learning, treinaremos o algorítmo RandomForestClassifier e por fim teremos o resultados das métricas.</p>

<hr>
<h3>PROCEDIMENTOS QUE APLICAREMOS NO DATASET</h3>
<h4>LABELLING</h4>
No final do notebook <a href="/1-source-code/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb</a> nós aplicamos a técnica active learning e criamos o arquivo <a href="/2-dataset">active_labels.csv</a> para fazermos o labelling.</p>
<p>Vamos fazer o labelling conforme documentado em <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>.</p>
<p>Importante :<br>
Baixar o arquivo <a href="/2-dataset">active_labels.csv</a>, cujo labelling já foi aplicado para facilitar nosso entendimento em cada técnica executada.</p>

<hr>
<h3>COM NOTEBOOK <a href="/1-source-code/4_Resultado_Active_Learning.ipynb" >4_Resultado_Active_Learning.ipynb</a></h3>
<h4>A PRIMEIRA MÉTRICA</h4>
<p>Ao aplicarmos as métricas average precision e auc-roc sobre o arquivo <a href="/2-dataset">active_labels.csv</a> considerando
as colunas y (labelling) e p (probabilidade) com o percentual de probabilidade de ser 1 (Video que provavelmente vamos assistir), vamos obter o seguinte resultado :<br>
<img src="/3-images/3rand_for_activ_learn.png"><br>
Comparando com as primeiras métricas, exibidas a seguir, do modelo DecisionTreeClassifier percebemos que houve uma melhora nas métricas :<br>
<img src="/3-images/2rand_fores_tfid0.png"> | <img src="/3-images/2rand_fores_tfid1.png">
<p>Esta primeira métrica realizada sobre o dataset com 100 exemplos que o modelo machine learning esta com dificuldade em classificar, indica que :<br>
- As métricas average_precision_score e roc_auc_score estão sensíveis com relação a pequena quantidade de dados que temos.<br>
- O dataset provavelmente deve receber mais tratamento e/ou mais dados para melhorarmos o modelo machine learning.<br>
- O modelo parece estar melhorando com o Active Learning</p>
<p>Analisando um pouco do dataframe do arquivo <a href="/2-dataset" >active_labels.csv</a> :<br>
A coluna p contém a probabilidade que o modelo machine learning dá ao item 579 de ser 37,5% positivo e ao item 846 de ser 82,6% positivo.<br>
Se usarmos um ponto de corte de 50%, sendo acima positivo e abaixo negativo, então o item :<br>
- 579 seria um Falso Negativo (37,5% < 50%)<br>
- 846 seria um Falso Positivo (82,6% > 50%)</p>
<p>Vamos concatenar os arquivos <a href="/2-dataset">active_labels.csv</a> com aproximadamento 100 exemplos ao <a href="/2-dataset">raw_data_with_labels.csv</a> com aproximadamento 500 exemplos e ambos com labelling realizado, para melhor treinarmos o modelo machine learning.</p>

<p>, criar mais exemplos para treino e teste, analisar o conteúdo do dataset, interpretar alguns dados, fazer algumas limpezas nos dados, aplicar algumas técnicas para limpeza de dados, utilizar o objeto TfidfVectorizer para transformar textos em uma representação significante de números, vamos analisar probabilidade, métricas roc_auc_score e average_precision_score, comparar com a referencial inicial obtida no notebook <a href="/1-source-code/2_Decision_Tree_Classifier.ipynb">2_Decision_Tree_Classifier.ipynb</a> e comparar com os resultados gerados no notebook <a href="/1-source-code/3_Random_Forest_Classifier.ipynb">3_Random_Forest_Classifier.ipynb</a>.
</p>
 A seguir veremos como aplicaremos as seguintes técnicas :<br>
    <ol>
        <li>aumentando apenas os dados de validação</li>
        <li>aumentando apenas os dados de treino</li>
        <li>aumentando os dados de validação e de treino</li>
    </ol>


<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
<p>
    <ul>
        <li>Vamos incluir a coluna [Novo] no dataframe com os aproximadamente 100 exemplos.
        </li>
        <li>Vamos incluir o número 1 na coluna [Novo] criada no dataframe com os aproximadamente 100 exemplos (*2)
        </li>
        <li>Vamos importar aproximadamente 498 registros do dataset <a href="\file-csv">raw_data_with_labels.csv</a>, cujo o campo y seja diferente de nulo/vazio, estão com anotações (labelling) 1 para vídeos que gosto ou 0 para vídeos que não gosto.
        </li>
        <li>Vamos unir os dois dataframes importados gerando um novo dataframe com aproximadamento 600 registros. Na coluna [Novo] estaram gravados 1 indicando dataset do dataframe que continha 100 registros e gravará nan's para os outros 500 registros.
        </li>
        <li>Vamos eliminar a coluna p relacionada a probabilidade de acerto dos vídeos. Esta não será usada nos próximos testes.
        </li>
        <li>Extrair a descrição dos títulos dos vídeos.</li>
        <li>Vamos substituir o conteúdo nan por 0 na coluna [Novo] referente aos 500 registros que estão com nan's (*2).
        </li>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas.</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número</li>
        <li>Criar Features - Tratamentos específicos nos dados.</li>
    </ul>
</p>

<hr>
<h3>AUMENTAR DATASET DE VALIDAÇÃO</h3>
<p>É o procedimento menos utilizado. Esta sendo utilizado por que a quantidade de dados é muito pouca. Esta é uma boa técnica para analisarmos melhor a probabilidade, média de precisão e o AUC ROC. Aqui os dados de validação são novos e os dados de treino antigos.
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

<p><strong>Atenção :</strong><br>
É indicado que o dataset de validação não seja alterado.<br>
Utilizaremos 
</p>

<hr>
<h3>AUMENTAR DATASET DE TREINO</h3>
<p>Este é o procedimento mais tradicional/utilizado. Também utilizada a análise da probabilidade, média de precisão e o AUC ROC. Aqui os dados de validação são antigos e os dados de treino são os novos.
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

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Novo dataframe : Evite alterar os dados no dataframe principal, trabalhe sempre com a cópia. Esta prática agiliza o processo de manipulação dos dados e se algo der errado basta executar a instção de cópia do dataframe novamente, alem de evitar que alguma rotina que utiliza o dataframe principal funcione indevidamente.
</p>

<p>Nota :<br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y (Youtube) para facilitar nosso entendimento.<br>
(*2) Conteúdo na coluna Novo :<br>
1-Relacionados aos 100 exemplos do dataset <a href=".\file-csv">active_labels1_done.csv</a><br>
0-Relacionados aos exemplos do dataset <a href=".\file-csv">raw_data_with_labels.csv</a>
(*3) TfidfVectorizer dá mais peso as palavras que aparecem bastante em determinado exemplo mas não aparece tanto no dadtaset como um todo. Palavras que aparecem pouco entre todos os videos mas aparecerem muito em um video tem mais peso. Ex : machine e learning apareceram em praticamente todos os vídeos e terão um peso menor
Há uma forma mais simples que é criar matriz com contagem de palavras em que em cada linha tem um video, e cada coluna é uma palavra e coloca a quantas vezes a palavra aparece no cruzamento da linha do video com a palavra do titulo do vídeo<br>
(*4) Matriz esparsa armazena valores diferentes de zero -é mais otimizada.<br>
(*5) A probabilidade é o percentual de acerto que o modelo machine learning alcançou.<br>

Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?<br>

A função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Conteúdo nan atrapalha a eficiência do modelo machine learning.
</p>

<p>Importante :<br>
Na maior parte das vezes quanto mais conteúdo estiver no dataset, melhor será modelo machine learning.
</p>

<p>Issue github :<br>
    <a href="https://github.com/scikit-learn/scikit-learn/issues/16017">TfidfVectorizer ngrams does not work when vocabulary provided #16017</a>
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

<!--Mensagens aos familiares e amigos pelo whatsapp
Muita paz à vocês meus amores
Muita felicidade amores
Muita sabedoria a cada um de vocês família amores.
Que você sempre tenha forças para lutar contra o pode destruir você e a quem você quer bem
Desejo que tenham saúde mental e física para você compartilhar todas as boas ações e intenções com as pessoas que você quer bem
Desejo que a paciência aumenta em vossa vida e na vida de todas as pessoas que convivem com você para que construam uma relação de confiança. Bom dia.
-->
