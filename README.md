LojaAX — API REST com Spring Boot

📌 Sobre o projeto

O LojaAX é uma aplicação desenvolvida em Java com Spring Boot para representar uma loja de computadores e notebooks.

O projeto possui uma API REST para gerenciamento de produtos e categorias, além de uma interface web desenvolvida com Thymeleaf.

A API permite realizar operações de consulta, cadastro, atualização e exclusão de produtos, seguindo o padrão de comunicação HTTP e retornando dados no formato JSON.

🎯 Objetivo

O projeto foi desenvolvido com o objetivo de aplicar conceitos de desenvolvimento Back-End com Java e Spring Boot, incluindo:

Criação de uma API REST;

Utilização de métodos HTTP;

Organização do projeto em camadas;

Criação de Controllers, Services, Repositories e Models;

Manipulação de objetos Java convertidos para JSON;

Validação básica dos dados dos produtos;

Controle de estoque;

Testes automatizados com JUnit e MockMvc.

🛠️ Tecnologias utilizadas

Java 25

Spring Boot 3.5.16

Spring Web

Spring Thymeleaf

Maven

JUnit 5

MockMvc

HTML5

CSS3

📂 Estrutura do projeto

LojaAX/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/lojaAX/LojaAX/
│   │   │       ├── controller/
│   │   │       │   ├── ProdutoController.java
│   │   │       │   └── ProdutoViewController.java
│   │   │       ├── model/
│   │   │       │   └── Produto.java
│   │   │       ├── repository/
│   │   │       │   └── ProdutoRepository.java
│   │   │       ├── service/
│   │   │       │   ├── ProdutoService.java
│   │   │       │   └── EstoqueService.java
│   │   │       └── LojaAxApplication.java
│   │   └── resources/
│   │       ├── static/
│   │       │   └── css/
│   │       │       └── styles.css
│   │       ├── templates/
│   │       │   ├── detalhe.html
│   │       │   ├── index.html
│   │       │   ├── layout.html
│   │       │   ├── novo-produto.html
│   │       │   ├── produtos.html
│   │       │   └── sobre.html
│   │       └── application.properties
│   └── test/
│       └── java/
│           └── com/lojaAX/LojaAX/
│               └── LojaAxApplicationTests.java
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md

🧱 Organização em camadas

O projeto foi organizado utilizando uma separação de responsabilidades:

Model

A classe Produto representa os produtos da loja.

Cada produto possui:

id

nome

categoria

fabricante

descricao

preco

imagem

estoque

Repository

A classe ProdutoRepository é responsável pelo armazenamento e consulta dos produtos.

Neste projeto, os dados são armazenados em memória utilizando uma lista (ArrayList). Portanto, não é necessário configurar um banco de dados para executar a aplicação.

Service

As classes ProdutoService e EstoqueService concentram as regras de negócio da aplicação.

Entre suas responsabilidades estão:

Listar produtos;

Buscar produtos por ID;

Filtrar produtos por categoria;

Criar produtos;

Atualizar produtos;

Excluir produtos;

Validar preço e estoque;

Verificar disponibilidade de estoque;

Validar uma venda;

Aplicar descontos dentro das regras definidas.

Controller

O ProdutoController disponibiliza os endpoints da API REST.

O ProdutoViewController é responsável pelas páginas web da aplicação utilizando Thymeleaf.

🚀 Como executar o projeto

Pré-requisitos

Antes de executar o projeto, tenha instalado:

JDK 25

Maven (opcional, pois o projeto possui Maven Wrapper)

IDE de sua preferência, como IntelliJ IDEA, Eclipse ou VS Code.

Verifique a instalação do Java:

java -version

▶️ Executando pelo Maven Wrapper

Windows

No terminal, dentro da pasta do projeto:

.\mvnw.cmd spring-boot:run

Linux/macOS

./mvnw spring-boot:run

▶️ Executando pelo Maven

Caso o Maven esteja instalado:

mvn spring-boot:run

A aplicação será iniciada na porta 8081.

http://localhost:8081

🌐 Interface Web

Além da API REST, o projeto possui páginas web.

Página inicial

http://localhost:8081/

Produtos

http://localhost:8081/produtos

Sobre

http://localhost:8081/sobre

Cadastro de produto

http://localhost:8081/produtos/novo

Detalhes de um produto

http://localhost:8081/produto/{id}

Exemplo:

http://localhost:8081/produto/1

🔌 API REST

A API possui como endereço base:

http://localhost:8081/api

Os dados retornados pela API são enviados no formato JSON.

1. Listar todos os produtos

Requisição

GET /api/produtos

Exemplo

GET http://localhost:8081/api/produtos

Resposta

[
  {
    "id": 1,
    "nome": "Notebook AX Ultra 14",
    "categoria": "Notebook",
    "fabricante": "AX Tech",
    "descricao": "Notebook leve, com processador moderno e display Full HD.",
    "preco": 4299.0,
    "imagem": "https://images.unsplash.com/...",
    "estoque": 12
  }
]

2. Filtrar produtos por categoria

Requisição

GET /api/produtos?categoria=Notebook

Exemplo

http://localhost:8081/api/produtos?categoria=Notebook

Também é possível utilizar:

http://localhost:8081/api/produtos?categoria=Computador

3. Buscar produto por ID

Requisição

GET /api/produtos/{id}

Exemplo

GET http://localhost:8081/api/produtos/1

Resposta

{
  "id": 1,
  "nome": "Notebook AX Ultra 14",
  "categoria": "Notebook",
  "fabricante": "AX Tech",
  "descricao": "Notebook leve, com processador moderno e display Full HD.",
  "preco": 4299.0,
  "imagem": "https://images.unsplash.com/...",
  "estoque": 12
}

Se o produto não existir, a API retorna:

404 Not Found

4. Listar categorias

Requisição

GET /api/categorias

Exemplo

GET http://localhost:8081/api/categorias

Resposta

[
  "Todos",
  "Notebook",
  "Computador"
]

5. Cadastrar produto

Requisição

POST /api/produtos

O corpo da requisição deve ser enviado em JSON.

Exemplo

{
  "nome": "Notebook AX Gamer",
  "categoria": "Notebook",
  "fabricante": "AX Tech",
  "descricao": "Notebook para jogos e alto desempenho.",
  "preco": 4999.90,
  "imagem": "https://exemplo.com/notebook.png",
  "estoque": 10
}

Resposta

Em caso de sucesso:

201 Created

Exemplo:

{
  "id": 6,
  "nome": "Notebook AX Gamer",
  "categoria": "Notebook",
  "fabricante": "AX Tech",
  "descricao": "Notebook para jogos e alto desempenho.",
  "preco": 4999.90,
  "imagem": "https://exemplo.com/notebook.png",
  "estoque": 10
}

6. Atualizar produto

Requisição

PUT /api/produtos/{id}

Exemplo

PUT http://localhost:8081/api/produtos/1

Corpo da requisição

{
  "nome": "Notebook AX Ultra 14 Pro",
  "categoria": "Notebook",
  "fabricante": "AX Tech",
  "descricao": "Notebook atualizado com alto desempenho.",
  "preco": 4599.90,
  "imagem": "https://exemplo.com/notebook-pro.png",
  "estoque": 15
}

Resposta

Em caso de sucesso:

200 OK

7. Excluir produto

Requisição

DELETE /api/produtos/{id}

Exemplo

DELETE http://localhost:8081/api/produtos/1

Resposta

Em caso de sucesso:

204 No Content

📊 Resumo dos endpoints

Método

Endpoint

Função

GET

/api/produtos

Lista todos os produtos

GET

/api/produtos?categoria=Notebook

Filtra produtos por categoria

GET

/api/produtos/{id}

Busca um produto pelo ID

GET

/api/categorias

Lista as categorias

POST

/api/produtos

Cadastra um novo produto

PUT

/api/produtos/{id}

Atualiza um produto

DELETE

/api/produtos/{id}

Exclui um produto

🧪 Testes

O projeto possui testes automatizados utilizando JUnit 5 e MockMvc.

Os testes verificam, entre outras funcionalidades:

Listagem de produtos;

Listagem de categorias;

Filtro por categoria;

Cadastro de produtos pela API;

Atualização de produtos;

Exclusão de produtos;

Consulta de estoque;

Validação de venda sem estoque;

Validação de desconto;

Funcionamento das páginas web.

Para executar os testes:

Windows

.\mvnw.cmd test

Linux/macOS

./mvnw test

📦 Dados da aplicação

O projeto possui produtos cadastrados inicialmente para demonstração.

As categorias disponíveis são:

Notebook

Computador

Como o armazenamento é feito em memória, os produtos cadastrados ou alterados durante a execução não são persistidos após o encerramento da aplicação.

👨‍💻 Projeto acadêmico

Projeto desenvolvido para aplicação prática dos conceitos de Desenvolvimento Back-End com Java, utilizando Spring Boot e API REST.

Projeto: LojaAX
Tecnologia principal: Java + Spring Boot
Tipo: API REST + aplicação Web
Autor: Nicolas Alexandrino
