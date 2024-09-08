## Conteúdo Estudado

## Encadeamente de ETL
O ETL de um dado, pode ser um RAW de outro ETL.

## Partição
>Em bancos de dados e SQL, uma partição é uma técnica usada para dividir uma tabela grande em partes menores e mais gerenciáveis, com o objetivo de melhorar o desempenho das consultas e a organização dos dados. Cada partição é tratada como uma unidade separada, mas ainda faz parte da tabela original.

>No contexto de dados colunares, a partição refere-se ao armazenamento de dados em colunas, ao invés de linhas. Quando você cria uma partição, essa partição se torna uma coluna de índice, ajudando a segmentar e distribuir os dados para otimizar a leitura e escrita. Isso é especialmente útil em tabelas com grandes volumes de dados, pois as consultas podem ser realizadas em partes específicas da tabela, reduzindo o tempo de processamento.

>Além disso, o número de partições pode ser ajustado de acordo com o volume de dados e a arquitetura do banco de dados, mas é necessário ter atenção ao limite máximo de partições para evitar problemas de desempenho.

>Cardinalidade refere-se ao número de valores únicos em uma coluna. Altas cardinalidades, como datas ou IDs únicos, podem gerar muitas partições, prejudicando o desempenho.

![Paricao](https://cloud.google.com/static/bigquery/images/clustering-and-partitioning-tables.png)

Em um **Data Lake**, é comum trabalhar com diferentes categorias de dados com base na sua relevância e frequência de uso: dado quente, dado morno e dado frio.

**Dado quente** é frequentemente acessado e atualizado, por isso precisa de maior desempenho.

**Dado morno** é acessado com menos frequência e pode ser movido para camadas de armazenamento intermediárias.

**Dado frio** é raramente acessado e pode ser armazenado em locais mais baratos e de maior latência.
Espurgo é o processo de remover ou arquivar dados antigos que não são mais úteis, liberando espaço e mantendo a eficiência do sistema.
