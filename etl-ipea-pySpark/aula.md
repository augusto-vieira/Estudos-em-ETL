## ETL

Começa com o desenvolvimento de **ETL** com dados do IPEA para para obtenção de features para um modelo de Machine Learning a luz da cultura MLOps.

![ETL-1](https://www.itigocloud.com/consulting/wp-content/uploads/sites/2/2019/08/Arquitetura-BI.jpg)

![ETL-2](https://ix-cdn.b2e5.com/images/208444/208444_30e22a1f13434888a1e7b330d0bf087f_1600957198.png)
>

`Extract`: coleta de dados de diferentes fontes, como bancos de dados, APIs, arquivos de log, entre outros.

`Transform`: processamento e limpeza dos dados para estarem em um formato adequado para análise. Isso pode incluir a normalização, agregação e engenharia de features.

`Load`: inserção dos dados processados em um sistema de armazenamento centralizado (DB, Data Lake), como um data warehouse (DW),  onde podem ser utilizados para treinamento de modelos de ML.

## A Importância do ETL em Machine Learning

`Qualidade dos Dados`: dados brutos contêm geralmente ruídos, inconsistências e valores ausentes. O ETL ajuda a limpar e transformar esses dados para garantir que os modelos de ML recebam informações de alta qualidade.

`Engenharia de Features`: o ETL permite a criação de features derivadas essenciais para melhorar o desempenho dos modelos de ML. Por exemplo, em dados de séries temporais, o ETL pode ser utilizado para gerar features como médias móveis, desvios padrão e outras estatísticas relevantes.

`Fonte Única da Verdade`: o ETL serve como uma ferramenta para consolidar dados de diversas fontes em uma única base coerente e confiável. Isso garante que todos os stakeholders e processos de negócio estejam baseados na mesma versão dos dados, facilitando a consistência e a integridade das análises e decisões.

## Cultara MLOps
`Design`: levantamento de requisitos de negócio, o problema a ser resolvido. Regras aplicadas nos dados, de modo que eles estejam preparados para consumo. Análise preliminar dos dados disponíveis, ter uma intuição do que vai fazer na fase de desenvolvimento.
`Model Development`: parte de engenharia de dados, modelos de ML, modelos de teste e validação.

Com os modelos de dados treinados e pipe line de ML desenvolvida, entramos no `Ciclo de Operations`, onde implementamos Deployment, CI/CD Pipelines, Monitoring & Triggering.

## Encadeamente de ETL
O ETL de um dado, pode ser um RAW de outro.


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

