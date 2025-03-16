# Configuração e Execução do Projeto

Este repositório contém a configuração para rodar um container com suporte a PostgreSQL e Redis. Abaixo estão as instruções para configurar e subir o container.

## Pré-requisitos

- Docker instalado na máquina.
- Docker Compose (opcional, mas recomendado).

## Passos para Configuração

1. **Clone o repositório**:
   ```bash
   git clone [(https://github.com/RosnerTech/evolution-api.git)]
   cd seu-repositorio
   Configure as variáveis de ambiente:

Renomeie o arquivo .env.exemplo para .env:

bash
Copy
mv .env.exemplo .env
Edite o arquivo .env e substitua os valores das variáveis pelos seus dados:

env
Copy
POSTGRES_USER=SEU_USUARIO
POSTGRES_PASSWORD=SUA_SENHA
POSTGRES_DB=SEU_BD

AUTHENTICATION_API_KEY=SUA_KEY

DATABASE_ENABLED=true
DATABASE_PROVIDER=postgresql
DATABASE_CONNECTION_URI=postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@postgres:5432/${POSTGRES_DB}?schema=public
DATABASE_CONNECTION_CLIENT_NAME=evolution_exchange

DATABASE_SAVE_DATA_INSTANCE=true
DATABASE_SAVE_DATA_NEW_MESSAGE=true
DATABASE_SAVE_MESSAGE_UPDATE=true
DATABASE_SAVE_DATA_CONTACTS=true
DATABASE_SAVE_DATA_CHATS=true
DATABASE_SAVE_DATA_LABELS=true
DATABASE_SAVE_DATA_HISTORIC=true

CACHE_REDIS_ENABLED=true
CACHE_REDIS_URI=redis://redis:6379/6
CACHE_REDIS_PREFIX_KEY=SUA_KEY
CACHE_REDIS_SAVE_INSTANCES=false

CACHE_LOCAL_ENABLED=false
Observação: Substitua SEU_USUARIO, SUA_SENHA, SEU_BD, SUA_KEY e outros valores conforme necessário.

Subir o container:
Execute o seguinte comando para construir e subir o container:

bash
Copy
docker-compose up -d
Isso irá iniciar os serviços configurados no docker-compose.yml.

Verificar se está funcionando:
Para verificar se os containers estão rodando, use o comando:

bash
Copy
docker ps
Você deve ver os containers do PostgreSQL e Redis em execução.

Estrutura do Projeto
PostgreSQL: Banco de dados principal.

Redis: Cache para melhorar o desempenho.

Variáveis de Ambiente: Configurações personalizadas no arquivo .env.

Comandos Úteis
Parar os containers:

bash
Copy
docker-compose down
Visualizar logs:

bash
Copy
docker-compose logs -f
Acessar o banco de dados PostgreSQL:

bash
Copy
docker exec -it nome_do_container_postgres psql -U SEU_USUARIO -d SEU_BD
Acessar o Redis:

bash
Copy
docker exec -it nome_do_container_redis redis-cli
Contribuição
Se encontrar algum problema ou tiver sugestões, sinta-se à vontade para abrir uma issue ou enviar um pull request.

Arquivos do Projeto
docker-compose.yml: Arquivo de configuração do Docker Compose com os serviços PostgreSQL e Redis.

.env.exemplo: Exemplo de arquivo de variáveis de ambiente. Renomeie para .env e configure conforme necessário.
