# Desafio QE - API

## Informações Projeto
Testar uma aplicação que é responsável por gerenciar produtos eletrônicos, onde o devemos garantir que a aplicação está funcionando corretamente de acordo com a documentação.

### Ferramentas
- Linguagem JAVA
- Biblioteca RestAssured
- IDE Intellij

## Como executar
- Entender os requisitos
- Documentar resultado esperado
- Validar fluxo de trabalho da aplicação
- Validar integrações a API
-Configurar o ambiente com base nos requisitos da API
   
## Objetivo
O objetivo principal é garantir que a API REST forneça respostas corretas, consistentes e seguras de acordo com as especificações.

## Eestratégia de testes
### Teste de Unidade
- Objetivo: Verificar a funcionalidade de cada método ou endpoint individualmente.
- Ação:
  - Testar cada endpoint com uma variedade de entradas válidas e inválidas.
  - Verificar se os dados retornados são os esperados.
  - Validar se os códigos de status HTTP estão corretos.
### Testes de Integração
- Objetivo: Garantir que os diferentes componentes da API funcionem corretamente juntos.
- Ação:
  - Testar as chamadas entre endpoints, garantindo que a comunicação seja efetiva.
  - Verificar se as respostas de um endpoint são usadas corretamente como entrada para outros.
### Testes de Funcionalidade
- Objetivo: Validar a funcionalidade da API como um todo.
- Ação:
  - Testar cenários de uso comum da API.
  - Garantir que todas as funcionalidades principais estejam operando corretamente.
  - Testar a manipulação adequada de dados de entrada e saída.
### Testes de Segurança
- Objetivo: Identificar e mitigar potenciais vulnerabilidades de segurança.
- Ação:
  - Verificar se a comunicação é segura (HTTPS).
  - Implementar e testar autenticação e autorização.
  - Realizar testes de segurança, como injeção de SQL e XSS.
### Testes de Exceção
- Objetivo: Avaliar o comportamento da API em situações inesperadas.
- Ação:
  - Enviar dados inválidos para a API e verificar se ela responde adequadamente.
  - Testar casos de erro, garantindo que os códigos de status e mensagens de erro sejam apropriados.
### Testes de Documentação
Confirmar se a documentação da API está precisa e completa.
  - Comparar os resultados dos testes com a documentação.
  - Validar se todos os parâmetros, métodos e respostas estão bem documentados.

## Ambiente
Configurar ambientes de teste separados para desenvolvimento, teste e produção, se possível.

## Cronograma
Estabelecer um cronograma de execução dos testes, incluindo testes automáticos e manuais.

## Relatórios
Gerar relatórios detalhados sobre os resultados dos testes, destacando problemas encontrados e áreas de melhoria.

## Casos de teste
### GET /test
Buscar o status da aplicação corretamente ao enviar uma solicitação GET para o endpoint '/test'.
- Dado que:
  - Request curl --location 'dummyjson.com/test'
- Quando:
  - Response 200 OK
- Então:  
  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20test_200%20OK.png)

### GET /users
Buscar usuário para autenticação corretamente ao enviar uma solicitação GET para o endpoint '/users'.
- Dado que:
  - Request curl --location 'dummyjson.com/users'
- Quando:
  - Response 200 OK
- Então:  
![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20users_200%20OK.png)

### POST /auth/login
Criação de token para Autenticação corretamente ao enviar uma solicitação POST para o endpoint '/auth/login'.
- Dado que:
 ![Web 1](https://github.com/BiankaLima/imagens/blob/main/POST%20auth%20login_Request.png)
  - E JSON
 ![Web 1](https://github.com/BiankaLima/imagens/blob/main/POST%20auth%20login_request%20json.png)
- Quando:
  - Response 201 OK
- Então:  
![Web 1](https://github.com/BiankaLima/imagens/blob/main/POST%20auth%20login_201%20OK.png)

### GET /auth/products
Buscar produtos com autenticação corretamente ao enviar uma solicitação GET para o endpoint '/auth/products'.
- Dado que:
  -  curl --location 'dummyjson.com/auth/products' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer /* YOUR_TOKEN_HERE */'
- Quando:
  -  Response 200 OK
- Então:  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20auth%20products_200OK.png)

- Dado que:
  -  curl --location 'dummyjson.com/auth/products' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer /* YOUR_TOKEN_HERE */'
- Quando:
  -  Response 403 Forbidden
- Então:  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20auth%20products_403.png)

- Dado que:
  -  curl --location 'dummyjson.com/auth/products' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer /* YOUR_TOKEN_HERE */'
- Quando:
  -  Response 401 Unauthorized
- Então:  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20auth%20products_401.png)

### POST /products/add
Criar produto corretamente ao enviar uma solicitação POST para o endpoint '/products/add'.
- Dado que:
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/POST%20product%20add_request.png)
- Quando:
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/POST%20product%20add_request%20body%20json.png)
- Então:
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/POST%20product%20add_201%20OK.png)
  
Note: Os produtos criados não serão persistidos.

### GET /products
Buscar todos os produtos corretamente ao enviar uma solicitação GET para o endpoint '/products'.
- Dado que:
  - Request curl --location 'dummyjson.com/products'
- Quando:
  -  Response 200 OK
    
- Então:
  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20products%20_200%20OK.png)

### GET /products/{id}
Buscar todos os produtos corretamente ao enviar uma solicitação GET para o endpoint '/products/{id}'.
- Dado que:
  - Request curl --location 'dummyjson.com/products/1'
- Quando:
  -  Response 200 OK
    
- Então:
  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20products%20ID%20_200%20OK.png)
- Dado que:
  - Request curl --location 'dummyjson.com/products'
- Quando:
  -  Response 404 Not found
    
- Então:
  
  ![Web 1](https://github.com/BiankaLima/imagens/blob/main/GET%20products%20ID%20_404%20NOK.png)

## Bugs



## Melhorias
- No response do GET /test, não retorna o "password" do usuario
