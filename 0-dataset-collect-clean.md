<h5><a href="blank_">[en]</a> | <a href="blank_">[pt-br]</a></br>
Projeto : Desenvolver Recomendador de vídeos do youtube<br>
Nivel Conhecimento : Iniciante à avançado<br>
Tipo Machine Learning : Supervisionado<br>
LinkedIn : https://www.linkedin.com/in/claudineien/
</h5>

<p>Para entender o funcionamento desta aplicação ler na sequência</p>

<br>
<p>O arquivo 0-dataset-collect-clean.md contém informações sobre o notebook <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0_dataset_collect_clean.ipynb">0_dataset_collect_clean.ipynb</a>
</p>

<p>
A bibioteca <a href="https://youtube-dl.org/">youtube_dl</a> foi escolhida por facilitar a extração de informações sobre o vídeo, gravando-as em um dicionário python.
</p>

<p>Processo mais especial do Cientista de Dados é processo da qualidade dos dados composto por :
    <ul>
        <li>obter o dataset</li>
        <li>extrair a sujeira do dataset</li>
        <li>transformar alguns dados no dataset</li>
        <li>analisar e validar a qualidade do dataser</li>
        <li>carregar o dataset com a qualidade necessária para o modelo machine learning, deep learning e/ou neural networks</li>
    </ul>
</p>

<p>
A qualidade dos dados significa sucesso ao modelo de predição
</p>

<a id="itemtec" >Tecnologias utilizadas neste projeto</a><br>
<em><a href="#itemtec">Tecnologias utilizadas neste projeto</a></em>

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

<!--



-->
