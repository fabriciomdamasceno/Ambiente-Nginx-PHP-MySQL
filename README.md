
Ambiente de desenvolvimento Docker com Nginx + PHP e MySQL

**Pré-requisitos:** Ter o Docker e Docker-compose instalados.


[Instalando Docker no Windows 10](https://www.mundodocker.com.br/docker-no-windows-10/)

[Instalando Docker e utilizando Docker no Linux. Docker-compose no Linux (qualquer distro)](https://mundodacomputacaointegral.blogspot.com/2019/10/instalando-docker-e-docker-compose-no-Linux.html)

Após ter instalado o Docker e Docker-compose, segue os procedimentos: 

1. Fork do repositório

2. Clonar o repositório forkado

3. Acessar o diretório onde salvou o clone do repositório

4. Execute `docker-compose up -d`

5. Adicione no arquivo hosts

   **Windows:** _C:\Windows\System32\drivers\etc\hosts_

   **Linux:** _/etc/hosts_

    `127.0.0.1 php.local`
 
    `127.0.0.1 laravel.local`
   
6. Acessar o container PHP para instalar novos projetos Laravel ou atualizar via composer.
   `docker exec -it app bash`
   
   Dentro do container PHP, ao digitar pwd você pode constatar que você está no diretório _/var/www/html/_.

   Você pode acessar o diretório `laravel` através do comando `cd laravel` e digitar `composer update` para baixar e atualizar as dependencias do projeto Laravel.

   Para criar um novo projeto laravel, basta digitar o comando abaixo em _/var/www/html_

   `composer create-project --prefer-dist laravel/laravel Nome_Do_Projeto`
   
7. No browser acesse [http://php.local](http://php.local) ou [http://laravel.local](http://laravel.local)

8. Esse ambiente de desenvolvido inclui 2 Vhosts no Nginx de exemplo para 2 projetos, mas pode ter N vhosts, basta reutilizar um dos arquivos de acordo com a necessidade do seu novo projeto. Para isso, basta renomear o arquivo _php.conf_ ou _laravel.conf_ para o novo arquivo, alterando o _server_name_ e adicionar no _Dockerfile_ do PHP. Lembrar de adicionar no arquivo hosts para cada Vhost do projeto.

9. No Linux para ter permissão no volume _src/php_ e _src/laravel_, acessa até o diretório do ambiente e execute:

   `sudo chown -R $(whoami):$(whoami) src/php` 

   `sudo chown -R $(whoami):$(whoami) src/laravel`
  
10. No Laravel Framework precisa editar o _src/laravel/.env_ em _APP_NAME=_ para _laravel.local_ que nesse caso é o ServerName definido no Vhost. Para os demais Vhosts que houver também.

11. Para acessar a Base de Dados é simples. Basta usar qualquer Software de Acesso da sua máquina local com a senha de acesso que está no arquivo docker-compose.yml que está na raiz desse projeto.

Prontinho!


