<h1>VISÃO GERENCIAL EM BIG DATA</h1>
<p>A era da informação e conhecimento sempre existiram. Para saber disto basta lembrar de Sócrates 469 a.C, Platão 428 a.C, Aristóteles 384 a.C, entre outros filósofos, matemáticos, físicos, cientitas, escritores, entre outros contribuidores, que contribuiram com milhares de milhares de informações e conhecimentos.</p>
<p>A diferença entre a época dos citados seres humanos e nossa época é que nos últimos 30 anos foram produzidos uma quantidade incomparável de informações e conhecimentos em relação os anteriores últimos 1000 anos, por conta da alta velocidade de propagação</p>
<p>Analisar dados é sobreviver, esta além de ser uma simples atividade</p>
<p>A globalização e competitividade mundial obriga as organizações a serem talentosamente eficientes  na extração de informações e conhecimentos no enorme universo exponencial de dados eletrônicos</p>
<p>O produto do talento eficiente na extração de informações e conhecimento será no mínimo : menos custo, mais vendas, clientes mais satisfeitos, fornecedores mais eficientes, conformidade com órgãos reguladores e conformidade com órgãos fiscalizadores</p>
<p>O PMBOK (2013) define que um projeto é um esforço temporário para produzir um produto ou serviço exclusivo. Um projeto Big Data possui estas mesmas características, e pode gerar resultados por tempo indeterminado.</p>
<p>Um projeto Big Data esta entre os mais complexos e com maiores riscos de todas as indústrias, produzindo algo abstrato, não tangível, envolve muitas estruturas, sistemas, formatos, pessoas e infraestrutura</p>
<p>Um projeto que envolve uma única fonte de dados relacionais para produzir dimensões em um data mart, não pode ser considerado Big Data. </p>
<h4>ENTENDER PROJETO BIG DATA</h4>
<p>Envolve grandes volumes de dados (petabytes, exabytes, até o infinito), velocidade, variedade, veracidade e valor.</p>
<p></p>
<h4>PROJETO BIG DATA</h4>
<p>Um projeto Big Data envolve muitas fontes de dados, os que envolvem poucas deve haver uma desestruturada ou semi-estruturada ou fontes de dados NoSQL, ou volumes de dados além de um projeto tradicional.</p>
<p>O PMBOK registra que nem todos os processos são obrigatórios. Nem aplicarmos aplica-los com a mesma intensidade. Quais processos usar e intensidade aplicar será responsabilidade do gerente do projeto e sua equipe. Os fatores que envolve são: complexidade, novos elementos relacionados, pessoas, tecnologias, dados de origem ou origem dos dados.</p>
<h4>CRIAR PROTÓTIPOS</h4>
<p>
    <ol>
        <li>Baixa complexidade : há experiência prévia e tecnologia madura e testada, talvez seja dispensável um protótipo</li>
        <li>Média complexidade : pouca experiência e com entrega de artefatos de visualização, pode ter protótipos em ferramentas que simulem maquetes de telas</li>
        <li>Grande complexidade : quase sem experiência alguma, pode requerer protótipo funcional para verificar viabilidade e minimizar riscos</li>
    </ol>
</p>
<h4>DIFERENÇA ENTRE PROJETO TRADICIONAL DE ANALISE DE DADOS E PROJETO BIG DATA</h4>
<div style="overflow-x:auto;">
  <table>
    <tr>
      <th>Características</th>
      <th>Projeto Tradicional</th>
      <th>Projeto Big Data</th>
    </tr>
    <tr>
      <td>Veracidade</td>
      <td>Pode demorar semanas ou meses</td>
      <td>Pode ser milhões de vezes mais rápido, e de forma contínua, e com maior índice de acerto</td>
    </tr>
    <tr>
      <td>Valor</td>
      <td>Pode demorar semanas ou meses, para ter certeza se o resultado é positivo ou negativo</td>
      <td>Provavelmente em algumas horas saiba se o resultado é positivo ou negativo</td>
    </tr>
    <tr>
      <td>Velocidade</td>
      <td>Auditoria manual, por amostragem, pode demandar semanas ou meses, definido período para executar</td>
      <td>Com computador o processo é quase todo eletrônico, o mínimo de erro, milhões de vezes mais rápido, e de forma contínua</td>
    </tr>
    <tr>
      <td>Volume</td>
      <td>Construídos em data warehouse, contendo até terabytes de dados</td>
      <td>Construídos em data warehouse e/ou nuvem, a partir de petabyte de dados</td>
    </tr>
    <tr>
      <td>Variedade</td>
      <td>Dados relacionais estruturados, hieráquico ou de rede</td>
      <td>Além do tradicional, incluem dados não estruturados, semi-estruturados : redes sociais, sensores, web, documentos, emails, etc, etc...</td>
    </tr>
    <tr>
      <td>Arquitetura</td>
      <td>Projeto Centralizado em um servidor</td>
      <td>Projeto Distribuído entre servidores</td>
    </tr>
    <tr>
      <td>Crescimento</td>
      <td>Vertical : +memória, +cpu, +servidor</td>
      <td>Horizontal : adicionados data nodes</td>
    </tr>
    <tr>
      <td>Virtualizados</td>
      <td>Normalmente não</td>
      <td>Geralmente Sim</td>
    </tr>
    <tr>
      <td>Tráfego de dados</td>
      <td>Mais dados do servidor ao cliente ou do servidor para fora da empresas</td>
      <td>O maior tráfego é entre os nós dos servidores</td>
    </tr>
    <tr>
      <td>Carga de dados</td>
      <td>Normalmente é realizado após pré-análise e identificação de valor agregado. Os dados são tratados e carregados em repositórios pequenos (para padrões Big Data), para apoiar decisões.</td>
      <td>Geralmente carregam grandes volumes (a partir de petabytes) de dados em um sistema HDFS -Hadoop Distributed File System ou para Serviços Cloud, mesmo sem identificar informação com valor agregado. O nome dado a formação de dados é data lakes (lago de dados). Posteriormente parte destes dados podem ser tranferidos a um tradidional data mart</td>
    </tr>
  </table>
</div>
<p>O gráfico a seguir mostra a relação inversa entre tempo de produção da informação e o valor da informação</p>
<picture>
    <img src=".\vlr-info_x_tempoproduinfo.png" alt="Grafico : Valor Informação x Tempo de produção da Informação">
</picture>
<br>
<h4>DIFERENÇAS NA ESTRUTURA BÁSICA DE SOLUÇÃO DE ANÁLISE DE DADOS</h4>
<div style="overflow-x:auto;">
  <table>
    <tr>
      <th>Elementos</th>
      <th>Análise Tradicional de Dados</th>
      <th>Análise de Big Data</th>
    </tr>
    <tr>
      <td>Fontes de dados</td>
      <td>Normalmente dados relacionais estruturados, hieráquico ou de rede. Alguns casos não estruturados</td>
      <td>Estruturados e não estruturados com enorme quantidade de variedades de fontes de dados</td>
    </tr>
    <tr>
      <td>Carga</td>
      <td>Realizado por um processo de carga, web service ou uma API</td>
      <td>Realizado por um processo de carga, web service ou uma API</td>
    </tr>
    <tr>
      <td>Armazenamento</td>
      <td>Em um banco de dados relacional ou dimensional</td>
      <td>Em sistemas de arquivos distribuídos com HDFS e em bancos de dados NoSQL</td>
    </tr>
    <tr>
      <td>Análise</td>
      <td>Utilizar consultas em linguagem estruturada (Pig Latin ou SQL) ou algorítimo machine learning (aprendizado de máquina) utilizando cubos de decisão</td>
      <td>Utilizar consultas em linguagem estruturada (Pig Latin ou SQL) ou algorítimo machine learning (aprendizado de máquina) utilizam map reduce</td>
    </tr>
    <tr>
      <td>Visualização</td>
      <td>Painéis, relatórios, KPIs, entre outros</td>
      <td>Painéis, relatórios, KPIs, entre outros</td>
    </tr>
  </table>
</div>
<h4>OBJETIVO DO PROJETO BIG DATA</h4>
<p>O objetivo do projeto big data é responder perguntas. E para isto é necessário:</p>
<img src="./triangulobigdata.png" alt="Grafico : Triangulo-Pessoas,Processod,Dados,Tecnologia">

<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>


<a href="https://www.youtube.com/watch?v=B-JmU842t_Q">A HISTÓRIA DA INFORMAÇÃO Documentário 2012</a><br>
<a href="https://www.youtube.com/watch?v=eOrpDa0BH1c">Consumo de informação | Ricardo Cappra, para PUCRS Online</a>
