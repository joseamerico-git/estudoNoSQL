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

# Introdução ao MongoDB

É um banco de dados orientado a documentos, por isso seu uso torna-se um pouco mais complexo, precisa ser minunciosamente planejado.
Uso: 
Aplicações Web

Análise de big data -> análise de grandes volumes de dados não estruturados ou semi estruturados, fornecendo uma plataforma para armazenar e processar esses dados.

Armazenamento de dados semiestruturados: Permite a inserção de documentos com estruturas diferentes em uma mesma coleção.

Caso de uso de geolocalização: Com suas funcionalidades de consulta geoespacial é adequado para casos de uso que envolvem dados baseados em localização, mapeamento e rastreamento.

# Instalação do MongoDB

[MongoDB-Atlas](https://www.mongodb.com/atlas/database)

## Estrutura de um banco de dados baseado a documentos.

São coleções de documentos 
-> Coleção é composta por vários documentos, é um agrupamento lógico de documentos, não exige esquema ou que os documentos tenham a mesma estrutura, porém não é uma boa prática e sim seguir alguns critérios.

# Os nomes das coleções devem começãr com algumas régras

## Características

Começar com letra ou _ (underscore)
Podem conter letras, números ou underscores.
Não podem ser vazios.
Não podem ter mais de 64 bytes de cumprimento.

# DOCUMENTOS

- São armazenados em estruturas BSON (Binary JSON), que são estruturas flexíveis e semiestruturadas

- Cada documento possui um identificador único chamado "_id"

- É composto por pares de chaves e valores.

# Tipos de dados Simples

- String
- Number
- Boolean
- Date
- Null
- ObjectId

# Tipos de dados Compléxos

- Array
- Documento Embutido (Embedded Document)
- Referência (Reference)
- GeoJSON

# Estrutura

```
    {
    _id : ObjectId(""),
    "nome_campo":"valor_campo",
    ...


   }
```

# Criando nossas coleções.

[JsonFormatter](https://jsonformatter.curiousconcept.com/)

# Estratégias de dados eficientes e escaláveis

Critérios para que seja escalável dependerá da modelagem ser compatível e eficiênte com nossas consultas.

A modelagem devem ser orientada pelas consultas que serão realizadas com mais frequência.

Olhando para usuarios, reservas e destinos é preciso pensar nas buscas que teremos em nosso sistema.

# Inner Documents

No MongoDB, é comum desnormalizar os dados para evitar operações de junção (join) custosas. Isso significa que os dados relacionados podem ser armazenados juntos em um único documento ao invés de serem distribuídos em várias coleções.

# Modelar usuário com estratégia desnormalizada

Quando utilizar o Inner Document
- Os dados aninhados são específicos para o documento pai.
- Os dados aninhados são sempre acessados juntamente com o documento pai
- A cardinalidade do relacionamento é um-para-muitos(um usuário pode ter várias reservas)

Quando não utilizar

Se os dados aninhados precisam ser consultados e atulizados independentemente do documento pai, é mais adequado utilizar coleções separadas.

# Referências 

Forma de relacionar os documentos entre si.

Modelagem com estratégias de referências


{
    "_id": ObjectId(123),
    "destino": ObjectId(456),
    "data" : "2023-10-10",
    "status" : "pendente",
    "usuario": ObjectId(345)
}



    {
        //usuários
   "id":1,
   "nome":"JOSE AMERICO",
   "email":"doichejunior@gmail.com",
   "enderecos":[
      {
        "logradouro":"Rua Aristeu Gallo",
        "numero":"123A",
        "bairro":"Park Bambú",
        "cidade":"Araraquara",
         
      }
   ],
   "interesses":[
      "kart",
      "culinária"
   ],
   "reservas":[
      1,
      1
   ]
}




# Criando um database

use nomebanco

Enquanto ele não tiver uma coleção ele não será apresentado na lista.

MongoDB Compass

db.createCollection("usuarios")
db.usuarios.insertOne({});
db.usuarios.insertMany([{},{}])

# Consultando doumentos

db.usuarios.find({})
db.usuarios.findOne({})
db.usuarios.findOneAndUpdate({},{});
db.usuarios.fidOneAndDelete({});

//buscando todos os dados 

passar as chaves vazias.

db.usuarios.find({})

//busca usuários que tem o nome Joao

db.usuarios.find({"nome":"JOAO"})

db.usuarios.findOneAndUpdate({"nome":"JOAO"},{$Set:{"nome": "JOAO PEDRO"}});

 # $Set: 
 
 mais utilizado para atualizar, pois ele devolve o registro da forma que estava anteriormente. 

atualizar todas as idades com nome x
como o operador 

# $inc incrementar

# $push incrementar array

# Exclusão de documentos

db.usuarios.deleteOne({})
db.usuarios.deleteMany({},{},...)

# IGUALDADE
db.usuarios.find({"campo":"valor"})

# OPERADORES LÓGICOS

```
$and
$or
$not

```

# COMPARAÇÃO

```
$eq: ==
$ne:!=
$gt:>
$gte:>=
$lt:<
$lte:<=
$in:[]
$nin:[]
```
# ORDENAÇÃO

```
    {"idade":"20", "nome":carlos} //pega o registro que correspondem a esses dois critérios

    //Utlizando o $and
    {$and:[{"idade":20,"nome":"fulano"}]}

```

# PAGINAÇÃO

db.usuarios.find().skip(10).limit(5)


# PROJEÇÃO

Quais campos eu quero retornar na minha consulta?

db.usuarios.findOne({cidade:{$nin:["São Paulo"]}})

# Breve introdução ao Redis

O Redis é um sistema de armazenamento de dados em memória de alto desempenho

- Armazenamento em memória
- Estrutura de dados versátil
- Operações atômicas
- Cache de alto desempenho
- Pub/Sub (Publicação/Assinatura)

Principais Utilizações do Redis

- Cache de dados
- Filas de Mensagens
- Contagem de acessos e estatísticas em tempo real
- Gerenciamento de sessões
- Cache de resultados de consultas

# COMANDOS PRINCIPAIS

- SET
- GET
- DEL
- EXISTS
- KEYS
- INCR
- DECR

[Exemplo](https://try.redis.io)

```
    > SET nome 'pamela'
OK
> set nome_2 'pmela2'
OK
> get nome
"pamela"
> get nome_2
"pmela2"
> SET JOAO
OK
> get nome
"pamela"
> get JOAO
""
> KEYS
(error) ERR wrong number of arguments for 'keys' command
>
> keyw
(error) I'm sorry, I don't recognize that command. Please type HELP for one of these commands: DECR, DECRBY, DEL, EXISTS, EXPIRE, GET, GETSET, HDEL, HEXISTS, HGET, HGETALL, HINCRBY, HKEYS, HLEN, HMGET, HMSET, HSET, HVALS, INCR, INCRBY, KEYS, LINDEX, LLEN, LPOP, LPUSH, LRANGE, LREM, LSET, LTRIM, MGET, MSET, MSETNX, MULTI, PEXPIRE, RENAME, RENAMENX, RPOP, RPOPLPUSH, RPUSH, SADD, SCARD, SDIFF, SDIFFSTORE, SET, SETEX, SETNX, SINTER, SINTERSTORE, SISMEMBER, SMEMBERS, SMOVE, SORT, SPOP, SRANDMEMBER, SREM, SUNION, SUNIONSTORE, TTL, TYPE, ZADD, ZCARD, ZCOUNT, ZINCRBY, ZRANGE, ZRANGEBYSCORE, ZRANK, ZREM, ZREMRANGEBYSCORE, ZREVRANGE, ZSCORE
> keys
(error) ERR wrong number of arguments for 'keys' command
> KEYS nome
1) "nome"
> KEYS
(error) ERR wrong number of arguments for 'keys' command
> GET KEYS
(nil)
> EXPIRE nome_2 1
(integer) 1
> TTL
(error) wrong number of arguments (given 0, expected 1)
> EXISTS nome_2
(integer) 0

```

# CONCLUSÃO 

CONCEITOS BÁSICOS DE DADOS NÃO RELACIONAIS

Quando utilizar um ou outro? Vai depender muito do senário, porém podemos utilizar várias técnologias juntas.

Relacional -> precisamos de integridade de dados

Não Relacionais -> Ganha em agilidade e facilidade de modelagem, perde na ACID


O que é ORM? ORM (Object Relational Mapping, ou Mapeamento Objeto Relacional em português) é uma técnica de programação que visa facilitar a comunicação entre bancos de dados relacionais e linguagens de programação orientadas a objetos, como Java, Python e JavaScript.

















