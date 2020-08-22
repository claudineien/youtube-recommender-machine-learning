<h4>Objetivo : Desenvolver um recomendador de vídeos do youtube
    <p>Nivel Conhecimento : Intermediário à avançado<br>
    Tipo Machine Learning : Supervisionado</p>
    <p><a href="blank_">[En]</a> | <a href="blank_">[Pt-Br]</a></p>
</h4>
<h1 align='center'>CURVA ROC</h1>
<h3>RECEIVER OPERATOR CHARACTERISTIC</h3>
<p>Auxiliar o pesquisador a encontrar o melhor ponto de corte no score de determinados classificadores machine learning sob determinados grupos que estão sendo analisados.<br><br>
Importante que o dataset seja o mesmo utilizado em todos os classificadores machine learning.<br><br>
Perguntas que a curva ROC deve responder :<br>
<ol>
    <li>A partir de qual score no classificador machine learning é possível classificar corretamente o alvo desejado ?</li>
    <li>Qual a proporção de alvos corretamente classificados ?</li>
</ol>
<p>
Também auxilia a explicar a escolha de determinado classificador machine learning do ponto de vista científico-técnico.</p>
Dois termos a observar :<br>
<table>
    <thead>
    <tr>
        <th>Termo</th>
        <th scope="col">Definição</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td scope="row">Sensibilidade</td>
        <td>Probabilidade do alvo ser corretamente classificado. A classificação do classificador machine learning confirma a classificação real. Significa que o classificador é sensível para classificar o alvo desejado.</td>
    </tr>
    <tr>
        <td scope="row">Especificidade</td>
        <td>Probabilidade do não alvo ser corretamente não classificado. A classificação do classificador machine learning confirma a classificação real.</td>
    </tr>
    </tbody>
</table>
<p><strong>Importante :</strong> É raridade em uma mesma classificação, obter 100% de sensibilidade e 100% especificidade.
</p><br>
<p>Fontes de erro :<br>
Falso Positivo : Na classificação real o Alvo é falso, mas para o classificador machine learning o Alvo é verdadeiro.<br>
Falso Negativo : Na classificação real o Alvo é verdadeiro, mas para o classificador machine learning o Alvo é falso.
    <table>
        <thead>
        <tr>
            <td><td>
            <td></td>
            <td colspan="2"><strong>Classificação Real</strong></td>
        </tr>
        <tr>
            <th></th>
            <th></th>
            <th></th>
            <th scope="col">Alvo</th>
            <th scope="col">Não-Alvo</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <th>Classificação</th>
            <th></th>
            <td scope="row">Alvo</td>
            <td><strong>Verdadeiro Positivo</strong></td>
            <td>Falso Positivo</td>
        </tr>
        <tr>
            <th>Machine Learning</th>
            <td></td>
            <td scope="row">Não-Alvo</td>
            <td>Falso Negativo</td>
            <td><strong>Verdadeiro Negativo</strong></td>
        </tr>
        </tbody>
    </table>
</p>
<p>O <strong>modelo machine learning ideal</strong> será quando a proporção entre falso negativo e falso positivo for a menor possível e quando o acerto do verdadeiro positivo e verdadeiro negativo for a maior possível.</p>
<br>
<hr>
<p><strong>roc_auc_score()</strong><br>
    todos os elementos positivos e as probabilidades de serem  positivos ou não<br>
    todos os elementos negativos e as probabilidades de serem negativos ou não<br>
    o score de um elemento probabilidade positivo é maior
    que o elemento probabilidade negativo = True<br>
    o score de um elemento probabilidade positivo é maior
    que o elemento probabilidade negativo = False<br>
    calcular a média dos resultados valores True e False<br>
<strong>Pergunta e resposta :</strong><br>
    Average precision:  média ponderada de cada precisão, usando como peso a precisão anterior.
    AUC: É a área sobre a curva ROC (TP x FN)
    Resposta : As duas são AUC (área sob a curva), o que muda é a curva. Uma é a curva de precision-recall (average_precision, AUPRC) e a outra é a curva ROC (roc_auc_score, ROC-AUC)
</p>

<p><strong>Aprender mais :</strong><br>
<a href="https://qastack.com.br/stats/51275/what-is-the-difference-in-what-aic-and-c-statistic-auc-actually-measure-for-mo">AIC e a c-estatística (AUC)</a><br>
<a href=""> A</a><br>
<a href=""> B</a><br> 
<a href=""> C</a><br>
<a href=""> D</a><br>
</p>


<hr>
<h3>LIMPAR E TRANSFORMAR DADOS</h3>
    <ul>
        <li>Extrair apenas a data de uma coluna tipo objeto, com strings e datas</li>
		<li>Extrair apenas o número de uma coluna tipo objeto, com strings e número (*2)</li>
        <li>Aplicar Features - Tratamentos específicos nos dados</li>
        <li>Plotar - Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
    </ul>


<p><strong>Dica :</strong><br>
Formatação de datas : Fique atento à formatação de datas de português para inglês ou vice-versa<br>
Número : O local do ponto em português é diferente do inglês<br>
Transformar Data em valor numérico : O formato número é mais eficiente aos algoritmos machine learning<br>
Modelo ml x Realidade : Para melhor eficiência do modelo machine learning os dados de treino e de teste devem ser o mais semelhantes possível a rotina da realidade em uma empresa ou em uma pesquisa de campo<br>
Métrica realística : Encontrar características iguais entre os dados, ainda que seja necessário converter quantidade de dados x por ano em por dia. Ex : Upload de vídeos por dia, visualizações por dia ou algo semelhante.
</p>

<p><strong>Nota :</strong><br>
(*1) Você pode colocar o nome que quiser, foi escolhido Y para padronizar o ensinamento<br>
(*2) Observar que a função fillna() serve para evitar que o conteúdo nan (considerado nulo) continue na coluna. Este atrapalha a eficiência do modelo machine learning.<br>
</p>

<hr>
<h3>PLOTAR - EXIBIR DADOS EM GRÁFICO</h3>
    <ul>
        <li>Exibir dados em gráfico para auxiliar na análise da limpeza e/ou tratamento dos dados</li>
        <li>Permite analisar os dados para desenhar o melhor cenário de para o modelo machine learning</li>
    </ul>
<p>A amostra por data, indica que no final do período há muito mais vídeos, provavelmente a busca do youtube faz seleção aleatória específica, desobedecendo a instrução de ordem estabelecida ao <a href="https://github.com/claudineien/youtube-recommender-machine-learning/blob/master/0_dataset_collect_clean.md">COLETAR DATASET</a>, deixando a maior quantidade dos vídeos por último.</p>
<p>O pico de vídeos do final do período é um fator de atenção e que deve ser melhor analisado em um ambiente machine learning real.</p>
</p>

<hr>
<h3>MODELO MACHINE LEARNING</h3>
Este primeiro modelo será para analisar rapidamente a influência da predição do modelo machine learning com duas features. Utilizaremos a Decision tree (Árvore de decisão).
    <ul>
        <li>Separar dados de treino e dados de teste - Aplicar validação temporal por ser uma time series</li>
        <li>Executar o algoritmo Decision tree</li>
        <li>Treinar modelo machine learning (*3)</li>
        <li>Executar a probabilidade da Decision tree (*4)</li>
        <li>Aplicar a métrica de média de precisão (*5)</li>
        <li>Tratar o ranking dos vídeos (*5)</li>
        <li>Aplicar a curva <a href="blank_">ROC</a></li>
        <li>Exibir a Decision tree para analisar o modelo</a></li>
    </ul>

<p><strong>Aprender mais :</strong><br>
<a href="​https://www.youtube.com/watch?v=Y1XAP6omGzo">Entendiendo las Curvas ROC</a><br>
<a href="blank_">ROC</a>
</p>

<br>
<p><strong>Dica :</strong><br>
50% para treino e 50% para teste : Por ser uma time series, é quase 100% certeza que os dados de treino serão diferentes dos dados de validação, e a metodologia mais eficiente é dividir os dados o mais próximo possível de 50%<br>
Arvore de decisão : Uma das melhores maneiras de entender a relação das features (recursos) com o target (alvo)<br>
</p>

<p><strong>Nota :</strong><br>
(*3) Há bibliotecas com métodos para separar os dados de treino e os dados de teste, que pode ser em percentual e/ou em quantidade<br>
(*4) A probabilidade mostra o valor provavel de positivo 1-vídeos que quer assistir e/ou negativo 0-vídeos que não quer assistir. Queremos somente a probabilidade de ser 1.<br>
(*5) Métrica de média de precisão : utilizado o método average_precision_score, que será nosso baseline, e seja qual for o modelo machine learning a average_precision deve ser o mais próximo possível de 1.0. Esta serve para melhor visualizarmos o ranking dos vídeos : dos mais interessantes para os menos interessantes
</p>

<h3>INTERPRETAR A DECISION TREE</h3>
<p>Uma boa forma de entender como o as features (recursos) estão se relacionando com o target (alvo)
    <ul>
        <li> ul li</li>
    </ul>
</p>
<h4> h4 </h4>
<p> p </p>



```
    average_precision_score
    Métrica de média de precisão : seja qual for o modelo machine learning a average_precision deve ser o mais próximo possível de 1.0.

    Em cada ponto de corte definido ao calcular precision e recall aparecerá uma curva, a área sobre a curva é a average precision

    Precision : é o número que responde a pergunta de todos os modelos que disse que são positivos, 50% destes são realmente positivos
    Recall : é taxa de detecção, isto é, de todos os modelos que disse que são positivos quanto o modelo realmente previu como positivos ?

```

<h4> h4 </h4>
<p> p </p>
<p> p
    <ul>
        <li> li </li>
        <ul> ul
            <li> li </li>
        </ul>
    </ul>
</p>

<p> p 
    <ol> ol
        <li> li </li>
    </ol>
</p>

<h3> h3 </h3>
<p> p </p>

<h4> h4 </h4>
<p> p </p>
<p> p
    <ul> ul
        <li> li </li>
    </ul>
</p>


<br>
<hr>
<p>Fontes :
    <ul>
        <li><a href="https://curso.mariofilho.com/">   
        Curso Solução Completa de Data Science - Instrutor Mario Filho-Kagle Gran Master</a></li>
        <li><a href="https://www.youtube.com/watch?v=NbnVfpRJNp0">CURVA ROC</a></li>
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
