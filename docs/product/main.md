# Product API

A Product API é uma API REST desenvolvida em **Java** utilizando o framework **SpringBoot**. A API permite ao usuário realizar a criação, listagem e deleção de um produto. 

A API possui os seguintes endpoints:

!!! info "POST /product"

    Create a new product.

    === "Request"

        ``` { .json .copy .select linenums='1' }
        {
            "name": "Tomato",
            "price": 10.12,
            "unit": "kg"
        }
        ```

    === "Response"

        ``` { .json .copy .select linenums='1' }
        {
            "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
            "name": "Tomato",
            "price": 10.12,
            "unit": "kg"
        }
        ```
        ```bash
        Response code: 201 (created)
        ```

!!! info "GET /product"

    Get all products.

    === "Response"

        ``` { .json .copy .select linenums='1' }
        [
            {
                "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
                "name": "Tomato",
                "price": 10.12,
                "unit": "kg"
            },
            {
                "id": "0195abfe-e416-7052-be3b-27cdaf12a984",
                "name": "Cheese",
                "price": 0.62,
                "unit": "slice"
            }
        ]
        ```
        ```bash
        Response code: 200 (ok)
        ```

!!! info "GET /product/{id}"

    Get a product by its ID.

    === "Response"

        ``` { .json .copy .select linenums='1' }
        {
            "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
            "name": "Tomato",
            "price": 10.12,
            "unit": "kg"
        }
        ```
        ```bash
        Response code: 200 (ok)
        ```

!!! info "DELETE /product/{id}"

    Delete a product by its ID.

    ```bash
    Response code: 204 (no content)
    ```

A API está disponível nos seguintes repositórios: [Product](https://github.com/mmp052/product){target="_blank"} e [Product Service](https://github.com/mmp052/product-service).

## Estrutura do Projeto 

### Interface da API

A estrutura da interface da ProductAPI é organizada da seguinte forma:

```
product/
│   ├── ProductController.java
│   ├── ProductIn.java
│   ├── ProductOut.java
├── Jenkinsfile
└── pom.xml
```

### Implementação da API

A implementação completa da ProductAPI segue a estrutura abaixo:

```
product-service/
├── k8s/
│   ├── k8s.yaml
├── src/main/
│   ├── java/store/product/
│   │   ├── Product.java
│   │   ├── ProductApplication.java
│   │   ├── ProductModel.java
│   │   ├── ProductParser.java
│   │   ├── ProductRepository.java
│   │   ├── ProductResource.java
│   │   └── ProductService.java
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

=== "ProductController.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product/main/src/main/java/store/product/ProductController.java"
    ```

=== "ProductIn.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product/main/src/main/java/store/product/ProductIn.java"    
    ```

=== "ProductOut.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product/main/src/main/java/store/product/ProductOut.java"
    ```

=== "pom.xml"
    ``` { .xml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product/main/pom.xml"
    ```

### Implementação da API

=== "Product.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/Product.java"
    ```

=== "ProductApplication.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/ProductApplication.java"    
    ```

=== "ProductModel.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/ProductModel.java"
    ```

=== "ProductParser.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/ProductParser.java"
    ```

=== "ProductRepository.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/ProductRepository.java"
    ```

=== "ProductResource.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/ProductResource.java"
    ```

=== "ProductService.java"
    ``` { .java .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/src/main/java/store/product/ProductService.java"
    ```

=== "pom.xml"
    ``` { .xml .copy .select linenums="1" }
    --8<-- "https://raw.githubusercontent.com/mmp052/product-service/main/pom.xml"
    ```