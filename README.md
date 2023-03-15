
### Base URL: http://localhost:3001

### Registrar usuário:
POST /register
É necessario corpo de requisição

ex: `
{
	"email": "document.varela@mail.com",
	"password": "123456",
	"name": "Krishna",
	"address": "address",
	"isAdm": false
}
`

FORMATO DA RESPOSTA - STATUS 200:
`
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImRvY3VtZW50LnZhcmVsYUBtYWlsLmNvbSIsImlhdCI6MTY3Nzg1OTU1OCwiZXhwIjoxNjc3ODYzMTU4LCJzdWIiOiIyIn0.PeRSh8NispT-tLbiYEuDvLckffp-U9PTMtzfT5OsOq0",
	"user": {
		"email": "document.varela@mail.com",
		"name": "Krishna",
		"address": "address",
		"isAdm": false,
		"id": 2
	}
}

` 
### Login:
POST /login
É necessario corpo da requisição

ex: `
{
	"email": "document.varela@mail.com",
	"password": "123456",
}
`

FORMATO DA RESPOSTA - STATUS 200:
`
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImRvY3VtZW50LnZhcmVsYUBtYWlsLmNvbSIsImlhdCI6MTY3Nzg2MDA0OCwiZXhwIjoxNjc3ODYzNjQ4LCJzdWIiOiIyIn0.9VtODWK_JCx4MDZ-R5KdY8I95DLIjHXXkw3qWWWk3Iw",
	"user": {
		"email": "document.varela@mail.com",
		"name": "Krishna",
		"address": "address",
		"isAdm": false,
		"id": 2
	}
}
`
### Buscar Perfil do usuário logado (token):
GET /users/userID - FORMATO DA REQUISIÇÃO

Na requisição é necessário o TOKEN
Não é necessario um corpo de requisição

FORMATO DA RESPOSTA - STATUS 200:
`
{
	"email": "document.varela@mail.com",
	"password": "$2a$10$82I49yJ7zhyVIP9tLyzlJ.jN6t5cfqwfDHb/6yrCR410QHyZVk8dy",
	"name": "Krishna",
	"address": "address",
	"isAdm": false,
	"id": 2
}
`
### Editar perfil do usuário logado (token):
PATCH /users/userID - FORMATO DA REQUISIÇÃO

Na requisição é necessário o TOKEN
O corpo da requisição é necessario apenas a chave que for editada
Ex:
`
{
	"address": "Teste de edição"
}
`
FORMATO DA RESPOSTA - STATUS 200:
`
{
	"email": "document.varela@mail.com",
	"password": "$2a$10$82I49yJ7zhyVIP9tLyzlJ.jN6t5cfqwfDHb/6yrCR410QHyZVk8dy",
	"name": "Krishna",
	"address": "Teste de edição",
	"isAdm": false,
	"id": 2
}
`

### Deletar perfil do usuário logado (token):
PATCH /users/userID - FORMATO DA REQUISIÇÃO

Na requisição é necessário o TOKEN
Não é necessario um corpo de requisição


### Listar produtos cadastrados:
GET /products

Não é necessario um corpo de requisição
Não é necessario token de autenticação;

FORMATO DA RESPOSTA - STATUS 200:
`
[
	{
		"id": 1,
		"name": "Guitarra Eletrica Fender",
		"brand": "fender",
		"category": "Guitarra",
		"img": "URL",
		"value": 8722
	},
	{
		"name": "Contrabaixo Fender",
		"brand": "fender",
		"category": "Contrabaixo",
		"img": "URL",
		"value": 7689,
		"id": 2
	}
]

` 

### Registrar produto:
POST /products

É necessario o token de autenticação
É necessario um corpo de requisição
ex:
`
{
   "name": "Contrabaixo Fender",
	 "brand": "fender",
    "category": "Contrabaixo",
    "img": "URL",
    "value": 7689
}
`

FORMATO DA RESPOSTA - STATUS 200:
`
{
	"name": "Contrabaixo Fender",
	"brand": "fender",
	"category": "Contrabaixo",
	"img": "URL",
	"value": 7689,
	"id": 2
}
` 

### Editar produto:
POST /products/productID

É necessario o token de autenticação
É necessario um corpo de requisição, com apenas a chave que for editada.
ex:
`
{
    "value": 10000
}
`

FORMATO DA RESPOSTA - STATUS 200:
`
{
	"name": "Contrabaixo Fender",
	"brand": "fender",
	"category": "Contrabaixo",
	"img": "URL",
	"value": 10000,
	"id": 2
}
`

### Deletar produto:
DELETE /products/productID

É necessario o token de autenticação
Não é necessario um corpo de requisição