# CP05-API RESTful

## 1. Introdução

Esta API RESTful foi desenvolvida para possibilitar a criação, gerenciamento e compartilhamento de decks do jogo Magic: The Gathering (MTG). Inspirada na plataforma [Archidekt](https://archidekt.com), ela fornece endpoints para manipular decks, cartas, usuários e comentários, com suporte a múltiplos formatos e categorias.

## 2. Rotas da API
| Nº | Método | Rota                     | Descrição                       | Status Codes |
|--|--------|--------------------------|---------------------------------|--------------|
| 1 | GET    | /cartas  | Listar todas as cartas  | 200, 500            |
|2| GET    | /cartas/{id}   | Buscar carta por ID  | 200, 404, 500       |
|3| POST   | /cartas    | Criar nova carta         | 201, 400, 500       |
|4| PUT    | /cartas/{id}    | Atualizar carta   | 200, 400, 404, 500  |
|5| DELETE | /cartas/{id}    | Excluir carta        | 204, 404, 500       |
||  |  |    |   |
|6| GET    | /decks   | Listar todos os decks   | 200, 500  |
|7| GET    | /decks/{id}   | Buscar deck por ID       | 200, 404, 500  |
|8| POST   | /decks    | Criar novo deck     | 201, 400, 500  |
|9| PUT    | /decks/{id}    | Atualizar um deck existente | 200, 400, 404, 500  |
|10| DELETE | /decks/{id}   | Excluir um deck   | 204, 404, 500       |
|11| GET    | /decks/usuario/{idUsuario} | Listar decks de um usuário específico | 200, 404, 500    |
|12| POST   | /decks/{id}/cartas  | Adicionar carta a um deck  | 201, 400, 404, 500  |
|13| DELETE | /decks/{id}/cartas/{idCarta}  | Remover carta de um deck   | 204, 404, 500   |
|  |  |   |  |
|14| GET    | /usuarios  | Listar usuários      | 200, 500   |
|15| POST   | /usuarios    | Criar novo usuário     | 201, 400, 500       |
|16| GET    | /usuarios/{id}     | Buscar usuário por ID       | 200, 404, 500       |
|17| PUT    | /usuarios/{id}   | Atualizar dados do usuário    | 200, 400, 404, 500  |
|18| DELETE | /usuarios/{id}  | Excluir usuário        | 204, 404, 500    |
|19| POST   | /decks/{id}/comentarios   | Adicionar comentário ao deck   | 201, 400, 404, 500  |
|20| GET    | /decks/{id}/comentarios    | Listar comentários de um deck    | 200, 404, 500       |

## 3. DTOs e Modelos de Dados

3.1. **CartaDTO**
```json
{
  "id": 10,
  "nome": "Tarmogoyf",
  "tipo": "Criatura",
  "descricao": "A força de Tarmogoyf é igual ao número de tipos de card no cemitério.",
  "cor": "Verde",
  "custoMana": "1G",
  "quantidade": 4,
  "dataCriacao": "2025-04-10"
}
```

3.2. **DeckDTO**
```json
{
  "id": 1,
  "nome": "Golgari Midrange",
  "formato": "Modern",
  "descricao": "Deck com foco em valor incremental e remoções.",
  "cartas": [
    {
      "id": 10,
      "nome": "Tarmogoyf",
      "tipo": "Criatura",
      "descricao": "A força de Tarmogoyf é igual ao número de tipos de card no cemitério.",
      "cor": "Verde",
      "custoMana": "1G",
      "quantidade": 2,
      "dataCriacao": "2025-04-10"
    }
  ],
  "comentarios": [
    {
      "id": 1,
      "conteudo": "Deck excelente para o meta atual!"
    }
  ],
  "dataCriacao": "2025-04-10"
}
```

3.3. **UsuarioDTO**
```json
{
  "id": 12,
  "nome": "Maria Silva",
  "email": "maria@email.com",
  "senha": "********",
  "dataCadastro": "2025-04-01",
  "cartas": [
    {
      "id": 10,
      "nome": "Tarmogoyf",
      "tipo": "Criatura",
      "cor": "Verde",
      "custoMana": "1G",
      "quantidade": 2
    }
  ],
  "decks": [
    {
      "id": 1,
      "nome": "Golgari Midrange",
      "formato": "Modern",
      "descricao": "Deck com foco em valor incremental e remoções.",
      "dataCriacao": "2025-04-10"
    }
  ]
}
```

