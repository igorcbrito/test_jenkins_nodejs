# test_jenkins_nodejs
Aplicação de um projeto de testes unitários com node.js e jenkins

## Instalar o Docker
Por conta da utilização do sistema operacional Windows, a escolha de instalação do Docker foi feita através do Docker Toolbox.
Basta baixar o executável em https://github.com/docker-archive/toolbox/releases e avançar as etapas. Depois basta iniciar o Quick Start Temrinal para que a docker machine seja configurada.

### Subir o container do Jenkins

Criar uma rede de ponte no Docker: 

`docker network create skynet`

Criar um volume para persistir os dados Jenkins:

`docker volume create jenkins-data`

Fazer download da imagem jenkinsci/blueocean:

`docker pull jenkinsci/blueocean`

No MacOS ou Linux, usar o comando para executar o container docker com Jenkins:

`docker container run --name jenkins-blueocean --detach \
  --network skynet -u root \
  --volume jenkins-data:/var/jenkins_home \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  --publish 8080:8080 --publish 50000:50000 jenkinsci/blueocean`
  
 No Windows:
 
`docker container run --name jenkins-blueocean --detach ^
  --network skynet -u root ^
  --volume jenkins-data:/var/jenkins_home ^
  --volume /var/run/docker.sock:/var/run/docker.sock ^
  --publish 8080:8080 --publish 50000:50000 jenkinsci/blueocean`



