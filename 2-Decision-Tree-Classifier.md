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

<h1 align='center'>1o Modelo Machine Learning - DecisionTreeClassifier</h1>
<p>Nosso objetivo neste processo é obter as primeiras métricas, que servirão como guia para nos ajudar a otimizar os algorítmos machine learning até obter um modelo no qual as métricas indiquem como sendo a solução machine learning que precisamos.</p>
<p>Nossas métricas base serão:
    <ol>
        <li><strong>AUC-ROC</strong> para indicar se o nosso modelo esta rankeando corretamente os exemplos. É a probabilidade que exemplo selecionado randômicamente tem mais probabilidade preditiva de ser positivo do que ser um exemplo randomicamente selecionado negativo.</li>
        <li><strong>Average precision</strong> indica se o nosso modelo pode corretamente indentificar todos os exemplos positivos sem acidentalmente marcar também muitos exemplos negativos como exemplos positivos.</li>
    </ol>
</p>
<p>Utilizaremos o notebook <a href="/file-ipynb/2_Decision_Tree_Classifier.ipynb">2_Decision_Tree_Classifier.ipynb</a> para entendermos um pouco de como este processo funciona.</p>
<p>Iniciaremos aplicando a técnica Labelling, aplicaremos limpezas no dataset, criaremos algumas Features, analisaremos o gráfico time series da biblioteca pandas, faremos tuning no algorítmo machine learning, treinaremos o algorítmo DecisionTreeClassifier e por fim teremos o resultados das métricas.</p>

<hr>
<h3>LABELLING</h3>
<p>Vamos aplicar o labelling para o algoritmo machine learning predizer com o melhor average precision e auc-roc possível o vídeo que possivelmente assistiremos.</p>
<p>
A seguir estão os procedimentos para aplicarmos o labelling:
    <ol>
        <li>Abrir o arquivo <a href="/2-dataset">raw_data_sem_labels.csv</a> em uma planilha eletrônica como ms excel, <a href="https://gsuite.google.com/intl/pt-BR/products/sheets/">google sheets</a> ou <a href="https://pt-br.libreoffice.org/descubra/calc/"> LibreOffice</a> através da opção de importar um arquivo .csv</li>
        <li>Criar a coluna Y (*1)</li>
        <li>Inserir na coluna Y o número 0 ou 1 (*2)</li>
    </ol>
</p>
<p><strong>Importante:</strong><br>
Baixar o arquivo <a href="/2-dataset">raw_data_with_labels.csv</a>, cujo o labelling foi aplicado para facilitar nosso entendimento em cada técnica executada</p>

<hr>
<h3>COM NOTEBOOK <a href="/file-ipynb/2_Decision_Tree_Classifier.ipynb">2_Decision_Tree_Classifier.ipynb</a></h3>
<h4>LIMPAR E TRANSFORMAR DADOS</h4>
<p>Nossa primeira tarefa é fazer uma cópia do dataframe original e extrair todos os dados cujo y estejam configurados (labelling realizado) com 1 ou 0 (*2), vamos utilizar os métodos head(), info() e/ou tail() para analisar o conteúdo do dataset.</p>
<p>Durante a análise do dataset perceberemos que uma boa prática para treinar o algoritmo machine learning é extrair somente a data do campo watch-time-text e extrair somente a quantidade do campo watch-view-count e transformá-los em recursos para identificar a quantidade de visualizações por dia por vídeo encontrado. Estes itens atendem o passo 03 do <a href="/0-ciclo-de-vida.md">CICLO DE VIDA DE UMA SOLUÇÃO EM CIÊNCIA DE DADOS</a></p>
<p>Na conversão do campo watch-view-count utilizaremos a função fillna() para substituir o conteúdo nan (considerado nulo) por 0, por que o conteúdo nan prejudica a eficiência do modelo machine learning.</p>
<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : Atenção para o local do ponto, que em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.</p>

<h4>PLOTAR - EXIBIR DADOS EM GRÁFICO</h4>
<p>Para uma visualização rápida da quantidade de videos visualizados por dia por ano-mês, vamos plotar um gráfico time series com a biblioteca pandas. Vamos observar que há um grande pico no volume de vídeos visualizados no final do período ano-mês que pode ter sido por conta do youtube ter aplicado alguma aleatoridade na pesquisa dos dados ou por conta de uma situação extraordinária qualquer.</p>
<img src="/3-images/grafico_video_ano_mes.png">
<p>Este aumento muito desproporcional apenas em um mês do ano pode prejudicar o treinamento do algoritmo machine learning, se não executarmos a técnica de balanceamento dos dados adequada.</p>

<h4>MODELO MACHINE LEARNING</h4>
<p>Com o algorítmo DecisionTreeClassifier vamos analisar rapidamente a influência da predição do modelo machine learning apenas com features view e view_por_dia por data de upload. Para esta análise devemos :
    <ul>
        <li>Separar os dados de treino e dados de teste por data de publicação/upload, por ser uma time series (*3)</li>
        <li>Configurar o parâmetro class_weight="balanced"</li>
        <li>Treinar modelo machine learning</li>
    </ul>
</p>
<p>Para melhorar a eficiência do algorítmo machine learning, na predição de vídeos, é uma boa prática balancear a quantidade de visualizações por dia por ano-mês por vídeo coletado por data de upload entre o dataset treino e dataset teste, por que foi muito grande o aumento de vídeos no final do período.</p>
<p>O balanceamento entre os dataset treino e dataset teste é realizado configurando o parâmetro class_weight igual a "balanced".</p>

<h4>APLICAR AS MÉTRICAS</h4>
<p>Métrica <strong>average precision</strong> da biblioteca sklearn.metrics que conforme imagem a seguir informa que o algorítmo teve um percentual de 14,81% de exemplos positivos, que representa vídeos cujo labelling é 1 (*2).<br>
<img src="/3-images/0dectrecla_aver_prec.png"></p>
<p>Métrica <strong>auc-roc</strong> da biblioteca sklearn.metrics que conforme imagem a seguir informa que o algorítmo teve uma probabilidade percentual de 57,05% de selecionar os exemplos positivos, que representa vídeos cujo labelling é 1 (*2).<br>
<img src="/3-images/0dectrecla_auc_roc.png"></p>
<p>Esta serve para melhor visualizarmos o ranking dos vídeos : dos mais interessantes para os menos interessantes.</p>
<p>Importante :<br>
O objetivo em ambos métricas average precision e auc-roc é alcançar 1.0 ou o valor mais próximo possível, sendo esta a nossa baseline técnica em machine learning.</p>

<br>
<p><strong>Dica :</strong><br>
Dataset Time series 50% treino e 50% teste : Por ser uma time series, é quase 100% certeza que os dados de treino serão diferentes dos dados de validação, e a metodologia mais eficiente é dividir os dados o mais próximo possível de 50%<br>
Arvore de decisão : É uma das melhores maneiras de entender a relação das features (recursos) com o target (alvo)</p>

<h3>INTERPRETAR A DECISION TREE</h3>
<p>Esta é uma boa forma de entender rapidamente como o as features (recursos) se relacionam ao target (alvo).</p>
<p>Para uma rápida analise configuramos a profundidade máxima (max_depth) de 2 níveis de nós.<br>
<img src="/3-images/decisiontree.png"></p>
<p>
Aplicamos balanceamento (class_weight="balanced") no peso dos vídeos, e o nó raiz exibe dentro do total 15110.0 visualizações, amostra de 228 vídeos, heterogeneidade em 50% (gini) e os valores com peso balanceado em 114.0 exemplos negativos e 114.0 positivos. Então :<br>
    <ol>
        <li>quando inferior ao nó raiz (à esquerda), no 1o nível do nó vemos que a quantidade por dia é inferior a 1 visualização por dia para 133 amostras de vídeo, no 2o nó à esquerda as 14 amostras são exemplos negativos 0.0, não interessantes. No nó a direita há mais amostras e estes provavelmente são vídeos que interessam por ter uma pontuação positiva de 92.625.
        </li>
        <li>quando superior ao nó raiz (à direita), no 1o nível de nó vemos que a quantidade pode ser menor ou igual ou superior a 26712.0. Se inferior temos 20 amostas negativas 0.0, não interessantes. A direita há muita amostra porem pela classificação 21.375 provavelmente são vídeos que não interessam.</li>
    </ol>
</p>

<p><strong>Nota :</strong><br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y (Youtube) para facilitar nosso entendimento.<br>
(*2) 0 -Vídeo que provavelmente não vamos assistir; 1 -Vídeos que provavelmente vamos assistir
(*3) Há bibliotecas com métodos para separar os dados de treino e os dados de teste, que pode ser em percentual e/ou em quantidade.<br>
<br>
Vamos lembrar :<br>
:/: Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos<br>

:/: Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?
</p>

<br>
<hr>
<p>Fontes de estudo :
    <ul>
        <li>Curso <a href="https://curso.mariofilho.com/">   
        Solução Completa de Data Science</a> - Instrutor Mario Filho-Kagle Gran Master</li>
        <li><a href="https://www.youtube.com/watch?v=Y1XAP6omGzo">Entendiendo las Curvas ROC</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/generated/sklearn.tree.plot_tree.html">Método plot_tree</a></li>
        <li><a href="https://glassboxmedicine.com/2020/07/14/the-complete-guide-to-auc-and-average-precision-simulations-and-visualizations/">auc and average precision</a></li>
        <li><a href="https://strftime.org/">Tabela de códigos para converter strings em datas no Python</a></li>
        <li><a href="http://gskinner.com/RegExr/">Testador de expressões regulares</a></li>
        <li><a href="https://numpy.org/doc/stable/reference/arrays.datetime.html">Numpy : Timedelta</a></li>
        <li><a href="https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html">Pandas : Time/Date</a></li>
        <li><a href="https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html#sphx-glr-auto-examples-model-selection-plot-precision-recall-py">Curva de Precision/Recall</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a></li>
        <li><a href="https://towardsdatascience.com/understanding-auc-roc-curve-68b2303cc9c5">Understanding AUC-ROC</a></li>
        <li><a href="https://pypi.org/project/feather-format/">feather-format</a></li>
        <li><a href="https://machinelearningmastery.com/cost-sensitive-decision-trees-for-imbalanced-classification/#:~:text=The%20decision%20tree%20algorithm%20is,perform%20well%20on%20imbalanced%20datasets.&text=How%20the%20decision%20tree%20algorithm,class%20weight%20when%20selecting%20splits.">DecisionTreeClassifiier - Class_Weight</a></li>
    </ul>
</p>
