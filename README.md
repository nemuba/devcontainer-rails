# DevContainer Rails

Este projeto configura um ambiente de desenvolvimento para uma aplicação Rails usando DevContainers.

## Ruby Version
- Ruby 3.1.0

## System Dependencies
- Docker
- Docker Compose

## Configuration
1. Clone o repositório:
   ```sh
   git clone https://github.com/nemuba/devcontainer-rails.git
   cd devcontainer-rails
   ```

2. Configure variáveis de ambiente:
   Crie um arquivo `.env` com as variáveis necessárias.

## Database Creation
1. Inicie os containers:
   ```sh
   docker-compose up -d
   ```

2. Crie o banco de dados:
   ```sh
   docker-compose exec app bundle exec rake db:create
   ```

## Database Initialization
1. Rode as migrações:
   ```sh
   docker-compose exec app bundle exec rake db:migrate
   ```

2. Popule o banco de dados com dados iniciais (se aplicável):
   ```sh
   docker-compose exec app bundle exec rake db:seed
   ```

## How to Run the Test Suite
1. Execute os testes:
   ```sh
   docker-compose exec app bundle exec rspec
   ```

## Services
- Servidor Redis para filas de trabalho
- Memcached para cache

## Deployment Instructions
1. Compile os assets:
   ```sh
   docker-compose exec app bundle exec rake assets:precompile
   ```

2. Inicie o servidor em modo produção:
   ```sh
   docker-compose -f docker-compose.prod.yml up -d
   ```
