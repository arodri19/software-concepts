Aqui está um exemplo de um arquivo `docker-compose.yml` que define um serviço web e um serviço de banco de dados:

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8000:80"
    volumes:
      - ./web:/usr/share/nginx/html
    networks:
      - mynetwork
    environment:
      - NGINX_HOST=example.com
      - NGINX_PORT=80

  db:
    build:
      context: ./db
      dockerfile: Dockerfile
    volumes:
      - ./db-data:/var/lib/postgresql/data
    networks:
      - mynetwork
    environment:
      - POSTGRES_USER=myuser
      - POSTGRES_PASSWORD=mypassword
      - POSTGRES_DB=mydb

networks:
  mynetwork:
```

Neste exemplo:

- `web` é um serviço que usa a imagem `nginx:latest`, mapeia a porta 8000 do host para a porta 80 do contêiner, monta o diretório `./web` do host no diretório `/usr/share/nginx/html` do contêiner, usa a rede `mynetwork` e define algumas variáveis de ambiente.
- `db` é um serviço que usa a imagem `postgres:latest`, monta o diretório `./db-data` do host no diretório `/var/lib/postgresql/data` do contêiner, usa a rede `mynetwork` e define algumas variáveis de ambiente.
- `mynetwork` é uma rede que é usada pelos serviços `web` e `db`.

Para iniciar os serviços definidos neste arquivo `docker-compose.yml`, você usaria o comando `docker-compose up`:

```bash
docker-compose up
```

```bash
docker-compose up -d
```


Lembre-se de substituir `./web`, `./db-data`, `example.com`, `80`, `myuser`, `mypassword`, `mydb` e `mynetwork` pelos valores reais que você deseja usar.