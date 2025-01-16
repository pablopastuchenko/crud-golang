# Go and PostgreSQL API

Este projeto é uma API RESTful simples desenvolvida em Go utilizando o framework Fiber e o ORM Gorm para interagir com um banco de dados PostgreSQL. A aplicação permite gerenciar livros, com funcionalidades como criar, listar, buscar por ID e excluir livros.

## Funcionalidades
- Criar um novo livro
- Listar todos os livros
- Buscar um livro por ID
- Excluir um livro

## Requisitos
Certifique-se de ter os seguintes itens instalados:
- [Go](https://golang.org/) v1.20 ou superior
- [PostgreSQL](https://www.postgresql.org/) v12 ou superior
- [Git](https://git-scm.com/)

## Configuração do Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/pablopastuchenko/goandpostgres.git
   cd goandpostgres
   ```

2. Instale as dependências:
   ```bash
   go mod tidy
   ```

3. Configure as variáveis de ambiente:
   Crie um arquivo `.env` na raiz do projeto com as seguintes variáveis:
   ```env
   DB_HOST=localhost
   DB_PORT=5432
   DB_USER=seu_usuario
   DB_PASS=sua_senha
   DB_NAME=nome_do_banco
   DB_SSLMODE=disable
   ```

4. Inicie o PostgreSQL e crie o banco de dados especificado na variável `DB_NAME`.

5. Execute as migrações para criar as tabelas:
   O projeto executa automaticamente as migrações na inicialização.

## Executando a Aplicação

1. Inicie o servidor:
   ```bash
   go run main.go
   ```

2. A API estará disponível em [http://localhost:8080](http://localhost:8080).

## Endpoints da API

### Criar Livro
- **POST** `/api/create_books`
- **Body**:
  ```json
  {
    "author": "Autor Exemplo",
    "title": "Título Exemplo",
    "publisher": "Editora Exemplo"
  }
  ```
- **Resposta de Sucesso** (HTTP 200):
  ```json
  {
    "message": "book has been added"
  }
  ```

### Listar Todos os Livros
- **GET** `/api/books`
- **Resposta de Sucesso** (HTTP 200):
  ```json
  {
    "message": "books fetched successfully",
    "data": [
      {
        "id": 1,
        "author": "Autor Exemplo",
        "title": "Título Exemplo",
        "publisher": "Editora Exemplo"
      }
    ]
  }
  ```

### Buscar Livro por ID
- **GET** `/api/get_books/:id`
- **Resposta de Sucesso** (HTTP 200):
  ```json
  {
    "message": "book id fetched successfully",
    "data": {
      "id": 1,
      "author": "Autor Exemplo",
      "title": "Título Exemplo",
      "publisher": "Editora Exemplo"
    }
  }
  ```

### Excluir Livro
- **DELETE** `/api/delete_book/:id`
- **Resposta de Sucesso** (HTTP 200):
  ```json
  {
    "message": "book delete successfully"
  }
  ```

## Estrutura do Projeto

```
.
├── models
│   └── books.go      # Modelo para a tabela de livros
├── storage
│   └── postgres.go   # Configuração da conexão com o banco de dados
├── .env              # Arquivo de variáveis de ambiente (não incluso no repositório)
├── go.mod            # Gerenciador de dependências
├── go.sum            # Checksums das dependências
└── main.go           # Arquivo principal da aplicação
```

## Contribuições
Contribuições são bem-vindas! Siga os passos abaixo:

1. Fork o repositório
2. Crie uma branch para a sua funcionalidade (`git checkout -b feature/nova-funcionalidade`)
3. Faça commit das suas alterações (`git commit -m 'Adicionei nova funcionalidade'`)
4. Faça push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

## Licença
Este projeto está licenciado sob a Licença MIT. Consulte o arquivo LICENSE para mais detalhes.

## Autor
[Pablo Henrique](https://github.com/pablopastuchenko)

