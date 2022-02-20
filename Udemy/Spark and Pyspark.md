# The largest heading
## The second largest heading
###### The smallest heading

# Spark

## Why Spark 
Criado para lidar com grandes quantidades de dados face a tecnologiad mais antigas como SQL server, Oracle, etc. 
Sitema de analise de larga escala para processamento de dados local ou em nuvem.
Facil de usar e poliglota! 
Contem hoje varios modulos importantes: SQL, Steaming, MLib, Graphx

Map Reduce
    -   Divisao dos Arquivos em HDFS (Hadood File System)
    -  Força o trabaho de Mapear e ReduzirHao os dados, entao demais operacoes como Join, Filter, Unon, etc. 
    - LER, MP e Grava no disco novamente a cada etapa
SPARK
    - Nao tem gravacoes repetidas de dados ao disco. Ele ler do HDFS, processa em memoria, garda os intermediarios em memoria e so no final guarda em HDFS.  



## Main Components

- Core: Cuida de acoes como MR, Joins, Etc (EC2, Kubernets, Mesos, YARN) 
- Spark SQL: Cuida das analises de dados
- Streaming: Cuidado de stream de dados
- MLib: Machine Learing
- Grahx: Criacao de graficos

## HDFS (Haddop) - Dealing with Big Data

HDFS - Store Big Data
Map Reduce - Procesing Data (Onde Spark foi feito para deixar o MP ate 100x mais rapido)

Master or Name Node:
    Onde estao guardados os metadados e orquestra o funcionamento dos Data Nodes 
Slaves or Data Node:
    Seguem as instrucoes do Name Node

HDFS divide os arquivos em pedacos menores de 128mb por padrao e tem uma replicacao padrao de 3. Iso significa que cada pedaco de arquido pode ser enonctrado 3 vewes parmi os nodes. 


## Spark Sessions
Antes da versão 2.0 existia uma divisão entre:

- SparkContext
- SQLContext
- HiveContext

Ao iniciar uma nsessão no antigo, um objeto chamado *sc* nos era dado, que corrsponde ao SparkContext

Apos o 2.0, tudo passa para uma unica definição *SparkSession*. Todos os contextos em um só lugar. 
A variável<span style="color:red"> spark </span> que nos é dada ao inicar, é um *Objeto* da classe *SparkSession* e contém várias funcionalidades. 

Para acessar os contextos na nova definião, basta:
- spark.sparkContext

 Caso a variavel spark não seja criada automaticamente, precisamos executar:

from pyspark.sql import SparkSession
 spark =    SparkSession\
            .builder \
            .master('yarn')\
            .appName("Nome da Aplicação")\
            .getOrCreate()

matser pode ser: *yarn, mesos, Kubernetes or local[k] (onde k é o número de cores que queremos usar)*

No final fa aplicação, coloque: <span style="color:red"> spark.stop()  </span> 

## Spark Submit
O Spark Submit nos permite deploy jobs para serem rodados no Spark. Com as novas versões do Spark, ele apresenta uma série de parametros que podem ser configurados:

```
./bin/spark-submit \
  --class <main-class> \
  --master <master-url> \
  --deploy-mode <deploy-mode> \
  --conf <key>=<value> \
  ... # other options
  <application-jar> \
  [application-arguments]
```

Some of the commonly used options are:

* --class: The entry point for your application (e.g. org.apache.spark.examples.SparkPi)
* --master: The master URL for the cluster (e.g. spark://23.195.26.187:7077)
* --deploy-mode: Whether to deploy your driver on the worker nodes (cluster) or locally as an external client (client) (default: client) 
* --conf: Arbitrary Spark configuration property in key=value format. For values that contain spaces wrap “key=value” in quotes (as shown). Multiple configurations should be passed as separate arguments. (e.g. --conf <key>=<value> --conf <key2>=<value2>)
application-jar: Path to a bundled jar including your application and all dependencies. The URL must be globally visible inside of your cluster, for instance, an hdfs:// path or a file:// path that is present on all nodes.
* application-arguments: Arguments passed to the main method of your main class, if any
* -- py-files: Podemos incluir vários arquivos .py e .zip se suporte ao nosso script principal

Escreva: *spark-submit script.py*

## RDD
Existem dois tipos de dados no Spark: RDD e Data Frames. 

When to use?
- Dados não estruturados 
- Performance e Optimization não são importantes

Problems with RDD?
- Opaque Computation: Cada Taks trabalha na sua partition indiviudalmente, entao o TODO não é analisado junto e não pode ser otimizado. 
- Linguagem de Codigo muito trabalhosa e antiguada

### RDD - Resilient Distrivuited Datasets
Resilient: Resistente ou facilmente recuperavel em caso de problemas
* As RDDs não podem ser modificadas
* Além de track data lineage para analisar dados perdidos e recupera-los automaticamente

Distribuited: São dividios em menos pedaços (Partitions) e distribuidas ao longo dos clusters (multiple nodes). 

Dataset: Contem Dados.

### Transformations and Actions
Podemos fazer dois operações com as RDDs: Transformações e Actions. 

Sempre que uma transformação é feita, uma nova RDD é criada e elas são ligadas entre si pela Lineage. E essa linhagem vai ajudar a recuperar dados perdidos em caso de falhas no processo, podem se recuperar. 

Transformações são Lazy Operations. Já Actions dispara a ação para criar o resultado. 

    Cada Partition da RDD vai ter processada por um TASK diferente dentro do Woker Node (Core) figure-1

#### Lazy Valuation
Sempre que fazermos uma *Transformation*, essa operação não é executada de imediato. O trigger só ocorre quando temos umas *Action*.

#### In-memory Computation
O Spark guarda os dados em memória RAM, se não couber, ele irá tentar colcoar no disco, porém com prejuizos à perfomance. Todas as operações, à la base, são feitas em memoria (mais rápido)

## Dataframe Fundamentals

 - Dataframe é um dataset organizado em linhas e colunas. 
 - Assim como os RDDs, as dataframes também são distribuidas pelos nós do cluster (partitions) figure-2
 - Número de partições *df.rdd.getNumPartitions()*
 - Saber como está a divisão dos dados: *df.rdd.glom().collect()*
 - Lazy Valuation: Os mesmos conceitos de Transformation and Action tambem são aplicados para as Dataframes. Esperando até o trigger de ação ser enviado para escolher o melhor caminho para realizar a tarefa.
 - Os dados na origem não são modificados durante a utlização do Spark. Uma copia dos dados é feita na memória e é com essa copia que o Spark trabalhará. 

 ### Organization
 - Schema: Nome e tipo das colunas que compem a DF. *df.printSchema()*
 - Stored: A forma como os dados estão divididos nas partições (na memoria, no disco ou both) *df.rdd.getStorageLeve()* (useDisk, useMemory,useOffHeap,deserialized,replication)
 - API: Funções para manipular os dados: Select, withColumn,GroupBy

## SparkSession
O SparkSession contem todos os demais context dentro dele (SQL, HIVE E Spark). Assim que iniciamos o Spark, um objeto chamado *spark* da classe *SparkSession* é criado. 

Criando o objeto Spark:
```
from pyspark.sql import SparkSession
 spark =    SparkSession\
            .builder \
            .master('yarn')\
            .appName("Nome da Aplicação")\
            .getOrCreate()
```

### Principais comandos do objeto 'spark'

help(spark)

- df.show(5, truncate=False): Vai forçar o Spark a mostarr tudo que esrá escrito nas colunas

- spark.range(inicio, fim, passo) : Cria uma DF num range de números

- spark.createDataFrame(data = ??, schema) : Cria uma DF a partir de uma estrutura de texto. Se não passarmos o schema ele tenta achar sozinho. ex: *schema = ['Name',  'Age']* or schema=*('Name' string,'Age' Int )* Essa função aceita diversas entradas com tuples, dics, pandas, rdds

- spark.createOrReplaceTempView("Nome da Tabela): Permite cirar um view temporária onde poderemos executar comandos de sql 

- spark.sql (""" ESCREVER A QUERY """) : Podemos passar a query para a view temporárias que foi criada.

- spark.table('Tabel name') : Transforma a TempView numa dataframe

- spark.read.load( path, format='csv' or 'parquet', <span style="color:red"> inferSchema=True </span>,<span style="color:blue"> header = True </span>   )

```
PS: Se para o projeto, sempre todas as colunas são necessárias, então CSV, JSON ou Avro (Row-Based files) são mas indicados. 
However, se apenas algumas colunas espeficicas são necessarias nas analises, Parquet e ORC (Column-Based files) ganham em perfornance. 
```

## Dataframe Fucntions

### Row
from pyspark.sql import Row
row = Row(name='Roberto', Age=35)
row.name
row.Age
'name' in row
'Robert' in row.name

### Column
Acesso:
- df.nome_da_coluna 

    ou df.select(df.nome_da_coluna) 

    ou df.seldct(df["nome_da_coluna"])

 - col 

    from pyspark.ql.functions import col  

    df.select(col("nome da coluna")).show()

Renomear colunas:

- df.nome_da_coluna.alias("novo_nome")

Coluna Ordenada:
 
- df.orderBy(df.nome_da_coluna.asc())

    df.orderBy(col("nome_da_coluna").asc()).select(col("nome_da_coluna")).distict().show()

