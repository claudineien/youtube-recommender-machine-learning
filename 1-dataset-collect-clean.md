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

<h3 align="center">COLETAR DATASET DE VÍDEOS DO YOUTUBE</h3>
Para obtermos os mesmos resultados e facilitar o nosso entendimento em cada técnica executada, baixar os arquivos :
<ul>
  <li><a href="/2-dataset">raw_data_with_labels.csv</a></li>
  <li><a href="/file-ipynb/1_dataset_collect_clean.ipynb">1_dataset_collect_clean.ipynb</a></li>
</ul>
<p>Vamos aprender a fazer download dos dados de vídeos do youtube utilizando a biblioteca <a href="https://youtube-dl.org/">youtube_dl</a> que é muito boa por trazer as informações em formato de dicionário do python, e este formato agiliza todo e qualquer processo de preparação dos dados para o modelo machine learning.</p>
<p>Precisamos aplicar o labelling para treinar o modelo machine learning, que é classificar manualmente se o vídeo é o que possivelmente vamos assistir ou não. Para isto será necessário converter o tipo de dado objeto com conteúdo de data para o tipo data e encontrar a quantidade de dias de publicação do vídeo.</p>
<p>Os tratamentos dos dados serão respectivamente realizados com a biblioteca <a href="https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html">pandas</a> e <a href="https://numpy.org/install/">numpy</a> ambas muito boas para tratamento do dataset.</p>
<p>Disponibilizaremos o dataset trabalhado em um arquivo .csv para aplicar labelling, que ajudará na predição do algoritmo machine learning.</p>
</p>
<br>
<hr>
<p>Inconsistências na biblioteca youtube_dl registradas no github :<br>
    <ul>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26219">ytsearchdateall only returns the first page (20 videos) of results</a></li>
        <li><a href="https://github.com/ytdl-org/youtube-dl/issues/26484">How can we use extract_info from youtube-dl to extract 50, 60, 70 or more videos ?</a></li>
    </ul>
</p>

<br>
<hr>
<p>Fontes de estudo :
    <ul>
        <li>Curso <a href="https://curso.mariofilho.com/">   
        Solução Completa de Data Science</a> - Instrutor Mario Filho-Kagle Gran Master</li>
        <li><a href="https://numpy.org/install/">numpy</a></li>
        <li><a href="https://pandas.pydata.org/community/ecosystem.html">pandas.pydata.org</a></li>
        <li><a href="https://github.com/ytdl-org/youtube-dl/blob/master/README.md#how-do-i-update-youtube-dl">youtube_dl README.md</a></li>
        <li><a href="https://www.reddit.com/r/youtubedl/comments/hqc577/getting_error_unable_to_extract_video_data/">reddit - YouTube</a></li>
        <li><a href="https://pypi.org/project/yt-search/">yt-search</a></li>
        <li><a href="https://www.bogotobogo.com/VideoStreaming/YouTube/youtube-dl-embedding.php">youtube-dl embedded</a></li>
      </ul>
</p>

<!--
<li><a href="https://python-pytube.readthedocs.io/en/latest/user/quickstart.html#downloading-a-video">pytube3</a></li>
<li><a href="https://www.geeksforgeeks.org/python-program-to-download-complete-youtube-playlist/?ref=rp">BeautifulSoup</a></li>
<li><a href="https://www.bogotobogo.com/VideoStreaming/YouTube/Dissecting-YouTube-URLs.php">BeautifulSoup to download complete Youtube playlist</a></li>
-->
