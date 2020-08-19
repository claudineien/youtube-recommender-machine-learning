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
<!--
<p>labelling</p>
<p>Active learning</p>
feather-format 0.4.1
pip install feather-format
https://pypi.org/project/feather-format/
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>-->
