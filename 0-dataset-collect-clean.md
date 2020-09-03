<h4><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a></br>
Projeto : Desenvolver Recomendador de vídeos do youtube<br>
Notebook : <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0_dataset_collect_clean.ipynb">0_dataset_collect_clean.ipynb</a><br>
Nivel Conhecimento : Iniciante à avançado<br>
Tipo Machine Learning : Supervisionado
</h4>
<br>
<h3 align="center">COLETAR DATASET DE VÍDEOS DO YOUTUBE</h3>

<br>
<p>Atenção :<br>
Para facilitar o entendimento em cada técnica executada, baixar o arquivo <a href=".\file-csv">raw_data_with_labels.csv</a>.
</p>

<p>O notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0_dataset_collect_clean.ipynb">0_dataset_collect_clean.ipynb</a> contém scripts para :
    <ul>
        <li>download dos dados de vídeos do youtube utilizando a biblioteca <a href="https://youtube-dl.org/">youtube_dl</a></li>
        <li>armazenar os dados em um dataframe utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>analisar o conteúdo do dataset utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>limpar e/ou tratar dados para o modelo de predição utilizando a biblioteca <a href="https://numpy.org/install/">numpy</a></li>
        <li>preparar dataset para realizar o labelling</li>
        <li>gravar os dados em arquivo com extensão .csv, para realizar o labelling</li>
    </ul>
</p>

<p>Inconsistências youtube_dl no Github :<br>
    <ul>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26219">ytsearchdateall only returns the first page (20 videos) of results</a></li>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26484">How can we use extract_info from youtube-dl to extract 50, 60, 70 or more videos ?</a></li>
    </ul>
</p>

<hr>
<p>Fontes :
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
    </ul>
</p>

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<h4><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a></h4>
<h4>Objetivo : Desenvolver Recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Iniciante à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
</h4>
<br>
<h3 align="center">COLETAR DATASET DE VÍDEOS DO YOUTUBE</h3>
<p>O notebook <a href="">0_dataset_collect_clean.ipynb</a> fará o download de dados de vídeos do youtube utilizando a biblioteca <a href="https://youtube-dl.org/">youtube_dl</a>, limpará o dataset e o gravará em arquivo com extensão .csv. Mas para facilitar o entendimento em cada técnica executada, você deverá baixar o arquivo <a href=".\file-csv">raw_data_with_labels.csv</a>, para trabalharmos com a mesma fonte dataset.
</p>

<p>O arquivo <a href=".\file-csv" >raw_data_sem_labels.csv</a> será explicado no próximo processo.
</p>

<p>Também aprenderemos a :
    <ul>
        <li>armazenar os dados em um dataframe utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>analisar conteúdo do dataset utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>limpar e/ou tratar dados para o modelo de predição utilizando a biblioteca <a href="https://numpy.org/install/">numpy</a></li>
        <li>preparar dataset para realizar o labelling</li>
    </ul>
</p>

<a href="">0_dataset_collect_clean.ipynb</a> 
Limpar e/ou tratar dados é um processo demorado, para melhor uso pelo modelo de predição utilizando a biblioteca

<p>
A limpeza dos/nos dadaset é a garantia de que o modelo machine learning será o mais efetivo possível.
</p>


<a id="itemtec" >Tecnologias utilizadas neste projeto</a><br>
<em><a href="#itemtec">Tecnologias utilizadas neste projeto</a></em>

<p>Pendência e questionamento no Github :<br>
    <ul>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26219">ytsearchdateall only returns the first page (20 videos) of results</a></li>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26484">How can we use extract_info from youtube-dl to extract 50, 60, 70 or more videos ?</a></li>
    </ul>
</p>

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

<p>Importante :<br>
O notebook <a href="">0_dataset_collect_clean.ipynb</a> gerará o arquivo raw_data_sem_label_youtube-dl.csv.<br>
Mas por conta da quantidade muito limitada que a biblioteca youtube_dl permite baixar, disponibilizamos os arquivos <a href=".\file-csv">raw_data_sem_labels.csv</a> e <a href=".\file-csv">raw_data_with_labels.csv</a> com mais informações para conseguir executar os treinamentos e testes do modelo machine learning</p><br>
<p>Erros|Errors e|and Soluções|Solutions :<br>
Erro | ERROR: 0OX7Y4b1AIg: YouTube said: Unable to extract video data<br>
Solução | Fix:<br>
Don’t forget to first uninstall the version you have then, for more information read <br>
<a href="https://github.com/ytdl-org/youtube-dl/blob/master/README.md#how-do-i-update-youtube-dl">README.md</a> and follow the steps shown there.<br>
Firstly subscribe on reddit to access <a href="https://www.reddit.com/r/youtubedl/comments/hqc577/getting_error_unable_to_extract_video_data/">reddit - YouTube said: ...</a>

</p>
<br><br><br><br><br>
<hr>
<p>Fontes :
    <ul>
        <li><a href="https://curso.mariofilho.com/">   
        Curso Solução Completa de Data Science - Instrutor Mario Filho-Kagle Gran Master</a></li>
    </ul>
</p>
<!--<p></p>-->
