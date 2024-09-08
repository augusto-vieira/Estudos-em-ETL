## Descrição dos Requisitos dos Dados

Com base no levantamento de requisitos, é possível construir um catálogo de dados que descreva em detalhes as necessidades específicas para o processo de ETL.

>No caso específico deste hands-on, vamos supor que o Cientista de Dados e outras partes interessadas do seu time tem como objetivo prever a média mensal do preço do petróleo bruto do IPEA, assim como usar essse dado como variáveis preditoras em outros modelos e análises. Para isso, os seguintes campos com os respectivos tipos foram solicitados. Ainda foi pedido para que os dados do mês vigente não sejam calculados.

Dado o levantamento de requisito da tabela final, foi documentado o seguinte dicionário de dados, alinhando os nomes dos campos na tabela, sua descrição e tipagem dos dados.

|Nome da Variável |	Descrição | Tipo de Dado| Formato|
| ------------- | ------------| ------------| ------ |
|ano | Ano da observação | Integer |integer|
| mes |	Mês daobservação | Integer integer|
| preco_medio_usd |	Média mensal do preço do petróleo bruto| Decimal | decimal(5,2)|
| lag_1_mes_preco_medio_usd | Defasagem de 1 mês   da média  mensal do preçodo petróleo| Decimal | decimal(5,2)|
| lag_2_mes_preco_medio_usd | Defasagem de 2 meses da média mensal do preço do petróleo | Decimal |	decimal(5,2)|
| lag_3_mes_preco_medio_usd | Defasagem de 3 meses da média mensal do preço do petróleo | Decimal |	decimal(5,2)|
| lag_4_mes_preco_medio_usd | Defasagem de 4 meses da média mensal do preço do petróleo | Decimal |	decimal(5,2)|
| lag_5_mes_preco_medio_usd | Defasagem de 5 meses da média mensal do preço do petróleo | Decimal |	decimal(5,2)|
| lag_6_mes_preco_medio_usd | Defasagem de 6 meses da média mensal do preço do petróleo | Decimal |	decimal(5,2)|
| media_movel_6_meses_preco_medio_usd | Média móvel dos últimos 6 meses do preço dopetróleo	Decimal| decimal(5,2)|
| desvio_padrao_movel_6_meses_preco_medio_usd| Desvio padrão móvel dos últimos 6 meses | Decimal | decimal(5,2)|
| valor_minimo_6_meses_preco_medio_usd |Valor mínimo dos últimos 6 meses | Decimal| decimal(5,2)|
| valor_maximo_6_meses_preco_medio_usd | Valor máximo dos últimos 6 meses| Decimal|	decimal(5,2)|
| trimestre | Trimestre da observação| Integer | integer|

## Dados do IPEA
### Overview
O Instituto de Pesquisa Econômica Aplicada (IPEA) disponibiliza uma vasta gama de dados econômicos que podem ser utilizados para análise e previsão de séries temporais. Este case aborda a aplicação de ML para previsão de séries temporais utilizando dados do IPEA.

Nesse case será mostrado na prática como realizar engenharia de features através de um processo de ETL.

Há disponível uma biblioteca do python para acessar dados de séries temporais do IPEA o qual será usado nesse case: https://pypi.org/project/ipeadatapy/

A série temporal que será utilizada será de preço por barril do petróleo bruto Brent (FOB) com código EIA366_PBRENT366, é uma série temporal com dados diários desde 04/01/1986.

## Pipeline do ETL
![Pipeline-ETL]()

`Extract`: dados brutos do petróleo, obtidos pela biblioteca 'ipeadatapy', carregados em um DataFrame do PySpark. Os dados obtidos são persistidos em formato **Parquet** na camada `RAW`.

`Transform`: registros com valores ausentes em "VALUE(US$)", são removidos para garantir a integridade dos cálculos. Em seguida, os dados são agrupados por ano e mês, para calcular a média mensal do preço do petróleo bruto. A seguir, os dados do mês corrente são excluídos para evitar distorções em análise ou previsões. Além disso,`Lags` (defasagens) de até 6 meses são criadas para capturar a dependência temporal, e estatísticas móveis, como média, desvio padrão, valor mínimo e máximo dos últimos 6 meses, são calculadas. Componentes sazonais, como trimestre, também são extraídos para melhor representar as variações temporais no modelo.

`Transform`: os dados transformados e enriquecidos são preparados para uso em análise ou modelagem de ML. O DataFrame final, contendo todas as features necessárias, é salvo em formato **Parquet** na camada `final`. Esta etapa visa garantir que os dados estejam prontos para serem consumidos por outras aplicações ou processos, proporcionando um formato eficiente e otimizado para consultas e processamento adicional.

## Importante
Recomenda-se dividir os dados em cada etapa do processo, permitindo a extração e a verificação de qualidade (Data Quality) em cada fase. Isso é essencial, pois, se for necessário reprocessar alguma informação, você poderá refazer apenas a parte específica. Uma boa prática é utilizar partições diárias para facilitar o controle e o reprocessamento.

## ETL com  PySpark
Neste projeto, as features da tabela serão obtidas conforme os requisitos definidos pelos stakeholders(interessados), utilizando PySpark.

PySpark é uma interface em Python para o Apache Spark, uma poderosa ferramenta de computação distribuída usada para processar grandes volumes de dados de forma eficiente, especialmente em clusters. PySpark oferece várias bibliotecas que facilitam essas operações. Aqui, utilizaremos o DataFrame do PySpark, que simula os DataFrames do Pandas, sendo uma abstração para dados estruturados, mas otimizada e distribuída para lidar com grandes volumes de dados.









