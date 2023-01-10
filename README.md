# CobraXAve

Criação de um CRUD baseado em funcionários publicos com tempo limite de 15m

# Objetivo

Criar uma aplicação CRUD funcional que cotenha essa rotas
POST, GET, PATCH/PUT, DELETE e suas respectivas validações

# Tabelas

### employees

* id - primary key - uuid
* name - string
* email - url - unique
* age - integer
* salary - float

### cityHall

* id - primary key - uuid
* city - string
* cep - string - unique
* mayor - string

> Crie uma tabela pivot entre elas ligando os funcionários a prefeitura, lembrando que uma prefeitura pode ter vários funcionários, mas um funcionário só pode está em uma prefeitura

# Rotas

### POST /cityHall

Criar uma prefeitura baseado nos dados da tabela respectiva

> Caso o cep da prefeitura já tenha sido criado, retorne um bad request
---

### POST /employees

Criar um funcionário baseado nos dados da tabela respectiva

> Funcionários ao serem criados obrigatoriamente precisam está ligados a alguma prefeitura.

> Caso o funcionário tenha o mesmo email, retorne um bad request
---

### GET /employees/:cityId

Retornar todos os funcionários da prefeitura baseada no id passado na url

> Validar se a prefeitura passada por id existe. Caso não exista retorne um not found
---

### PATCH/PUT /employees/:employeId

Será possível modificar apenas o name, salary e age do funcionário passado por id

> Validar se o funcionário passada por id existe. Caso não exista retorne um not found

>Proibir entrada de valores diferentes da pedida
---
### DELETE /employees/:employeId

Remover o funcionário do banco de dados e sua relação com a prefeitura.

> Validar se o funcionário passada por id existe. Caso não exista retorne um not found