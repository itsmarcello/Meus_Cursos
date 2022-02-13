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

