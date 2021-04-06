# :bulb:Terminal, Shell
---

* É uma linha de comando onde podemos executar programas específicos do Linux.
* A maioria dos comandos são iguais em diversas distribuições.
* Uso para automação de processos através dos comandos, facilita o trabalho no Sistema para profissionais na área.
---

### :penguin:Comandos mais utilizados:
* Comandos básicos:

    * `--help` = Exibe o arquivo de ajuda de um comando específico.
        Exemplo: `ls --help`
    * `pwd` = O pwd (print working directory) é um comando que imprime o nome do diretório local em uma interface de linha de comando. 
    * `ls` = Este comando lista o conteúdo de um diretório em que está no momento.
        * `ls - l` = Utilizado para listar o conteúdo com detalhes.
    * `cd` = O comando “cd” serve para acessar e mudar de diretório corrente. Ele é utilizado para a navegação entre as pastas do computador. 
        * `cd ..` = Retorna para um diretório anterior.
        * `cd /` = Retorna ao diretório root(raíz).
        * `cd ~` = Retorna ao diretório pessoal(home).
    * `mkdir <nomeDaPasta>` = O comando 'mkdir' é usado para criar diretórios.
        * Exemplo: `mkdir pastaNova`
    * `history` = Retorna o histórico de comandos utilizados no terminal.
    * `exit` = Fecha o terminal.
    * `mv <nomeAntigo> <nomeNovo>` = Renomeia um diretório ou um arquivo.
        * Exemplo: `mv pastaNova pastaNovoNome`
    * `rmdir <nomeDaPasta>` = Remove um diretório.
    * `find` = Comando para buscar arquivos.
        * Exemplo: `find ~ -name pastaNova`
            * Busca todas as pastas em 'home' para comparar se encontra alguma com nome 'pastaNova'.
    * `arch` = Mostra a arquitetura do sistema (32 ou 64 bits)
    * `reboot` = Reinicia a máquina
        * `last reboot` = Retorna um histórico de todas as vezes que foi reiniciado.
    *
    
---   
* Manipulando arquivos:
    * `touch <nomeDoArquivo.extensão>` = Cria um arquivo vazio.
        * Exemplo: `touch texto.txt`
    * `rm <nomeDoArquivo>` = Remove um arquivo.
    * Editor de texto, comando `nano`.
        * Exemplo: `nano texto.txt`
        * O símbolo '^' é o mesmo que 'Ctrl', por exemplo Ctrl+X, para sair do editor.
        * A letra 'M' é o mesmo que 'Alt', por exemplo Alt+U para "desfazer".

    * `cat <nomeDoArquivo>` = Este comando envia o conteúdo de um ou mais arquivos para a saída padrão ou para um outro arquivo. Portanto, cat conCATena (junta) arquivos.
        * `cat <nomeDoArquivoFornecedor.extensão> >> <nomeDoArquivoReceptor.extensão>` = Concatena 2 arquivos.
            * Exemplo: `cat texto1.txt >> texto2.txt`
    * `head <nomeDoArquivo>` = Mostra as 10 primeiras linhas do arquivo.
    * `tail <nomeDoArquivo>` = Mostra as últimas 10 linhas do arquivo
    * `grep <palavra>` = Busca palavras em arquivos de texto.
---
* Operadores lógicos dentro do terminal:
    * "|" = Envia a saída de um comando para a entrada de outro comando, permitindo a execução de dois comandos
    * ">" = Redireciona a saída de um comando para outro comando ou arquivo.
    * ">>" = Redireciona a saída e adiciona a mesma para um comando ou arquivo.
    * "&" = Este operador permite usar dois comandos e separar suas saídas no teterminal.
    * "&&" = Usado para que dois comandos sejam executados, se o primeiro for executado com sucesso.
---
* Gerenciamento de pacotes:
    * `sudo apt upgrade <pacote>` 
        * Comando para atualizar um pacote.
    * `sudo apt remove <pacote>`
        * Remove um pacote.
    * `sudo apt update && upgrade `
        * Atualiza todos pacotes do sistema.
        * Pode ser necessário `sudo su`
    * `sudo dpkg -i <pacote>` 
        * Instala um programa com extensão **.deb**
        * Exemplo : `dpkg -i instalador.deb`
    * `sudo dpkg -r <pacote>`
        * Remove um pacote.
        * Pode ser necessário `sudo dpkg -I` para localizar o nome do pacote.
    















---

:penguin:[Guia Linux](https://guialinux.uniriotec.br/)