# Spark

Conceito:
Ferrameta para analise de Big Data
Bom para Dadosm sem estrutura e relações bem definidas (NO SQL)



## Hadoop (HDFS) - Map Reduce
O Hadoop apresenta uma estrutura chamda MapReduce que permite dividir o sue dado em diversos servers e utilizados para realisar as queries. O Mapreduce cuide da parte pesada de comnunicação, admistracão e troca de dados entre os clusters.
* Map = Dados separados pentre Chave- Valor
* Reduce = agrega os valores e gera novos grupos menores a aprtor das regras escolhidas. 
Porem para algoritimos que leem os mesmo dados repedidamente e iteram com eles (ML), pode ser desvantajoso. O Happod é bom para processamenytos em lots. 

O Spark apresneta uma feature semelhante, realizando esses calculosna memoria sendo mais rapido. Ele realiza o processos de RDD (Resilient Distribuited Datasets) tudo na memoria, como uma Machine Virtal do Hadoodp e que armazem em cash os dados do cluster. O Spark é otimo para trabalhos iterativos e lots. 


pypark -> SparkContext - Ciração de RDDS


## Transformações

-> Lazy Evaluation
As operações só são execultadas quando forem realmente necessarias.

* Map 
* flatMap
* filter 
* set - união, interseção 

## Ações

Assim com as df to Pandas, o Spark apresenta suas RDDs. Essas RDDs podem forer transformações e ações. Transformações refazem essa RDD em várias versões dela (lineage), porém ficam aguardando uma ação para serem finalmente executadas. Quando uma ação é executada, as tranformações são feitas e um resultado é gerado. 
Já as ações  

-> Lazy Evaluation
As operações só são execultadas quando forem realmente necessarias.

* Map 
* flatMap
* filter 
* set - união, interseção 

## SPARK SQL 

Bom para dados estruturados vindos de outras fontes de dados. 

Spark Context (pyspark)- > SQL Context (para trabalhar com SQL)
Spakr Session para trabalhr com DataFrames

## SPARK  Streaming 

Bom estudo de streaming de dados. Nao é 100% time, pois trabalha com processamento em pequenos batches, porem ainda é bem rapido. 
Usamos essa ferramenta para:

![image](https://user-images.githubusercontent.com/62761388/120375942-b258c100-c2f1-11eb-818a-e7556c9f218e.png)

![image](https://user-images.githubusercontent.com/62761388/120376018-c3a1cd80-c2f1-11eb-8ded-5a16aeb8c53f.png)


* Batches : ML, criacao de Warehouses, etc
* Streaming : Alimentacao Dashboards online, Internet das coisas, avalicao de fluxos em WebSites, etc.

"Big Data never stops!"



