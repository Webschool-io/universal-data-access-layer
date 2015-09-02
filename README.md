# Universal Data Access Layer

Uma ideia que tenho há MUITO TEMPO e agora vamos começar a tirar do papel eu e o Marcelo Carvalho é de um Data Access Layer que trabalhe com bancos NoSQL.
A ideia eh que vc possa criar um roteiro de onde seus dados irão em um sistema com vários bancos de dados!
Por exemplo:
- insere no MongoDB;
- pega certos valores desse Objeto e cria as relações com GRAFOS
- pega certos valores desse Objeto e cria o Objeto de CACHE em um Redis da vida.
E assim vai! E claro que tudo via REST.
A ideia é que essa API tenha a mesma interface de CRUD para qualquer banco, porém para cada TIPO de banco exista uma interface mais especializada para ele, diferentemente dos relacionais que são todos iguais.
Porque eu sempre evangelizei essa arquitetura híbrida de Bancos NoSQL desde 2012 pelo menos.

## API CRUD

- Create: `insert` ou `save`
- Retrieve: `find` e `findOne`
- Update: `update` ou `save`
- Delete: `remove`

### Create

A função para **inserir** um dado usando ou `insert` ou `save` será passando o objeto a ser inserido no parâmetro da função, essa tendo setado a conexão e o Model/Coleção/Tabela onde será inserido. Por exemplo:

```js
var MongoDB = require('UniversalDataAccessLayer')('MongoDB');
// MongoDB.connect('mongodb://localhost:27017'); a conexão ja estará no config.js
var Schema = new MongoDB.Schema({name: {type: String, required: true});
var Model = new MongoDb.Model(Schema);

var User = new Model({name: "Suissa"});
User.save(callback);
// ou User.insert({name: "Suissa"}, callback);
```

### Retrieve
### Update
### Delete
