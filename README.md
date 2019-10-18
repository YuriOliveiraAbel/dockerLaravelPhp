# CONTAINER DOCKER COM LARAVEL, PHP, MYSQL, POSTGRESQL


1. Na pasta raiz do container executar o comando: 
    docker-compose up -d --build (construir o container)
    
2. Verificar a execução do container com o comando:
    docker ps
    
3. Verificar as portas de configuração no arquivo docker-compose.yml, como padrão o apache vem executando o php na porta 3000 executar o    localhost:3000 no navegador

4. Criar o projeto laravel a partir da documentação, irá cria-lo junto as pastas do container.
    4.1 composer global require laravel/installer
    4.2 composer create-project laravel/laravel testeguzzle --prefer-dist v6

5. Mapear o caminho do public do projeto no arquivo apache.conf dentro da pasta container.

6. Rebuidar o container:
    docker stop db_container php_container
    docker-compose rm -v
    docker-compose up -d --build
    
PRONTO
