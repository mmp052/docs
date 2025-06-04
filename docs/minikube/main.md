# MiniKube

O MiniKube foi escolhido como orquestrador Kubernets para a arquitetura de microsserviços desenvolvida. 

## Estrutura do Projeto

Todos os microsserviços tiveram o deploy realizado no mesmo cluster, para isso, foi criado uma pasta k8s com os arquivos necessários em cada uma das API's desenvolvidas. 

A estrutura básica de diretórios para o projeto é a seguinte:

``` { .bash }
.
├── account-service
│   ├── k8s/
│   │   ├── k8s.yaml 
│   └── ...
```

## Código Fonte

Os arquivos de configuração do MiniKube são apenas criados nos repositórios de implementação da API, ou seja, aqueles que possuem ´Service´ no nome.

### Postgres

=== "Postgres"
    ``` { .yaml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/db/refs/heads/main/k8s/k8s.yaml"
    ```

### Account Service

=== "k8s.yaml"
    ``` { .yaml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/account-service/refs/heads/main/k8s/k8s.yaml"
    ```
### Auth Service

=== "k8s.yaml"
    ``` { .yaml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/auth-service/refs/heads/main/k8s/k8s.yaml"
    ```

### Gateway Service

=== "k8s.yaml"
    ``` { .yaml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/gateway-service/refs/heads/main/k8s/k8s.yaml"
    ```

### Product Service

=== "k8s.yaml"
    ``` { .yaml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/refs/heads/main/k8s/k8s.yaml"
    ```

### Order Service

=== "k8s.yaml"
    ``` { .yaml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/refs/heads/main/k8s/k8s.yaml"
    ```

