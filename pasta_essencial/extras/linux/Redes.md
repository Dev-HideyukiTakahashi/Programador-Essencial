# :bulb: Básico sobre redes e usuários 
---
### 1. Internet

* `ifconfig`
    * **ifconfig**, um acrônimo em inglês de "configuração de interface" (interface configuration) é um comando de UNIX e de sistemas operacionais tipo UNIX para configurar, controlar e visualizar informações sobre parâmetros TCP/IP de uma interface de rede.
* `hostname`
    * Este comando mostra ou muda o nome do computador na rede.
        * `hostname -I` = Retorna o endereço de IP na rede
        * `hostname -i` = Retorna o ip de loopback
* `who`
    * Em sistemas operacionais do tipo Unix, o comando who exibe usuários conectados ao sistema .
`dig`
    * Retorna todas as informações em DNS.
        * Exemplo : `dig www.google.com`
`whois`
    * Retorna um maior número de informações detalhadas sobre o domínio da internet.
        * Exemplos : `whois www.google.com`
---

### 2. Grupo de usuários, grupos e permissões

* `sudo adduser <nomeUsuario>` = Adiciona um novo usuário.
* `su <nomeUsuario>` = Permite mudar o proprietário de uma sessão para qualquer usuário.
* `passwd <nomeUsuario>` = Altera a senha do usuário
* `last` = Comando **last** e **lastb** do Linux. Em sistemas operacionais do tipo Unix, o último comando exibe uma lista dos usuários conectados mais recentemente. Nos sistemas operacionais Linux , o comando lastb suplementar exibe uma lista de logons incorretos (com falha).
* `userdel -r <nomeUsuario>`= Remove um usuário
* `groups`   = Exibe todos os grupos que o usuário pertence no sistema.
    * `addgroup <nomeGrupo>` = Adiciona um grupo.
    * `adduser <nomeUsuario> <grupo>` = Adiciona um usuário a um grupo.
    * `groupdel <nomeGrupo>` = Remove um grupo.
* Permissões:
    * r - read (leitura)
    * w - write (escrita)
    * x - execution (execução)
    * `ls -lh` = lista os diretórios e arquivos e suas permissões.
    * `chmod` = Muda a permissão de um diretório ou arquivo.
---
:point_right: [Programador Essencial](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
    





