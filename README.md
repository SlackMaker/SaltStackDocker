# Ambiente de teste realizado com Docker SaltStack no CentOS 
Configurando o Docker Compose para rodar o salt-master e minions.

# Guia rápido

*Instalar Docker e Docker-Compose*

Clonar o repositório abaixo:

`$ git fork https://github.com/SlackMaker/SaltStackDocker.git`

`$ cd SaltStackDocker`

Inicie o Master and Minion:

`$ docker-compose up`

*Esta janela exibirá a saída de depuração do Salt Master e dos Minions*

Abra um novo terminal e verifique se você está SaltStack-Docker-Dev-Env/

Faça login no seu Master:

`$ docker-compose exec salt-master bash`

ou utilize

`$ chmod +x master-login.sh`

`$ ./master-login.sh`

Faça login no seu Minion:

`$ docker-compose exec salt-minion bash`

ou utilize

`$ chmod +x minion-login.sh`

`$ ./minion-login.sh`

Agora realize um teste de ping do seu Master:

`$ salt '*' test.ping`

*O salt-master está configurado para aceitar todas as conexões dos minions que tentam se conectar. Apenas minions dentro da rede de serviço do docker-compose serão capazes de se connectar*

# Executando Múltiplos Minions:

`$ docker-compose up --scale salt-minion=2`

*Se você estiver executando mais de um minion with `--scale=2`, você precisará usar `docker-saltstack_salt-minion_1` e `docker-saltstack_salt-minion_2` para os minions se quiser acessá-los individualmente.*

# Nomes dos Hosts
Os **hostnames** correspondem aos nomes dos contêineres, então o nome do salt master é `salt-master` e o nome do salt minion é `salt-minion`.

# Atualização de compilação de SO utilizando Docker-Compose

*Se necessário, você pode realizar alterações na instância do Docker, incluindo a adição de pacotes binários adicionais à pilha do docker, executando o seguinte:*

`$ cd /SaltStackDocker`

Faça as alterãções necessárias no DockerFile(s) e salve os arquivos

`$ docker-compose build`

`$ docker-compose up`
