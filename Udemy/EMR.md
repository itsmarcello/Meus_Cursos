# The largest heading
## The second largest heading
###### The smallest heading

# EMR course

### Master, Core and Taks
* Master
* Cores
* Tasks

### Key Pair 
Com a criacao de uma Key Pair de E2C e seu input na criacao do EMR, podemos ter acesso ao Cluster (MASTER) que esta rodando no EMR

### Master Public DNS
Usado para se conectar com a Master dentro do seu EMR

### Bootstrap
Parte reposavel pela  intalacao de pre-requitos na criacao do EMR cluster

### Acessing File in 3 EMR
aws s3 ls s3://bucket-name
aws s3 mb s3///bucket -- abrir pasta
aws s3 ls!grep github -- procurar pastas com nome de github
mkdir nome_da_pasta -- criar pasta no ambiente EMR

### Rodar Applcation direto no Terminal 
spark-submit app.py
expr