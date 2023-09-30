# Resumo

# Conteúdo programático

# Conceitos básicos:

O que é um banco de dados não relacional?

O termo NoSQL não significa somente (não sql) e sim NOT Only SQL

Não segue modelo de tabelas e relacionamentos

Projetado para lidar com alto volume de dados, alta escalabilidade

Alta flexibilidade na estrutura de dados

Eles são amblamente utilizados em cenários onde consistência imediata de dados não é crítica.

# DIFRENÇAS 

|SQL                       |NoSQL                                    |
|--------------------------|-----------------------------------------|
|Modelo de dados fixo      |Modelo de dados flexíveis                |
|Escalabilidade vertical   |Escalabilidade Horizontal                |
|TransaçÃO ACID 100%       |Transações ACID ausentes total ou parcial|
|Linguagem de consulta SQL |cada SGBD tem sua própria                | 


Visão geral dos tipos de NoSQL

- key-Value
- Documento
- Coluna
- Grafos
- entre outros...

key-Value -> Chave Valor

Armazena dados como pares de chave e valor, onde cada chave é um identificador único para acessar o valor correspondente.

Exemplos de SGBD: Redis, Riak, Amazon DynamondDB

Uso: Um site pode usar um banco de dados Redis para armazenar informações de sessão de usuário.

Documento -> Documento

Armazenam dados em documentos semiestruturados geralmente no formato JSON ou BSON.

Exemplos de SGBD: MongoDB, Couchbase, Apache CouchDB

Uso: Um catálogo de e-commerce pode usar o MongoDB para armazenar informações de produtos, como nome, descrição, preço e atributos adicionais.

Quando se tem um esquema muito diversificado é interessante o uso.

# COLUNA 

Armazenam dados em formato de colunas , permite alta escalabilidade e eficiência em determinados tipos de consultas.
Exemplo de SGBD: Apache Cassandra, ScyllaDB, HBase
Uso: Um sistema de registro de aplicativos pode usar o Apache Cassandra para armazenar registros de log.

# GRAFOS

Armazenam dados interconectados, onde os relacionamentos entre os dados são tão importantes quanto o próprio dado.

Exemplo de SGBD; Neo4j, Amazom Neptune, JanusGraph
Uso: Uma rede social pode usar o Neo4j para armazenar os perfis dos usuários e suas conexões, permitindo consultas eficientes para encotrar amigos em comum.









