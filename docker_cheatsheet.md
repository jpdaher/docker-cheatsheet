# Docker Cheatsheet
Lista de comandos docker para checagem rápida. Aqui estão somente comandos mais\
relevantes para uso diário. Para uma lista completa consulte a documentação oficial.

## Ajuda
`docker <COMANDO> --help` - Lista todos os parâmetros aceitos para o subcomando\
docker especificado.

## Container
`docker container ls` - Lista os containers em execução;

`docker container ls -a` - Lista todos os containers;

`docker container create <IMAGE_NAME>` - Cria um container sem executá-lo;

`docker container run --name <CONTAINER_NAME> <IMAGE_NAME>` - Cria e executa um\
novo container a partir da imagem especificada. Baixa a imagem se não estiver disponível\
localmente. O nome é opcional;

`docker container run -d <IMAGE_NAME>` - Cria e executa um novo container como\
daemon (em segundo plano);

`docker container run -m 512M <IMAGE_NAME>` - Cria e executa um novo container com\
memória limitada a 512mb;

`docker container run --cpus=0.5 <IMAGE_NAME>` - Cria e executa um novo container com\
uso de CPU limitado a meio core;

`docker container update -m <valor> --cpus=<valor> <CONTAINER_ID>` - Atualiza as\
limitações de uso de memória e CPU de um container;

`docker container attach <CONTAINER_ID>` - Volta para o terminal (caso exista)\
de um container em execução;

`docker container exec -it <CONTAINER_ID> <COMMAND>` - Executa o comando\
especificado em um container que está rodando em segundo plano. -it serve para\
alocar um terminal interativo ao comando. Útil, por exemplo, em containers que\
não iniciam com o bash;

`docker container pause|unpause <CONTAINER_ID>` - Pausa ou despausa um container;

`docker container start|stop -i|a <CONTAINER_ID>` - Inicia ou para um container\
existente. -it aloca um terminal interativo, -a te permite ver o STDOUT;

`docker container start|stop $(docker container ls -a -q)` - Inicia ou para todos\
os containers existentes

`docker container restart <CONTAINER_ID>` - Reinicia um container em execução;

`docker container inspect <CONTAINER_ID>` - Lista vários detalhes sobre o container;

`docker container stats <CONTAINER_ID>` - Acompanha em tempo real o uso de recursos\
de um container;

`docker container top <CONTAINER_ID>` - Lista os processos em execução em um container;

`docker container logs -f <CONTAINER_ID>` - Exibe e acompanha os logs de um container;

`docker container rm <CONTAINER_ID>` - Remove um container (mantém a imagem).

## Image
`docker image ls` - Lista todas as imagens disponíveis localmente;

`docker image pull <IMAGE_NAME>:<IMAGE_VERSION>` - Baixa uma imagem do repositório\
online. Se a versão for omitida, baixa a mais recente;

`docker image build -t <IMAGE_TAG> <PATH_TO_DOCKERFILE>` - Cria uma imagem a partir\
de uma dockerfile. Tag pode ser omitida, mas facilita a identificação. Uma tag\
geralmente é composta por `<IMAGE_NAME>`:`<IMAGE_VERSION>`;

`docker image tag <IMAGE_TAG> <NEW_IMAGE_TAG>` - Adiciona uma nova tag à imagem.\
Não remove a tag antiga;

`docker image inspect <IMAGE_NAME>` - Lista vários detalhes sobre a imagem;

`docker image prune` - Remove todas as imagens baixadas que não estão sendo usadas\
por nenhum container;

`docker image rm <IMAGE_NAME>` - Remove a imagem especificada do repositório local.

## Atalhos
`Ctrl + p + q` (em um container) - Se estiver em um terminal interativo, sai \
sem interromper a execução do container