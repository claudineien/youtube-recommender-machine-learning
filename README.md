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

<hr>
<h3 align="left">CIÊNCIA DE DADOS NA RECOMENDAÇÃO DE VÍDEOS DO YOUTUBE</h3>
<p>Através deste projeto recomendador de vídeos do youtube nós entenderemos na prática uma pequena parte de tarefas executadas no processo Ciência de Dados.</p>

<p>Utilizaremos :
    <ul>
        <li>linguagem de programação <a href="https://www.python.org/">python</a> 3.7</li>
        <li>plataforma de desenvolvimento <a href="https://jupyter.org/">jupyter notebook</a></li>
        <li>sistema operacional Windows Professional 64bits processador x64</li>
        <li>8g memória RAM</li>
        <li>processador Intel (R) Corel (TM) i7-2640M CPU @ 2.80GHZ 2.80GHz</li>
    </ul>
</p>

<h3>TÉCNICAS QUE APRENDEREMOS<br>
Para um melhor entendimento devemos ler e seguir ordenamente os documentos a seguir :</h3>
<p>No documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0-ciclo-de-vida.md">0-ciclo-de-vida.md</a> aprenderemos sobre o ciclo de vida de um projeto Data Science e através desta técnica desenvolveremos o modelo machine learning para recomendar vídeos do youtube.</p>

<p>No documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-dataset-collect-clean.md">1-dataset-collect-clean.md</a> aprenderemos sobre a coleta de dados de vídeos do youtube com a bibioteca <a href="https://youtube-dl.org/">youtube_dl</a>, por trazer os dados em formato de dicionário do python, que agiliza todo e qualquer processo de preparação dos dados para o modelo machine learning.</p>

<p>No documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Decision-Tree-Classifier.md">2-Decision-Tree-Classifier.md</a> aprenderemos algumas técnicas para adequar o dataset para uma melhor predição pelo modelo machine learning com o algorítmo DecisionTreeClassifier.</p>

<p>No documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/3-Random-Forest-Classifier-Active-Learning.md">3-Random-Forest-Classifier-Active-Learning.md</a> iniciaremos o entendimento sobre algumas técnicas para identificar o modelo machine learning mais eficiente entre o DecisionTreeClassifier e RandomForestClassifier, além de continuarmos com as adequações no dataset, aplicar a técnica Active Learning o utilizar o algorítimo TfidfVectorizer.</p>

<p>No documento <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/3-Medir-Active-Learning.md">4-Medir-Active-Learning.md</a> nós vamos entender o resultado que Active Learning traz ao nosso projeto.</p>

<p>Durante o processo nós vamos encontrar respostas à algumas perguntas como :
    <ol>
        <li>Qual é o problema a resolver ?</li>
        <li>Qual será a melhor solução ?</li>
        <li>Qual será nossa a baseline dentro no dataset ?</li>
        <li>Qual será nossa a baseline no modelo machine learning ?</li>
        <li>O dataset está com ótima qualidade para o modelo machine learning ?</li>
        <li>Qual é o erro do modelo machine learning ?</li>
        <li>Estamos melhorando a predição com o modelo X ou Y ?</li>
        <li>Quais ações executar para melhorar o modelo ?</li>
        <li>Como está a probabilidade de acerto ?</li>
        <li>Quais métricas de avaliação, validação aplicar sobre modelo machine learning para melhora-lo ?</li>
        <li>Esta sendo utilizado a limpeza adequada no dataset ?</li>
        <li>Quais gráficos utilizar para melhor analisar a melhoria do modelo machine learning ?</li>
        <li>O average_precision_score esta melhorando ?</li>
        <li>O roc_auc_score esta melhorando ?</li>
    </ol>
</p>
<hr>
<h3>MENSAGEM DO AUTOR</h3>
<p>A tarefa de um Data Scientist é árdua (causa cansaço/fadiga),  porém muito recompensadora quando o resultado é melhorar a vida das pessoas envolvidas diretamente e indiretamente pelo processo que utiliza a inteligência arficial para eliminar problemas.</p>

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
