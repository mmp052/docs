# Product API

A Order API é uma API REST desenvolvida em **Java** utilizando o framework **SpringBoot**. A API permite ao usuário realizar a criação, listagem e deleção de um pedido. 

A API possui os seguintes endpoints:

!!! info "POST /order"

    Create a new order **for the current user**.

    === "Request"

        ``` { .json .copy .select linenums='1' }
        {
            "items": [
                {
                    "idProduct": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
                    "quantity": 2
                },
                {
                    "idProduct": "0195abfe-e416-7052-be3b-27cdaf12a984",
                    "quantity": 1
                }
            ]
        }
        ```

    === "Response"

        ``` { .json .copy .select linenums='1' }
        {
            "id": "0195ac33-73e5-7cb3-90ca-7b5e7e549569",
            "date": "2025-09-01T12:30:00",
            "items": [
                {
                    "id": "01961b9a-bca2-78c4-9be1-7092b261f217",
                    "product": {
                        "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8"
                    },
                    "quantity": 2,
                    "total": 20.24
                },
                {
                    "id": "01961b9b-08fd-76a5-8508-cdb6cd5c27ab",
                    "product": {
                        "id": "0195abfe-e416-7052-be3b-27cdaf12a984"
                    },
                    "quantity": 10,
                    "total": 6.2
                }
            ],
            "total": 26.44
        }
        ```
        ```bash
        Response code: 201 (created)
        Response code: 400 (bad request), if the product does not exist.
        ```

!!! info "GET /order"

    Get all orders **for the current user**.

    === "Response"

        ``` { .json .copy .select linenums='1' }
        [
            {
                "id": "0195ac33-73e5-7cb3-90ca-7b5e7e549569",
                "date": "2025-09-01T12:30:00",
                "total": 26.44
            },
            {
                "id": "0195ac33-cbbd-7a6e-a15b-b85402cf143f",
                "date": "2025-10-09T03:21:57",
                "total": 18.6
            }
            
        ]
        ```
        ```bash
        Response code: 200 (ok)
        ```

!!! info "GET /order/{id}"

    Get the order details by its ID. **The order must belong to the current user.**, otherwise, return a `404`.

    === "Response"

        ``` { .json .copy .select linenums='1' }
        {
            "id": "0195ac33-73e5-7cb3-90ca-7b5e7e549569",
            "date": "2025-09-01T12:30:00",
            "items": [
                {
                    "id": "01961b9a-bca2-78c4-9be1-7092b261f217",
                    "product": {
                        "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
                    },
                    "quantity": 2,
                    "total": 20.24
                },
                {
                    "id": "01961b9b-08fd-76a5-8508-cdb6cd5c27ab",
                    "product": {
                        "id": "0195abfe-e416-7052-be3b-27cdaf12a984",
                    },
                    "quantity": 10,
                    "total": 6.2
                }
            ],
            "total": 26.44
        }
        ```
        ```bash
        Response code: 200 (ok)
        Response code: 404 (not found), if the order does not belong to the current user.
        ```

A API está disponível nos seguintes repositórios: [Order](https://github.com/mmp052/order){target="_blank"} e [Order Service](https://github.com/mmp052/order-service).

## Estrutura do Projeto 

### Interface da API

A estrutura da interface da OrderAPI é organizada da seguinte forma:

```
order/
├── src/main/java/store/order/
│    ├── ItemIn.java
│    ├── ItemOut.java
│    ├── OrderController.java
│    ├── OrderIn.java
│    ├── OrderOut.java
|    ├── ProductOut.java
|    ├── ProductRef.java
├── Jenkinsfile
└── pom.xml
```

### Implementação da API

A implementação completa da OrderAPI segue a estrutura abaixo:

```
order-service/
├── k8s/
│   ├── k8s.yaml
├── src/main/
│   ├── java/store/order/
│   │   ├── Item.java
│   │   ├── ItemModel.java
│   │   ├── ItemRepository.java
│   │   ├── Order.java
│   │   ├── OrderApplication.java
│   │   ├── OrderModel.java
│   │   ├── OrderParser.java
│   │   ├── OrderRepository.java
│   │   ├── OrderResource.java
│   │   └── OrderService.java
│   └── resources/
│       ├── db/migration/
│       │   ├── V2025.02.21.001__create_schema_account.sql
│       │   └── V2025.02.21.002__create_table_account.sql
│       └── application.yaml
├── Jenkinsfile
└── pom.xml

```

## Código-fonte

### Interface da API

=== "ItemIn.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/ItemIn.java"
    ```

=== "ItemOut.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/ItemOut.java"
    ```

=== "OrderController.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/OrderController.java"
    ```

=== "OrderIn.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/OrderIn.java"    
    ```

=== "OrderOut.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/OrderOut.java"
    ```

=== "ProductOut.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/ProductOut.java"
    ```

=== "ProductRef.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/src/main/java/store/order/ProductRef.java"
    ```

=== "pom.xml"
    ``` { .xml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order/main/pom.xml"
    ```

### Implementação da API

=== "Item.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/Item.java"
    ```

=== "ItemModel.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/ItemModel.java"
    ```

=== "ItemRepository.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/ItemRepository.java"
    ```

=== "Order.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/Order.java"
    ```

=== "OrderApplication.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/OrderApplication.java"    
    ```

=== "OrderModel.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/OrderModel.java"
    ```

=== "OrderParser.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/OrderParser.java"
    ```

=== "OrderRepository.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/OrderRepository.java"
    ```

=== "OrderResource.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/OrderResource.java"
    ```

=== "OrderService.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/src/main/java/store/order/OrderService.java"
    ```

=== "pom.xml"
    ``` { .xml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/order-service/main/pom.xml"
    ```