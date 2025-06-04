# Jenkins

Nesta etapa, o Jenkins foi utilizado para o desenvolvimento de um pipeline completo de CI/CD para automotização do deploy de uma aplicação em nuvem. A AWS foi escolhida como provedor de nuvem, sendo utilizado o Amazon EKS como o ambiente de produção.

A pipeline desenvolvida incluí as seguintes etapas:

1. SCM
1. Dependencies
1. Build
1. Push to Docker Hub
1. Deploy to K8s

## Estrutura do Projeto

Todos os microsserviços tiveram o deploy realizado no mesmo cluster, para isso, foi criado um Jenkinsfile em cada uma das API's desenvolvidas. 

A estrutura básica de diretórios para o projeto é a seguinte:

``` { .bash }
.
├── account-service
│   ├── Jenkinsfile
│   └── ...
```

## Código-fonte

### Jenkinsfile para Interface da API

=== "Account"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/account/refs/heads/main/Jenkinsfile"
    ```

=== "Auth"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/auth/refs/heads/main/Jenkinsfile"
    ```

=== "Product"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product/refs/heads/main/Jenkinsfile"
    ```

=== "Order"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/refs/heads/main/Jenkinsfile"    
    ```

### Jenkinsfile para Implementação da API

=== "Account Service"
    ``` { .groovy .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/account-service/refs/heads/main/Jenkinsfile"
    ```

=== "Auth Service"
    ``` { .groovy .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/auth-service/refs/heads/main/Jenkinsfile"
    ```

=== "Gateway Service"
    ``` { .groovy .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/gateway-service/refs/heads/main/Jenkinsfile"
    ```

=== "Product Service"
    ``` { .groovy .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/refs/heads/main/Jenkinsfile"
    ```

=== "Order Service"
    ``` { .groovy .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/refs/heads/main/Jenkinsfile"    
    ```