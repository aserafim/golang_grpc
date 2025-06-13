# 📚 Golang gRPC - Category Service

Este projeto implementa um serviço gRPC utilizando **Go** para o gerenciamento de categorias, com persistência em **SQLite**. Ele demonstra o uso de diferentes tipos de comunicação gRPC, como chamadas unárias, streaming cliente-servidor e bidirecional, seguindo boas práticas de arquitetura como organização em pacotes `cmd`, `internal` e `proto`.

---

## 🚀 Funcionalidades

- 📌 Criar categorias via requisição unária
- 📄 Listar todas as categorias
- 🔎 Buscar uma categoria por ID
- 🔁 Criar múltiplas categorias via streaming (cliente ou bidirecional)

---

## 📁 Estrutura do Projeto

```

golang\_grpc/
├── cmd/
│   └── grpcServer/           # Ponto de entrada da aplicação gRPC
│       └── main.go
├── internal/
│   ├── database/             # Lógica de acesso ao banco de dados
│   ├── pb/                   # Códigos gerados pelo protocolo gRPC
│   └── service/              # Implementação das regras de negócio
├── proto/                    # Definições .proto (Protocol Buffers)
│   └── course\_category.proto
├── go.mod / go.sum           # Gerenciamento de dependências Go
└── README.md

````

---

## 📦 Tecnologias e Ferramentas

- [Go (Golang)](https://golang.org/)
- [gRPC](https://grpc.io/)
- [Protocol Buffers (proto3)](https://developers.google.com/protocol-buffers)
- [SQLite](https://www.sqlite.org/index.html)
- [protoc-gen-go](https://github.com/protocolbuffers/protobuf-go)
- [protoc-gen-go-grpc](https://github.com/grpc/grpc-go)

---

## 🛠️ Como Executar o Projeto

### 1. Clonar o repositório

```bash
git clone https://github.com/seu-usuario/golang_grpc.git
cd golang_grpc
````

### 2. Instalar as dependências

```bash
go mod tidy
```

### 3. Gerar os arquivos `.pb.go` (caso não existam)

```bash
protoc --go_out=. --go-grpc_out=. proto/course_category.proto
```

> Certifique-se de que `protoc`, `protoc-gen-go` e `protoc-gen-go-grpc` estão instalados.

### 4. Criar o banco SQLite (opcional)

```sql
CREATE TABLE categories (
  id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  description TEXT
);

CREATE TABLE courses (
  id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  description TEXT,
  category_id TEXT,
  FOREIGN KEY(category_id) REFERENCES categories(id)
);
```

### 5. Rodar o servidor

```bash
go run cmd/grpcServer/main.go
```

O servidor gRPC ficará escutando na porta `:50051`.

---

## 🧪 Exemplo de Serviços gRPC Implementados

### 🔹 CreateCategory (unary)

Cria uma nova categoria com nome e descrição.

### 🔹 CreateCategoryStream (client-streaming)

Cria várias categorias através de uma stream enviada pelo cliente.

### 🔹 CreateCategoryStreamBidirectional (bidirectional-streaming)

Cliente e servidor enviam e recebem categorias simultaneamente.

### 🔹 ListCategories

Retorna a lista de todas as categorias cadastradas.

### 🔹 GetCategory

Retorna os dados de uma categoria com base no `id`.

---

## 📝 Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](LICENSE) para mais informações.

---

## 👤 Autor

Desenvolvido por [**Alefe Serafim**](https://github.com/aserafim)

