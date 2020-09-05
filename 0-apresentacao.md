<h5>
<div>
  <table>
    <tr>
      <th><strong>PROJETO</strong></th>
      <th><strong>NÍVEL DE CONHECIMENTO</strong></th>
      <th><strong>TIPO DE DADOS</strong></th>
      <th><strong>TIPO MACHINE LEARNING</strong></th>
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
<h3 align="left">SOBRE O RECOMENDADOR DE VÍDEOS DO YOUTUBE</h3>
<p>Criaremos um modelo preditivo em machine learning sob dados tipo time series, para trazer os vídeos que possívelmente assistiremos.<br>
O modelo consultará os últimos nnn vídeos por data de upload/publicação, considerando o título, visualizações totais desde seu upload, visualizações por dia desde seu upload. </p>

<hr>
<h3 align="left">PROCEDIMENTOS</h3>
<p>Para entendermos a tarefa de um Cientista de Dados e executarmos corretamente esta aplicação devemos ler e seguir os seguintes documentos :
<ol>
    <li><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0-dataset-collect-clean.md">0-dataset-collect-clean.md</a></li>
    <li><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1-Decision-Tree-Classifier.md">1-Decision-Tree-Classifier.md</a></li>
    <li><a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/2-Random-Forest-Classifier.md">2-Random-Forest-Classifier.md</a></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ol>
</p>

<hr>
<h3 align="left">PROCESSO : COLETAR DADOS</h3>
<p>
Para cumprirmos o processo de coletar os dados de vídeos do youtube foi escolhida a bibioteca <a href="https://youtube-dl.org/">youtube_dl</a>, por facilitar trazer as informações em um dicionário python. Isto agiliza o manuseio dos dados.
</p>

<hr>
<h3 align="left">PROCESSO : QUALIDADE DO DATASET</h3>
<p>
No processo de qualidade do dataset nós vamos :
    <ul>
        <li>separar as colunas considerados mais adequadas para o modelo classificador</li>
        <li>criar um campo para identificar se o vídeo é o que desejamos assistir ou não</li>
        <li>limpar e transformar alguns dados</li>
        <li>eliminar dados nulos ou com conteúdo <em>nan</em></li>
        <li></li>
    </ul>
</p>

<br>
<hr>
<h3 align="left">PROCESSO : ANALISAR E ESCOLHER MODELO MACHINE LEARNING</h3>
<p>
Neste processo de análise e escolha do modelo machine learning, inicialmente vamos testar os algorítmos DecisionTreeClassifier para analisar a influência da predição do modelo machine learning nas features quantidade total de visualizações e visualizações por dia. Aqui vamos obter a <em><strong>baseline</strong></em> sob as métricas curva roc (roc_auc_score) e média de precisão (average_precision_score), para analisar os próximos modelos machine learning.<br>
Utilizaremos a técnica para reduzir o impacto de tokens que ocorrem com muita frequência (TfidfVectorizer).<br>
Aplicaremos a técnica de Active Learning para melhor adequar o dataset aos modelos de predição machine learning. E juntamente a esta técnica vamos aplicar diversas limpezas e transformações de dados no dataset.<br>
Aplicaremos o modelo RandomForestClassifier e vamos comparar os resultados com a nossa <em><strong>baseline</strong></em>.
Executaremos a técnica para concatenar conteúdo denso com conteúdo esparso e faremos a predição probabilística com as features visualizações e visualizações por dia mais o título do vídeo, para entender se estamos contruindo um dataset com boa qualidade e se estamos encontrando o algorítmo de predição adequado.

</p>

<p>O processo mais trabalhoso para o Cientista de Dados é o processo da qualidade dos dados composto por :
    <ul>
        <li>obter o dataset</li>
        <li>identificar as inconsistências no dataset</li>
        <li>possivelmente aplicar labelling</p>
        <li>possivelmente aplicar normatization</p>
        <li>possivelmente aplicar padronization</p>
        <li>extrair sujeiras do dataset</li>
        <li>transformar alguns dados no dataset</li>
        <li>analisar e validar a qualidade do dataset</li>
    </ul>
</p>

<p>O segundo processo mais trabalhoso para o Cientista de Dados é o processo avaliação de dados :
    <ul>
        <li>obter o dataset</li>
        <li>identificar as inconsistências no dataset</li>
        <li>possivelmente aplicar labelling</p>
        <li>possivelmente aplicar normatization</p>
        <li>possivelmente aplicar padronization</p>
        <li>extrair sujeiras do dataset</li>
        <li>transformar alguns dados no dataset</li>
        <li>analisar e validar a qualidade do dataset</li>
    </ul>
</p>

<p>
A alta qualidade do dataset significa alto sucesso ao modelo de predição machine learning.
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

<!--<h5><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a></br>
Projeto : Recomendador de vídeos do youtube<br>
Nivel Conhecimento : Iniciante à avançado<br>
Tipo de dados : Time Series<br>
Tipo Machine Learning : Supervisionado<br>

LinkedIn : https://www.linkedin.com/in/claudineien/
</h5>-->
