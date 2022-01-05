# Desafio Pismo - Data Engeneering

<h2>Desafio proposto:</h2>

O desafio é criar uma solução para que consuma os arquivos disponibilizados e seguindo as regras de contrato, faça a tratativa de garantir que sempre seja o arquivo mais atual e que não haja nenhuma duplicidade.

<h3>(E)xtract:</h3>

&emsp;&emsp;● Como origem dos dados está sendo usado um diretório públco no <b>Amazon S3 Bucket</b>, onde os arquivos enviados foram inseridos

<h3>(T)ransform:</h3>
&emsp;&emsp;● Na parte de tratar os dados, está sendo usado o Databricks por já ter <b>python</b> e também ser possível usar <b>pyspark</b> de forma nativa
&emsp;&emsp;● No tratamento dos dados, foi identicado que os arquivos <b>JSON</b> estava fora da formatação padrão, sendo assim primeiramente os arquivos foram lidos como <b>texto</b> para que se fosse possível fazer alterações via <b>replace</b> para não termos mais esse impeditivo de formatação<br>
&emsp;&emsp;● Após a tratativa da formatação, foi-se aplicado uma correção no campo <b>timestamp</b>, pois foi identificado que em alguns registros o campo (até então em formato de texto) estava com a letra "T" e outros não, sendo assim foi normalizado esses registros<br>
&emsp;&emsp;● Em seguida o mesmo campo de <b>timestamp</b> foi convertido para o tipo de dados correto, sendo assim, possibilitando o uso dele como um campo de data<br>
&emsp;&emsp;● Seguindo a regra do contrato, proposto no desafio, o campo <b>event_key</b> é a junção de duas colunas: <b>"domain"</b> e <b>"event_type"</b>. Caracterizando-se assim como uma chave de tipo de evento</b><br>
&emsp;&emsp;● Finalizando a parte de tratamento dos dados, a regra aplicada no agrupamento dos dados, para trazer o <b>MAX(timestamp)</b> sendo assim, irá trazer o último e também irá remover os duplicados


<h3>(L)oad:</h3>
&emsp;&emsp;● Para concluir, os arquivos tratados anteriormente estão sendo escritos em um diretório público, também no <b>Amazon S3 Bucket</b> em formato <b>.parquet</b> e de forma particionada por: <b>"event_key"</b>, <b>"year"</b>, <b>"month"</b> e <b>"day"</b>

<h3>Como Usar:</h3>
Para que todos consigam usar a resolução do desafio, no repositório está sendo disponibilizado dois arquivos, um referente ao notebook e o outro referente ao ambiente no Databricks, para que seja possível testar o código é simples, basta importar os arquivos no ambiente do Databricks e executar.
