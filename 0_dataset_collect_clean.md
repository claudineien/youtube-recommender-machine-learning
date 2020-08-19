<h3>COLETAR DATASET DE VÍDEOS DO YOUTUBE E FAZER ALGUNS AJUSTES</h3>
<p>O notebook <a href="">dataset_collect_clean.ipynb</a> possui a documentação e explicações de como :
    <ul>
        <li>coletar os dados do youtube </li>
        <li>armazenar os dados em um dataframe da biblioteca pandas</li>
        <li>fazer alguns ajustes para melhor uso pelo modelo de predição</li>
        <li>preparar dataset para labelling</li>
    </ul>
</p>
<p>Dica : Baixar algumas amostras, e analisar se o conteúdo dos dados é suficiente para desenvolver a solução</p>

<p>Bibliotecas utilizadas :
    <ul>
        <li><a href="https://www.crummy.com/software/BeautifulSoup/bs4/doc/">BeautifulSoup4</a> : biblioteca python para puxar dados de uma página html e de arquivos xml e fazer o parsing (*)</li>
        <li><a href="https://requests.readthedocs.io/pt_BR/latest/user/quickstart.html">Requests</a> : é uma biblioteca HTTP para Python simples e elegante, feita para seres humanos</li>
        <li><a href="https://requests.readthedocs.io/pt_BR/latest/user/quickstart.html">youtube_dl</a> : é uma biblioteca HTTP para Python simples e elegante, feita para seres humanos</li>
    </ul>
    <p>Instalar biblioteca BeautifulSoup4 : pip install beautifulsoup4</p>
    <p>Instalar biblioteca Requests : pip install requests</p>
    <p>Instalar biblioteca youtube-dl : pip install youtube_dl</p>
    <p>(*) Biblioteca substituída em 01/07/2020 pela biblioteca youtube_dl</p>
</p>

<p>Importante :<br>
O notebook <a href="">dataset_collect_clean.ipynb</a> gerará o arquivo <a href="">raw_data_sem_label_youtube-dl.csv</a>.<br>
Mas por conta da quantidade muito limitada que a biblioteca youtube_dl permite baixar, esta disponibilizado os arquivos raw_data_sem_labels.csv e raw_data_with_labels.csv com mais informações para conseguir executar os treinamentos e testes do modelo machine learning</p>
<!--<p> - </p>-->
