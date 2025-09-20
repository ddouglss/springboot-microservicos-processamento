
# 📦 Microserviço de Processamento

Este projeto é parte de uma arquitetura de microsserviços que utiliza RabbitMQ para mensageria e PostgreSQL para persistência.
O Processamento Service é responsável por consumir mensagens de pedidos e realizar o processamento.

#### Repositorio do pedido:
- <a href=https://github.com/ddouglss/springboot-microservicos-pedido>microservicos-pedido</a>


## 🚀 Tecnologias Utilizadas

- Java 21

- Spring Boot 3.5.4

- Spring AMQP

- Spring Data JPA

- PostgreSQL

- RabbitMQ (CloudAMQP)
## 📂 Estrutura do Projeto

```
processamento/
 ├── src/main/java/dg/microservicos/processamento/
 │    ├── config/         # Configuração do RabbitMQ
 │    ├── consumer/       # Listener da fila
 │    ├── dto/            # DTO de Pedido
 │    ├── ProcessamentoApplication.java
 │
 ├── src/main/resources/
 │    ├── application.properties
 │
 └── pom.xml              # Configurações do Maven
```
## ⚙️ Configuração

#### Banco de Dados

O serviço utiliza PostgreSQL como banco de dados.

```
spring.datasource.url=jdbc:postgresql://localhost:5432/ms-processamento
spring.datasource.username=postgres
spring.datasource.password=aurora
spring.jpa.hibernate.ddl-auto=update

```
## RabbitMQ

A fila de mensagens é configurada via CloudAMQP.

```
spring.rabbitmq.addresses=amqps://USUARIO:SENHA@HOST/INSTANCIA
broker.queue.processamento.name=exchange.processamento
```
## ▶️ Como Rodar

#### Pré-requisitos

- Java 21+

- Maven 3.9+

- PostgreSQL rodando localmente

- Instância do RabbitMQ (pode ser local ou CloudAMQP)

#### Passos

## Clone o repositório:

```
git clone https://github.com/seu-usuario/ms-processamento.git
cd ms-processamento
```


#### Compile e rode o projeto:

```
mvn spring-boot:run
```

#### O serviço estará disponível em:

```
http://localhost:8082
```
## 🔄 Fluxo de Mensagens

- O Pedido Service publica uma mensagem (JSON) na fila exchange.processamento.

- O Processamento Service consome essa mensagem via ProcessamentoConsumer.

- A mensagem é logada/armazenada para processamento posterior.
## 🧪 Testes

O projeto inclui dependências para testes com JUnit, TestNG e Spring RabbitMQ Test.
Para rodar:

```
mvn test
```
