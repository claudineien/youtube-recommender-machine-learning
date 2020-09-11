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

<hr>
<h3 align="left">TAREFA DO CIENTISTA DE DADOS</h3>
<p>Para entendermos na prática uma pequena parte da tarefa de um Cientista de Dados e executar esta pequena aplicação, devemos ler e seguir ordenamente cada um dos documentos a seguir :
<h4><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0-apresentacao.md">0-ciclo-de-vida.md</a>
</h4>
<h4><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0-dataset-collect-clean.md">1-dataset-collect-clean.md</a>
</h4>
<h4><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a>
</h4>
<h4><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Random-Forest-Classifier.md">3-Random-Forest-Classifier.md</a>
</h4>
<h4><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/3-Medir-Active-Learning.md">4-Medir-Active-Learning.md</a>
</h4>

<hr>
<h3>CICLO DE VIDA DE UMA SOLUÇÃO DATA SCIENCE</h3>
<p>
Vamos entender um pouco da técnica que Data Scientists de sucesso como Andrew Y.Ng, Mario Filho entre outros tem aplicado em seus projetos.
</p>

<hr>
<h3>RECOMENDADOR DE VÍDEOS DO YOUTUBE</h3>
<p>Criaremos na linguagem python um modelo machine learning do tipo supervisionado sob dados <em>Time Series</em>, para trazer os vídeos que possívelmente assistiremos dentro de um determinado conjunto de palavras ou frases.<br>
</p>

<hr>
<h3>PROCESSOS QUE APRENDEREMOS</h3>
<h>COLETAR DADOS</h4>
<p>
Nós coletaremos os dados de vídeos do youtube com a bibioteca <a href="https://youtube-dl.org/">youtube_dl</a> por trazer as informações em formato de dicionário do python, e isto agiliza todo e qualquer processo de manuseio dos dados.
</p>

<h4>QUALIDADE DO DATASET</h4>
<p>Nós aprenderemos algumas técnicas que adequam o dataset para uma melhor predição pelo modelo machine learning.
</p>

<h4>ANALISAR MODELOS MACHINE LEARNING</h4>
<p>Aprenderemos algumas técnicas para identificar o modelo machine learning mais eficiente para recomendar vídeos do youtube.
</p>
<p>Utilizaremos os algorítmos DecisionTreeClassifier, RandomForestClassifier e TfidfVectorizer na predição dos vídeos.</p>
<p>Também utilizaremos nos algoritmos mencionados as seguintes técnicas :
    <ul>
        <li>Reduzir o impacto de tokens que ocorrem com muita frequência</li>
        <li>Active Learning</li>
        <li>Concatenar conteúdo denso com conteúdo esparso</li>
    </ul>
</p>

<p>Durante este processo nós vamos procurar respostas para algumas perguntas como :
    <ol>
        <li>Qual será nossa baseline ?</li>
        <li>O dataset está com ótima qualidade para o modelo machine learning ?</li>
        <li>Qual é o erro do modelo machine learning ?</li>
        <li>Estamos melhorando a predição com o modelo X ou Y ?</li>
        <li>Quais ações executar para melhorar o modelo ?</li>
        <li>Como está a probabilidade de acerto ?</li>
        <li>Quais métricas de avaliação, validação aplicar sobre modelo machine learning para melhora-lo ?</li>
        <li>Esta sendo utilizado o limpeza adequado ao dataset ?</li>
        <li>Quais gráficos utilizar para melhor analisar a melhoria do modelo machine learning ?</li>
        <li>O average_precision_score esta melhorando ?</li>
        <li>O roc_auc_score esta melhorando ?</li>
    </ol>
</p>
<hr>
<h3>CONSIDERAÇÕES DO AUTOR</h3>
<p>A tarefa de um Data Scientist é árdua (causa cansaço/fadiga),  porém muito recompensadora quando o resultado é melhorar a vida das pessoas envolvidas diretamente e indiretamente no e pelo processo da organização que utiliza o produto de inteligência arficial para eliminar problemas.</p>

<!--
<br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br> <br>
<p>Testaremos o algorítmo DecisionTreeClassifier para obter a nossa <em><strong>baseline</strong></em> extraída sob as métricas curva auc-roc (roc_auc_score) e média de precisão (average_precision_score), que nos ajudará a analisar os próximos modelos machine learning que vamos testar.
</p>
<p>Testaremos o algorítmo RandomForestClassifier e vamos comparar os resultados preditivos entre os algoritmos até aqui testados.
</p>
<p><strong>Importante :</strong>
O melhor modelo machine learning será aquele em que tanto o average precision (average_precision_score) quando a curva roc (roc_auc_score) ficaram o mais próximo possível de 1, que representa 100%.
</p>
<p>Utilizaremos a técnica para reduzir o impacto de tokens que ocorrem com muita frequência, utilizando o algorítmo TfidfVectorizer. Este também será utilizado como um algorítmo para predizer os vídeos que provavelmente vamos assistir, com base nos títulos dos vídeos.
</p>
<p>Aplicaremos a técnica Active Learning para evitar custos desnecessários, ajudar nas anotações, ajudar a adequar o dataset aos modelos de predição machine learning e contribuir para aumentar a predição verdadeiro positivo em dados que o modelo esta com dificuldade de fazer.
</p>
<p>A todo momento nós vamos comparar os resultados com a nossa <em><strong>baseline</strong></em>, para melhorar nossos modelos.
</p>
<p>Aprenderemos a técnica de concatenar conteúdo denso com conteúdo esparso e faremos a predição probabilística com as features : totais de visualizações, visualizações por dia e o título do vídeo. Assim entenderemos se estamos construindo um dataset com boa qualidade para o algorítmo de predição.
</p>
<p>Aprenderemos a medir o resultado que a técnica Active Learning esta trazendo ao nosso projeto. Neste processo entenderemos a qualidade do active learning aplicado, entenderemos melhor sobre a qualidade da limpeza dos dados para o active learning e para o modelo machine learning. E o mais importante entenderemos se será necessário mudar a estratégia de trabalho com e/ou nos dataset.
</p>
<p>O processo mais trabalhoso para o Cientista de Dados é o processo da qualidade do dataset composto por :
    <ul>
        <li>obter o dataset</li>
        <li>identificar as inconsistências no dataset</li>
        <li>possivelmente aplicar labelling</p>
        <li>possivelmente aplicar normatization</p>
        <li>possivelmente aplicar padronization</p>
        <li>extrair sujeiras do dataset</li>
        <li>transformar alguns dados no dataset</li>
        <li>aplicar os dataset em um ou mais modelos ml para obter uma baseline</li>
    </ul>
</p>
<p>O segundo processo mais trabalhoso para o Cientista de Dados  é o processo avaliação da qualidade do dataset :
    <ul>
        <li>analisar o resultados no modelo machine learning</li>
        <li>comparar os resultados em diversos modelos ml</li>
        <li>identificar técnicas para melhorar a qualidade do dataset</p>
        <li>possivelmente aplicar labelling</p>
        <li>possivelmente aplicar normatization</p>
        <li>possivelmente aplicar padronization</p>
        <li>extrair sujeiras do dataset</li>
        <li>transformar alguns dados no dataset</li>
    </ul>
</p>
<p>
Paciência, perseverança, pensamento analítico, vão produzir dataset com alta qualidade, e a alta qualidade do dataset significa alto sucesso ao modelo de predição machine learning.
</p>
<br>
<hr>
<p>Bibliotecas :
    <ul>
        <li><a href="https://www.crummy.com/software/BeautifulSoup/bs4/doc/">BeautifulSoup4</a> : biblioteca python para puxar dados de uma página html e de arquivos xml e fazer o parsing (*)</li>
        <li><a href="https://requests.readthedocs.io/pt_BR/latest/user/quickstart.html">Requests</a> : é uma biblioteca HTTP para Python simples e elegante, feita para seres humanos</li>
        <li><a href="https://requests.readthedocs.io/pt_BR/latest/user/quickstart.html">youtube_dl</a> : é uma biblioteca para baixar audios, vídeos do YouTube.com e alguns sites.</li>
    </ul>
    <ul>
        <li><a href="https://pypi.org/project/youtube_dl/">pip install youtube_dl</a></li>
        <li><a href="https://youtube-dl.org/">youtube-dl.org</a></li>
    </ul>
    <p>Instalar biblioteca BeautifulSoup4 : pip install beautifulsoup4</p>
    <p>Instalar biblioteca Requests : pip install requests</p>
    <p>(*) Biblioteca substituída pela biblioteca youtube_dl</p>
</p>
<br>
<hr>
<p>Fontes de estudo :
    <ul>
        <li>Curso <a href="https://curso.mariofilho.com/">   
        Solução Completa de Data Science</a> - Instrutor Mario Filho-Kagle Gran Master</li>
        <li><a href="https://github.com/ytdl-org/youtube-dl/blob/master/README.md#how-do-i-update-youtube-dl">youtube_dl README.md</a></li>
        <li><a href="https://www.reddit.com/r/youtubedl/comments/hqc577/getting_error_unable_to_extract_video_data/">reddit - YouTube</a></li>
        <li><a href="https://pypi.org/project/yt-search/">yt-search</a></li>
        <li><a href="https://python-pytube.readthedocs.io/en/latest/user/quickstart.html#downloading-a-video">pytube3</a></li>
        <li><a href="https://www.geeksforgeeks.org/python-program-to-download-complete-youtube-playlist/?ref=rp">BeautifulSoup</a></li>
        <li><a href="https://www.bogotobogo.com/VideoStreaming/YouTube/youtube-dl-embedding.php">youtube-dl embedded</a></li>
        <li><a href="https://www.bogotobogo.com/VideoStreaming/YouTube/Dissecting-YouTube-URLs.php">BeautifulSoup to download complete Youtube playlist</a></li>
        <li><a href="https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html#sphx-glr-auto-examples-model-selection-plot-precision-recall-py">Curva de Precision/Recall</a></li>
        <li><a href="https://scikit-learn.org/stable/modules/model_evaluation.html#roc-metrics">ROC (Receiver Operating Characteristic) Curve</a></li>
        <li><a href="https://www.kaggle.com/adamschroeder/countvectorizer-tfidfvectorizer-predict-comments">TfidfVectorizer</a></li>
        <li><a href="https://www.machinelearningplus.com/time-series/time-series-analysis-python/">Time series</a></li>
    </ul>
</p>
<a id="itemtec" >Tecnologias utilizadas neste projeto</a><br>
<em><a href="#itemtec">Tecnologias utilizadas neste projeto</a></em>
-->
