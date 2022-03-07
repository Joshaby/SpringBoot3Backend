SpringBoot2Backend
=====

Repositório do backend do curso Spring Boot, Hibernate, REST, Ionic, JWT, S3, MySQL, MongoDB na Udemy por Nélio Alves

Atualização do projeto https://github.com/Joshaby/SpringBoot2-Ionic-Backend

## Estruturação do projeto

### Estrutura das pastas com classes e interfaces

- Config: Classes de configuração do projeto, como persistência e segurança
- Entities: Classes de domínio que representam objetos do bando de dados
- Dto: Classes que representam JSON das requisições
- Repositories: Interfaces que realizaram consultas no banco de dados
- Controllers: API Rest do projeto junto com classes úteis e tratamento de execeção
- Security: Classes, classes úteis para prover segurança
- Services: Classes com regras de negócio junto com classes úteis e que acessam os repositories

### Pasta resource

#### Arquivos properties

- application.properties: Arquivo base de proprieadades do projeto! Usado para setar o ambiente de execução, definir senha de acesso so SMTP da Google e a secret key de geração de token JWT
- application-dev.properties: Arquivo com propriedades do ambiente dev, que roda localmente e usa MySQL
- application-prod.properties: Arquivo com propriedades do ambiente prod que roda no Heroku
- application-test.properties: Arquivo com propriedades do ambiente test, que roda localmente e usa hH2

#### Templates

- email: Contém um arquivo html populado com Thymeleaf usado para envio de pedidos por email

## Endpoints disponíveis

### H2
- `/h2-console` - GET: Acesso ao bando de dados H2

### Clientes

- `/clientes` - GET: Obtém todos os clientes
- `/clientes` - POST: Cadastro de cliente

    ```
    {
        "nome": "Donnie Darko",
        "email": "donniedarko@gmail.com",
        "cpfOuCnpj": "294.563.110-58",
        "tipoCliente": 1,
        "senha": donnie123,
        "logradouro": "Rua",
        "numero: "9696",
        "complemento": "Ao lado da padaria Pão Gostoso",
        "bairro": "Barro duro",
        "cep": "23213-343",
        "telefone1": "5583908490983",
        "telefone2": "5583918798912",
        "cidadeId": 1     
    }
    ``` 

- `/clientes/{id}` - GET: Obtém um cliente por id
- `/clientes/{id}` - PUT: Atualização de cliente por id

    ```
    {
        "nome": "Donnie Darko",
        "email": "donniedarko@gmail.com"
    }
    ``` 

- `/clientes/{id}` - DELETE: Deleção de cliente por id
- `/clientes/pages?page=0&linesPerPage=24&direction=ASC&orderBy=id` - GET: Obtém clientes em uma página

### Categorias

- `/categorias` - GET: Obtém todos as categorias
- `/categorias` - POST: Cadastro de categoria

    ```
    {
        "nome": "Informática"
    }
    ```

- `/categorias/{id}` - GET: Obtém uma categoria por id
- `/categorias/{id}` - PUT: Atualização de categoria por id

    ```
    {
        "nome": "Informática"  
    }
    ```

- `/categorias/{id}` - DELETE: Deleção de categoria por id
- `/categorias/pages?page=0&linesPerPage=24&direction=ASC&orderBy=id` - GET: Obtém categorias em uma página

### Pedidos

- `/pedidos/{id}` - GET: Obtém todos um pedido por id
- `/pedidos/{id}` - POST: Cadastra um pedido por id

    ```
    {
        "cliente": {
            "id": 1
        },
        "endereco": {
            "id": 1
        },
        "pagamento": {
            "numeroDeParcelas: 10,
            "@type": "pagamentoComCartao
        },
        "itens": [
            {
                "quantidade": 2,
                "produto": {
                    "id": 3
                }
            },
            {
                "quantidade: 4,
                "produto": {
                    "id": 2
                }
            }
        }
    }
    ```

### Produtos

- `/produtos/{id}` - GET: Obtém um pedido
- `/produtos?nome=""&categorias=""&page=0&linesPerPage=24&direction=ASC&orderBy=nome` - GET: Obtém produtos em uma página

### Login
- `/login` - POST: Faz login de um usuário com email e senha

    ```
    {
        "email: "donniedarko@gmail.com",
        "senha": donnie123
    }
    ```

[//]: # (### Auth)

[//]: # (- `/auth/refresh_token` - POST: Gera um novo token pra um usuário logado com token prestes a expirar)

[//]: # (- `/auth/forgot` - POST: Gera um nova senha e a envia por email)

## Notas

Endpoints `/produtos/**`, `/categorias/**` e `/clientes/**` não necessitam de autenticação
O endpoint `/h2-console` só funciona no ambiente de test

## Tecnologias

- Java 17

- Spring Boot 2.6.2

- Spring Framework 5.13.14

- Spring Data JPA 2.6.0

- Spring Security 5.6.1

- Thymeleaf 3.0.14

- Lombok 1.18.22

- H2 2.1.210

- MySQL Connector 8.0.28

- JWT Support For The JVM 0.9.1



