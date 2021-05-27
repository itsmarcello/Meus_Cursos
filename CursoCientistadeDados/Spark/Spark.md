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


