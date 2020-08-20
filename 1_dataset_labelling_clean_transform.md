<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>
<h3>LABELLING</h3>
<p>Abrir o arquivo <a href="blank_">raw_data_sem_labels.csv</a> no excel, criar a coluna Y (*) e nesta coluna inserir o número 0 nas linhas cujo título do vídeo não interesse e não quer assistir ou inserir 1 nas linhas cujo vídeo seja interessante e quer assistir.</p>
<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
    <ul>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (**)</li>
        <li> - </li>
        <li> - </li>
        <li> - </li>
    </ul>

<p><strong>Aprender mais :</strong><br>
<a href="​https://strftime.org/">Tabela de códigos para converter strings em datas no Python</a><br>
<a href="http://gskinner.com/RegExr/">Testador de expressões regulares</a>
</p>

<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : Local do ponto em português é diferente do inglês</p>

<p><strong>Nota :</strong><br>
(*) Você pode colocar o nome que quiser, foi escolhido Y para padronizar o ensinamento<br>
(**) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) seja gravado</p>

<h3> H3 </h3>
<p> - </p>
<p> - 
    <ul>
        <li>Exibir apenas os vídeos que eu vou gostar</li>
		<li>Criar Solução com Hanking dos vídeos que primeiramente eu vou gostar seguido dos que eu menos vou gostar</li>
        <li>Estabelecer uma abordagem de ponto corte : Retornar apenas 3 que eu vou gostar</li>
        <li>Abordagem de ranking : ordenar dos vídeos eu mais vou gostar aos que eu menos vou gostar</li>
        <li>Consultará pelas seguintes palavras chave : machine-learning, kaggle, datascience</li>
    </ul>
</p>
<h4>COMO A SOLUÇÃO SERÁ USADA PRODUTIVAMENTE ?</h4>
<p>O Cientista de dados analisa o resultado retornado, como este resultado será apresentado e define como devem ser tratados os novos dados.</p>
<p>O resultado pode ser apresentado em um Web app, ERP system, Dashboard, Excel, etc...</p>
<p>Em primeiro momento é responsabilidade do Cientista de dados definir como a solução será usada produtivamente. Após ter o modelo definitivo o Cientista de dados com o time de negócios estabelecem como a solução será usada definitivamente em produção.</p>
<p>Em nosso projeto : criaremos um Web App com os vídeos (links) e as previsões ordenadas e com os seguintes dados : Título, Label, Anotações, Descrição</p>
<h4>COMO SABER SE A SOLUÇÃO DEU CERTO ?</h4>
<p>O Cientista de dados define as métricas de acordo com a área de negócio e dados obtidos, então compara os resultados entre solução machine learning e os resultados atualmente conquistados sem machine learning.</p>
<p>Deve haver uma métrica primária e uma ou mais métricas secundárias.</p>
<p>Em nosso projeto :
    <ul>
        <li>A métrica primária será : Top N vídeos incluo na lista watch later</li>
		<li>As métricas secundárias podem ser :</li>
        <ul>
            <li>Quantidades N de vídeos assistidos até o final</li>
            <li>Tempo X investido selecionando os vídeos recomendados por Machine Learning</li>
            <li>Os top N recomendados por Machine Learning são mais assistidos do que os top N da busca google ? : [YES] [NO]</li>
        </ul>
    </ul>
</p>
<p>Importante :<br>
Definir um problema ja resolvido diversas vezes e a melhor solução à este problema com etapas rápidas e digamos "imperfeitas" é a melhor forma de sairmos do estado zero.</p>
<p>Cientista de dados deve considerar que :
    <ol>
        <li>Passos 01 e 02 : serve para entender todo o processo do negócio, para definir o problema e a melhor solução.
        </li>
        <li>Passos 03 e 04 : serve para desenvolver o modelo machine learning sob os processos e métricas do negócio.
        </li>
        <li>Passo 05 : serve para testar o modelo machine learning desenvolvido sob os processos e métricas do negócio e disponibilizá-lo em produção.
        </li>
    </ol>
</p>

<h3>COLETAR E TRABALHAR OS E/OU NOS DADOS</h3>
<p>Nesta etapa o Cientista de dados aplicará todas as técnicas para tornar os dados em perfeita conformidade ao modelo de predição que será desenvolvido</p>

<h4>COLETAR OS DADOS</h4>
<p>Os dados podem ser coletados das seguintes fontes :</p>
<p>
    <ul>
        <li>banco de dados relacional e estruturado</li>
        <li>banco de dados NoSQL</li>
        <li>buscando na internet (scraping)</li>
        <li>de imagens</li>
        <li>de emails</li>
        <li>com as pessoas envolvidas no processo</li>
        <li>planilhas excel</li>
        <li>redes sociais</li>
        <li>sensores</li>
        <li>documentos word/pdf e similares</li>
    </ul>
</p>

<h4>ANALISAR E EXPLORAR OS DADOS</h4>
<p>
    <ul>
        <li>detectar se há os dados que precisa para desenvolver a solução</li>
        <li>analisar o tipo de cada dado : string, objeto, float, inteiro</li>
        <li>analisar o conteúdo de cada dado</li>
        <li>analisar a correlação entre os dados</li>
        <li>Detectar padrões entre os dados</li>
        <li>Detectar tendências entre os dados</li>
    </ul>
</p>

<h4>LIMPAR OS DADOS</h4>
<p>
    <ul>
        <li>remover dados redundantes</li>
        <li>trabalhar nos dados faltantes</li>
        <li>trabalhar nos dados duplicados</li>
        <li>trabalhar nos dados desnecessários</li>
    </ul>
</p>

<h4>CONVERTER OS DADOS</h4>
<p>
    <ul>
        <li>de objetos para data</li>
        <li>de objetos para string</li>
        <li>de data para string</li>
        <li>categóricos para numéricos</li>
    </ul>
</p>

<h4>ANALISAR E EXPLORAR OS DADOS</h4>
<p>
    <ul>
        <li>Detectar padrões entre os dados</li>
        <li>Detectar tendências entre os dados</li>
    </ul>
</p>

<h4>MODELAR OS DADOS</h4>
<p>Nesta fase o Cientista de dados separa seu conjunto de dados nas seguinte proporções :</p>
<p>
    <ul>
        <li>Uma proporção para treinar o modelo, conhecido como conjunto de dados de treino</li>
        <li>Uma proporção para testar a eficiência do modelo, conhecido com conjunto de dados de teste</li>
    </ul>
Nesta fase o modelo de dados esta sendo contruÍdo pelo conjunto de dados de treino e sendo evoluÍdo pelo conjunto de dados de teste.
</p>

<h3>OTIMIZAR E IMPLANTAR</h3>
<p>Esta fase serve para melhorar a eficiência do modelo de dados, e realizar mais predições acuradas.</p>
<p>O objetivo final é implantar o modelo de dados em ambiente de validação ou em ambiente de produção para aceitação dos usuários</p>
<p>Os usuários deverão testar o desempenho dos modelos de dados e verificar se há qualquer inconsistências com os modelos, que serão corrigidos pelo Cientista de dados.</p>
<br><br><br><br><br>
<hr>
<p>Fontes :
    <ul>
        <li><a href="https://curso.mariofilho.com/">   
        Curso Solução Completa de Data Science - Instrutor Mario Filho-Kagle Gran Master</a></li>
    </ul>
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