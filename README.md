# CobraXAve

Criação de um CRUD baseado em funcionários publicos com tempo limite de 10m

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

# Rotas


### POST /employees

Criar um funcionário baseado nos dados da tabela respectiva

> Caso o funcionário tenha o mesmo email, retorne um bad request
---

### GET /employees

Retornar todos os funcionários

---

### PATCH/PUT /employees/:employeId

Será possível modificar apenas o name, salary e age do funcionário passado por id

> Validar se o funcionário passada por id existe. Caso não exista retorne um not found

> Proibir entrada de valores diferentes da pedida
---
### DELETE /employees/:employeId

Remover o funcionário do banco de dados.

> Validar se o funcionário passada por id existe. Caso não exista retorne um not found