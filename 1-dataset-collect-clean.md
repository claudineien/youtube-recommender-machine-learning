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

<br>
<h3 align="center">COLETAR DATASET DE VÍDEOS DO YOUTUBE</h3>
<p>
Nós coletaremos os dados de vídeos do youtube com a bibioteca <a href="https://youtube-dl.org/">youtube_dl</a> por trazer as informações em formato de dicionário do python, e isto agiliza todo e qualquer processo de preparação dos dados para o modelo machine learning.
</p>

<br>
<p><strong>Atenção :</strong><br>
Para facilitar o entendimento em cada técnica executada, baixar o arquivo <a href=".\file-csv">raw_data_with_labels.csv</a>.
</p>

<p>O notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/1_dataset_collect_clean.ipynb">1_dataset_collect_clean.ipynb</a> contém scripts para :
    <ul>
        <li>download dos dados de vídeos do youtube utilizando a biblioteca <a href="https://youtube-dl.org/">youtube_dl</a></li>
        <li>armazenar os dados em um dataframe utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>analisar o conteúdo do dataset utilizando a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a></li>
        <li>limpar e/ou tratar dados para o modelo de predição utilizando a biblioteca <a href="https://numpy.org/install/">numpy</a></li>
        <li>preparar dataset para realizar o labelling</li>
        <li>gravar os dados em arquivo com extensão .csv, para realizar o labelling</li>
    </ul>
</p>
<br>
<hr>
<p>Inconsistências na biblioteca youtube_dl no Github :<br>
    <ul>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26219">ytsearchdateall only returns the first page (20 videos) of results</a></li>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26484">How can we use extract_info from youtube-dl to extract 50, 60, 70 or more videos ?</a></li>
    </ul>
</p>

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
    </ul>
</p>
