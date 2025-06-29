# Microserviço de um Sistema de Pagamentos

Este projeto é uma aplicação desenvolvida com arquitetura de microsserviços, que simula o fluxo de pedidos e pagamentos dentro de um sistema distribuído. Ele é composto por quatro serviços: Eureka Server, API Gateway, Pedidos e Pagamentos, que se comunicam entre si via REST utilizando Feign para integração e Resilience4j para tolerância a falhas. O Gateway centraliza o acesso às rotas e facilita a comunicação entre os microsserviços. O projeto também realiza controle de status de pedidos e pagamentos, versionamento de banco de dados com Flyway e pode ser facilmente testado com ferramentas como o Postman.

---
## Tecnologias utilizadas

- Java 21
- Spring Boot 3
- MySQL
- Flyway
- Spring Cloud OpenFeign
- Resilience4j
- Eureka
- Postman 
---
## Rotas do nosso Microserviço

### Rotas do serviço de pedidos
- **Listar todos (GET):** 


    http://localhost:8082/pedidos-ms/pedidos

- **Listar por Id (GET):**


    http://localhost:8082/pedidos-ms/pedidos/{id}

- **Criar um Pedido (POST):**


    http://localhost:8082/pedidos-ms/pedidos

- **Atualizar status pedido (PUT):**


    http://localhost:8082/pedidos-ms/pedidos/{id}/status

- **Definir o pedido como pago (PUT):**

    
    http://localhost:8082/pedidos-ms/pedidos/{id}/pago

### Rotas do serviço de pagamentos

- **Listar todos os pagamentos (GET):**


    http://localhost:8082/pagamentos-ms/pagamentos

- **Listar todos os pagamentos (GET):**


    http://localhost:8082/pagamentos-ms/pagamentos/{id}

- **Cadastrar um Pagamento (POST):**


    http://localhost:8082/pagamentos-ms/pagamentos

- **Atualizar Pagamento (PUT):**


    http://localhost:8082/pagamentos-ms/pagamentos/{id}

- **Excluir pagamento (DELETE):**


    http://localhost:8082/pagamentos-ms/pagamentos/{id}

- **Confirmar um pagamento (Patch):**


    http://localhost:8082/pagamentos-ms/pagamentos/{id}/confirmar


**Obs**: Ao utilizar a rota de confirmação de pagamento, o status do pagamento será atualizado para REALIZADO. Em seguida, o sistema acionará, via Feign, a funcionalidade responsável por alterar o status do pedido no serviço de pedidos, garantindo que ambos fiquem sincronizados.

---
## Como executar o Projeto

- Clone os repositórios de cada serviço: Server, Gateway, Pedidos e Pagamentos.
- Verifique as configurações do banco de dados e a disponibilidade das portas; o projeto usa a senha padrão do MySQL (root), ajuste se necessário no application.properties.
- Inicie primeiro o servidor Eureka (Server).
- Em seguida, suba o Gateway.
- Por fim, execute os serviços de Pedidos e Pagamentos na ordem que preferir.

