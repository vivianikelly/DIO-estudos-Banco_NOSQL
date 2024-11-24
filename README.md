# Estudos Banco de dados NOSQL

Caderno de estudos sobre banco de dados NoSQL, com ênfase no MongoDB.

## Tipos de banco NoSQL

<div align="center"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgTvUap4oI3oRtBvYZkMTbY28RMt91TKIAsY97WXcCiqFA_COCIRTVP85rq8U_3i5EP1O-llqUuUwdUSvJ82fK1OsuZZT-93WQDGzFdc2N5ILcGe9nL5C7iuAMDM6ooBrwGheXKS_LfEUcy/s640/Autoci%25C3%25AAncia+-+Tipos+de+Bancos+de+Dados+NoSQL.png" alt="Bancos de dados NoSQL" width="600" height="300"></div>

### Grafos

Este tipo de banco é comum em detecção de fraudes, redes sociais, mecanismos de recomendação, etc.
O Neo4j é um exemplo de banco tipo grafo, o qual utiliza a linguagem **Cypher** para executar comandos e consultas.

#### Comandos Básicos

##### Criar Nós (Nodes):

CREATE (n:Label {propriedade: 'valor'})<br>

CREATE (p:Pessoa {nome: 'Viviani', idade: 30})

##### Criar Relacionamentos

MATCH (a:Label1), (b:Label2)
CREATE (a)-[r:RELACAO {propriedade: 'valor'}]->(b) <br>

MATCH (p1:Pessoa {nome: 'Viviani'}), (p2:Pessoa {nome: 'João'})
CREATE (p1)-[:AMIGO_DE]->(p2)

##### Buscar Dados

MATCH (n:Label) RETURN n <br>

MATCH (p:Pessoa {nome: 'Viviani'}) RETURN p

##### Atualizar propriedades

MATCH (n:Label {propriedade: 'valor'})
SET n.novaPropriedade = 'novoValor' <br>

MATCH (p:Pessoa {nome: 'Viviani'})
SET p.idade = 31

##### Remover Propriedades, Nós ou Relacionamentos

- Propriedade:

MATCH (n:Label {propriedade: 'valor'})
REMOVE n.propriedade

- Nós:

MATCH (n:Label {propriedade: 'valor'})
DELETE n

- Relacionamentos:

MATCH (n1)-[r:RELACAO]->(n2)
DELETE r

#### Deletar Todos os Dados
cypher
Copiar código
MATCH (n)
DETACH DELETE n

### Colunar

O banco Cassandra é um exemplo de banco colunar. 

- **Keyspace:** agrupamento de famílias de colunas => database.
- **Column Family/table:** agrupamento de colunas => table.
- **Row key:** chave que repesenta uma linha de coluna => PK.
- **Column:** representa um valor contendo: Name, Value, Timestamp.

A busca é realizada pelas chaves.

### Chave-valor (key-value)

Armazena um conjunto de dados, identificados por um ID exclusivo.

- Nom desempenho em APP na nuvem.
- Busca limitada, devido a busca ser pela chave.

Usados em cache, sessão de usuário, carrinhos de compra. O Redis é um exemplo de banco chave-valor.

Redis é altamente versátil e rápido, sendo ideal para caching, filas e manipulação de dados em tempo real.

### Documento

- Dados e documentos autocontidos e auto descritivos. 
- Permite redundância e incosistência.
- Livre de esquemas, o qual pode usar json, xml, etc.

Um exemplo de banco baseado em Documento é o MongoDB.

# MongoDB

## Introdução

- Código aberto
- Alta performance
- Schema-free
- Utiliza json para armazenamento dos dados (BSON)
- Suporta índices
- Escala horizontal
- GridFS - armazenamento e recuperação de arquivos que excedem o limite de tamanho do documento BSON de 16 MB.

### Estruturação

- Document ==> Tupla/Registro
- Collection ==> Tabela
- Embedding/linking ==> Join

#### Quando usar

- Grande volume de dados (usar índices).
- Dados não precisam ser estruturados.

#### Quando não usar

- Necessidade de relacionamentos/joins.
- Precisa ACID e transações.







