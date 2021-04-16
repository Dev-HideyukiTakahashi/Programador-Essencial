# :bulb:Dicas e comandos Docker
---
---

#### Alguns comandos.

* Quando nós acabamos de subir o Docker Engine, nós utilizamos esse comando para verificarmos as informações do nosso Docker Host: 
    * ####  `docker info`
---
* Nós utilizamos para listarmos as imagens que nós temos no nosso host:
    * #### `docker images`
        * Repository: repositório;
        * TAG: tag utilizada no repositório;
        * IMAGE ID: o id na nossa imagem;
        * Created: data de quando nós * criamos a nossa imagem;
        * Size: tamanho da imagem;
---
* Quando encontrarmos a imagem que precisamos para a nossa aplicação, nós precisamos baixar ela para o nosso host:
    * #### `docker pull (parametro)`
---
* Para que nós possamos criar um contêiner, nós precisamos de uma imagem. Caso você não tenha essa imagem no seu host ainda ele irá até o repositório central e irá baixar ela para o seu host, em seguida ele irá criar o contêiner:
    * #### `docker pull (nome da imagem)`
---
* Com esse comando é possível enviar imagens criadas por você para repositórios de imagens:
    * #### `docker push (nome da imagem)`
---
* Caso você tenha baixado uma imagem errada ou queira deletar alguma por um outro motivo, basta executar o comando a cima que ele deleta ela do seu host:
    * #### `docker rmi (nome da imagem)`
---
* Para verificar o status do nosso contêiner, execute o comando no terminal:
    * #### `docker ps`
---
* O comando inspect é responsável por informar todos os dados referentes à imagem:
    * #### `docker image inspect(nome da imagem)`
---

* Comando para que você possa executar seus containers a partir de uma imagem:
    * #### `docker run <parâmetros> <imagem> <CMD> <argumentos>`
Os parâmetros mais utilizados na execução do container são:
| Parâmetro |	Explicação
| --- | ---
|-d| 	Execução do container em background
|-i| 	Modo interativo. Mantém o STDIN aberto |mesmo sem console anexado
|-t| 	Aloca uma pseudo TTY
|--rm| 	Automaticamente remove o container |após finalização (Não funciona com -d)
|--name| 	Nomear o container
|-v| 	Mapeamento de volume
|-p| 	Mapeamento de porta
|-m| 	Limitar o uso de memória RAM
|-c| 	Balancear o uso de CPU
---
* Com o exec nós podemos executar qualquer comando nos nossos contêineres sem precisarmos estar na console deles:
    * #### `docker exec (id_container ou nome_container)`
 * Vejamos a baixo alguns dos parâmetros que podemos utilizar com ele:
    * -i permite interagir com o container
    * -t associa o seu terminal ao terminal do container
    * -it é apenas uma forma reduzida de escrever -i -t
    * --name algum-nome permite atribuir um nome ao container em execução
    * -p 8080:80 mapeia a porta 80 do container para a porta 8080 do host
    * -d executa o container em background
    * -v /pasta/host:/pasta/container cria um volume '/pasta/container' dentro do container com o conteúdo da pasta '/pasta/host' do host

---
* Para que possamos subir um contêiner vamos utilizar o comando start.
    * #### `docker start (id ou nome container)`


---
* Para que possamos parar um contêiner que esteja sendo executado, nós utilizamos o comando stop:
    * #### `docker stop (id ou nome container)`
---
