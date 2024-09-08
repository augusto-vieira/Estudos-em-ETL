## Conteúdo Estudado

### Glossário
``RAW``: Dados em sua forma bruta, sem processamento ou transformação.

`Dataframe`: Estrutura de dados bidimensional em forma de tabela, usada em ferramentas como Pandas e PySpark para manipular dados.

`Pandas`: Biblioteca Python usada para manipulação e análise de dados estruturados, geralmente utilizando DataFrames.

`PySpark`: Interface para usar o Apache Spark com Python, permitindo processamento distribuído de grandes volumes de dados, frequentemente utilizando DataFrames para lidar com grandes datasets.

`Data Quality`: Refere à precisão, completude, consistência, validade dos dados. Essencialmente, garante que os dados sejam confiáveis e úteis para ser usado em ferramentas de análise.

`Drop Duplicate (SQL)`: Comando SQL utilizado para remover registros duplicados em uma tabela, ajudando a melhorar a qualidade dos dados.

`Função Row Over (SQL)`: Função de janela SQL que realiza cálculos em subconjuntos de dados, útil para analisar e comparar registros dentro de um grupo de dados sem perder o contexto.

`Lag (defasagens)`: Diferença temporal ou atraso entre eventos, usada em análises temporais, frequentemente em conjunto com funções de janela SQL.

`Partição (SQL)`: Técnica para dividir grandes tabelas em partes menores, otimizando consultas em bancos de dados e facilitando o processamento de grandes volumes de dados.

`Parquet`: Formato de arquivo colunar que otimiza o desempenho e eficiência no processamento de grandes volumes de dados, especialmente útil em sistemas distribuídos como PySpark.

`Pipeline`: Conjunto de etapas automatizadas para processar e mover dados entre sistemas, geralmente envolvendo transformação e armazenamento de dados.

`Data Warehouse (DW)`: Sistema que armazena dados estruturados, usado para análises e relatórios em larga escala, com dados muitas vezes coletados e transformados por pipelines.

`Data Lake`: Repositório centralizado para armazenar dados em sua forma bruta (RAW), estruturados ou não, permitindo o processamento posterior e a integração com outras ferramentas.

`Data LakeHouse`: Arquitetura que combina elementos de Data Lakes e Data Warehouses, permitindo armazenar dados brutos e estruturados em um único local, otimizando análise e armazenamento.

`S3 (AWS)`: Serviço de armazenamento de objetos escalável da AWS, utilizado como Data Lake para armazenar grandes volumes de dados brutos.

`Amazon Athena (AWS)`: Serviço que permite consultar dados diretamente no S3 usando SQL, facilitando análises rápidas de dados armazenados em Data Lakes.

`Glue (AWS)`: Serviço de ETL (Extract, Transform, Load) gerenciado da AWS, que prepara e transforma dados armazenados em S3 para serem analisados ou carregados em outros sistemas, como Data Warehouses.

`Redshift (AWS)`: Serviço de Data Warehouse em nuvem da AWS, otimizado para análises de grandes volumes de dados estruturados, frequentemente alimentado por dados processados via Glue.

`Serverless`: Modelo de computação em que a infraestrutura é gerenciada automaticamente, como no caso de serviços como Athena e Glue, permitindo que os usuários se concentrem nas funções de processamento de dados sem se preocupar com servidores.

`Clusters`: Conjunto de máquinas que trabalham juntas para processar grandes volumes de dados, comuns em serviços como Redshift e PySpark para aumentar a capacidade de processamento.

`Filegroup`: Estrutura usada no SQL Server para organizar grupos de arquivos de banco de dados, facilitando o gerenciamento e a recuperação de dados particionados.

`Stakeholders`: Pessoas ou grupos com interesse em um projeto, como gerentes de dados, analistas e equipes de TI, que dependem do uso de ferramentas como Data Warehouses e Pipelines para tomadas de decisão.

`Canvas (AWS)`: Interface gráfica do AWS Amplify usada para criar e visualizar fluxos de trabalho, ajudando a simplificar o desenvolvimento de aplicações na nuvem, especialmente aquelas que utilizam diferentes serviços de dados.

## Partição
>Em bancos de dados e SQL, uma partição é uma técnica usada para dividir uma tabela grande em partes menores e mais gerenciáveis, com o objetivo de melhorar o desempenho das consultas e a organização dos dados. Cada partição é tratada como uma unidade separada, mas ainda faz parte da tabela original.

>No contexto de dados colunares, a partição refere-se ao armazenamento de dados em colunas, ao invés de linhas. Quando você cria uma partição, essa partição se torna uma coluna de índice, ajudando a segmentar e distribuir os dados para otimizar a leitura e escrita. Isso é especialmente útil em tabelas com grandes volumes de dados, pois as consultas podem ser realizadas em partes específicas da tabela, reduzindo o tempo de processamento.

>Além disso, o número de partições pode ser ajustado de acordo com o volume de dados e a arquitetura do banco de dados, mas é necessário ter atenção ao limite máximo de partições para evitar problemas de desempenho.

>Cardinalidade refere-se ao número de valores únicos em uma coluna. Altas cardinalidades, como datas ou IDs únicos, podem gerar muitas partições, prejudicando o desempenho.

![Paricao](https://cloud.google.com/static/bigquery/images/clustering-and-partitioning-tables.png)

Em um **Data Lake**, é comum trabalhar com diferentes categorias de dados com base na sua relevância e frequência de uso: `dado quente`, `dado morno` e `dado frio`.

**Dado quente**: frequentemente acessado e atualizado, por isso precisa de maior desempenho.

**Dado morno**: acessado com menos frequência e pode ser movido para camadas de armazenamento intermediárias.

**Dado frio**: raramente acessado e pode ser armazenado em locais mais baratos e de maior latência.

> Espurgo é o processo de remover ou arquivar dados antigos que não são mais úteis, liberando espaço e mantendo a eficiência do sistema.

> Encadeamente de ETL:
> 
> O ETL de um dado, pode ser um RAW de outro ETL.
