Aqui estão alguns dos principais comandos do Docker com exemplos:

1. **docker run**: Este comando é usado para iniciar um contêiner. Por exemplo, para iniciar um contêiner com a imagem do Ubuntu, você usaria:

```bash
docker run ubuntu
```

2. **docker ps**: Este comando lista todos os contêineres em execução. Para listar todos os contêineres, incluindo os que não estão em execução, use `docker ps -a`.

```bash
docker ps
```

3. **docker pull**: Este comando é usado para puxar imagens do Docker Hub.

```bash
docker pull ubuntu
```

4. **docker build**: Este comando é usado para construir uma imagem a partir de um Dockerfile.

```bash
docker build -t my-image:1.0 .
```

5. **docker images**: Este comando lista todas as imagens Docker.

```bash
docker images
```

6. **docker rm**: Este comando remove um ou mais contêineres.

```bash
docker rm my-container
```

7. **docker rmi**: Este comando remove uma ou mais imagens.

```bash
docker rmi my-image
```

8. **docker exec**: Este comando executa um comando em um contêiner em execução.

```bash
docker exec -it my-container bash
```

9. **docker stop**: Este comando para um ou mais contêineres.

```bash
docker stop my-container
```

10. **docker start**: Este comando inicia um ou mais contêineres.

```bash
docker start my-container
```

Lembre-se de substituir "my-container" e "my-image" pelos nomes dos seus contêineres e imagens.

Você pode mapear uma porta do host para uma porta do contêiner Docker usando a opção `-p` ou `--publish` com o comando `docker run`. O formato é `hostPort:containerPort`.

Aqui está um exemplo:

```bash
docker run -p 8080:80 my-image
```

Neste exemplo, a porta 8080 do host é mapeada para a porta 80 do contêiner. Isso significa que se o aplicativo dentro do contêiner estiver ouvindo na porta 80, você poderá acessá-lo na porta 8080 do host.

Se você quiser mapear mais de uma porta, pode fazer isso adicionando mais opções `-p`, como neste exemplo:

```bash
docker run -p 8080:80 -p 8081:81 my-image
```

Neste exemplo, a porta 8080 do host é mapeada para a porta 80 do contêiner e a porta 8081 do host é mapeada para a porta 81 do contêiner.

Você pode listar todos os contêineres em execução no Docker usando o comando `docker ps`.

```bash
docker ps
```

Este comando mostrará uma lista de todos os contêineres Docker atualmente em execução, juntamente com informações como o ID do contêiner, a imagem a partir da qual o contêiner foi criado, o comando que está sendo executado no contêiner, quando o contêiner foi criado, o status do contêiner, as portas que estão expostas e o nome do contêiner.

Se você quiser listar todos os contêineres, incluindo os que não estão em execução, você pode usar a opção `-a` ou `--all`.

```bash
docker ps -a
```

Aqui está um exemplo de comando Docker que inclui mapeamento de porta, montagem de volume, especificação de rede e definição de variáveis de ambiente:

```bash
docker run -d \
  --name=my-container \
  -p 8080:80 \
  -v /host/directory:/container/directory \
  --network=my-network \
  -e "ENV_VAR_NAME=value" \
  my-image
```

Neste exemplo:

- `-d` executa o contêiner em segundo plano e imprime o ID do contêiner.
- `--name=my-container` dá um nome ao contêiner para que você possa referenciá-lo mais tarde.
- `-p 8080:80` mapeia a porta 8080 do host para a porta 80 do contêiner.
- `-v /host/directory:/container/directory` monta o diretório do host `/host/directory` no diretório do contêiner `/container/directory`.
- `--network=my-network` especifica que o contêiner deve usar a rede `my-network`.
- `-e "ENV_VAR_NAME=value"` define uma variável de ambiente chamada `ENV_VAR_NAME` com o valor `value`.
- `my-image` é a imagem a partir da qual o contêiner é criado.

Lembre-se de substituir `/host/directory`, `/container/directory`, `my-network`, `my-container`, `ENV_VAR_NAME`, `value` e `my-image` pelos valores reais que você deseja usar.