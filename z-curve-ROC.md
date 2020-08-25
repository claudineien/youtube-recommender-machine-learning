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
            <td colspan="2"><td>
            <td colspan="2"><strong>Classificação Real</strong></td>
            <td></td>
        </tr>
        <tr>
            <th></th>
            <th></th>
            <th scope="col">Alvo</th>
            <th scope="col">Não-Alvo</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <th>Classificação</th>
            <td scope="row">Alvo</td>
            <td><strong>Verdadeiro Positivo</strong></td>
            <td>Falso Positivo</td>
        </tr>
        <tr>
            <th>Machine Learning</th>
            <td scope="row">Não-Alvo</td>
            <td>Falso Negativo</td>
            <td><strong>Verdadeiro Negativo</strong></td>
        </tr>
        </tbody>
    </table>
</p>
<p>O <strong>modelo machine learning ideal</strong> será quando a proporção entre falso negativo e falso positivo for a menor possível e quando o acerto do verdadeiro positivo e verdadeiro negativo for a maior possível.</p>
<p>Importante saber que ao aumentar a sensibilidade perde-se na especificidade e vice-versa.</p>
<br>
<img src=".\notebook\dados_brutos\grafico_roc.png">
<br>
<p>
NÃO ALVO = Dados que não interessa<br>
ALVO = Dados que interessam<br>
ESCORE = É a escala de medida<br>

</p>
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
<br>
<hr>
<p>Fontes :
    <ul>
        <li><a href="https://curso.mariofilho.com/">   
        Curso Solução Completa de Data Science - Instrutor Mario Filho-Kagle Gran Master</a></li>
        <li><a href="https://www.youtube.com/watch?v=NbnVfpRJNp0">CURVA ROC</a></li>
    </ul>
</p>

<hr>
<h3> h3 </h3>
    <ul>
        <li> li </li>
    </ul>


<p><strong>Dica :</strong><br>
p
</p>

<p><strong>Nota :</strong><br>
p
</p>

<hr>
<h3> h3 </h3>
    <ul>
        <li> li </li>
    </ul>
<p> p 
</p>

<hr>
<h3> h3 </h3>
    <ul>
        <li> li </li>
    </ul>

<p><strong>Aprender mais :</strong><br>
<a href="​https://"> link</a><br>
</p>

<br>
<p><strong>Dica :</strong><br>
p
</p>

<p><strong>Nota :</strong><br>
p
</p>

<h3> h3 </h3>
<p> p 
    <ul>
        <li> ul li</li>
    </ul>
</p>
<h4> h4 </h4>
<p> p </p>

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
<p> - = - + + : > < { [ * & % $ # @ ! } ]</p>-->
