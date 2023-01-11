# CobraXAve

Criação de um CRUD baseado em animais do zoológico com tempo limite de 20m

# Objetivo

Criar uma aplicação CRUD funcional que contenha essa rotas
POST, GET, PATCH, DELETE e suas respectivas validações

# Tabelas

### animal

* id - PK - bigserial
* scientific_name - string - not null
* surname - string - not null
* species - string - not null
* weight - float - not null
* age - integer- not null

### zoo

* id - PK - bigserial
* name - string - not null
* city - string - not null
* capacity - integer - not null

> Crie um relacionamento entre os animais e o zoológico, lembrando que cada animal só pertence a um zoologico, mas cada zoologico pode ter vários animais

# Rotas

### POST /animals

Criar um animal baseado nos dados da tabela respectiva

> Caso alguma informação esteja incorr  eta ou faltante retorne um bad request - statusCode: 400

```
    Expected
    statuCode: 201
    Response: {
        "id": 1,
	    "scientific_name": "Panthera tigris",
	    "surname": "Rajado",
	    "species": "felina",
	    "weight": 88.58,
	    "age": 12
    }
```
---
### POST /zoo

Criar um zoológico baseado nos dados da tabela respectiva

Obs: O zoológico pode ser criado sem animais 

> Caso alguma informação esteja incorreta ou faltante retorne um bad request - statusCode: 400

```
    Expected
    statuCode: 201
    Response: {
	    "name": "kenzieAnimal",
	    "city": "curitiba",
	    "capacity": 2
    }
```
---

### POST /zoo/add

Adicione um animal ao zoológico

```
body: {
    animalId: 1,
    zooId: 1
} 
```

> Caso não encontre o animal, retorne um not found - statusCode: 404

> Caso não encontre o zoológico, retorne um not found - statusCode: 404

> Caso o animal já esteja no zoológico retorne um conflict - statusCode: 409

> Caso o zoológico esteja lotado, retorne um not acceptable - statusCode: 406


```
    Expected
    statuCode: 201
    Response: "animal adicionado"
```

### GET /zoo

Retorne todos os zoológicos relacionados com os animais

```
    Expected
    statuCode: 200
    Response: [
    {
        "id": 1,
        "name": "kenzieAnimal",
        "city": "curitiba",
        "capacity": 2,
        "animals": [
            {
                "id": 1,
	            "scientific_name": "Panthera tigris",
	            "surname": "Rajado",
	            "species": "felina",
	            "weight": 88.58,
	            "age": 13
            }
            ...
        ]
    }
    ...
    ]
```

### PATCH /animals/animalId

Modificar informações de algum animal baseado no id passado na url

> Caso não encontre o animal, retorne um not found - statusCode: 404

> Caso alguma informação esteja incorreta retorne um bad request - statusCode: 400

```
    Expected
    statuCode: 200
    Response: {
        "id": 1,
	    "scientific_name": "Panthera tigris",
	    "surname": "Rajado",
	    "species": "felina",
	    "weight": 88.58,
	    "age": 13
    }
```

### DELETE /animals/animalId

Remova o animal do banco, remoção deve ser em cascata, ou seja, remover também do zoológico que está. 

> Caso não encontre o animal, retorne um not found - statusCode: 404

```
    Expected
    statuCode: 204
    Response: Not Content
````