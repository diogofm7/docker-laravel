## Requisitos
- Docker
- Docker Compose
- Traefik    

## Iniciar Serviços

1. Criar arquivo .env

    ```sh 
    cp .env-exemple .env
    ```


2. Editar arquivo .env com informações do projeto

    ```sh
    vim .env
    ```
   
3. Criar pasta app

    ```sh
    mkdir app
    ```

4. Rodar comndo docker-compose
    
    ```sh
   docker-compose up -d
    ```