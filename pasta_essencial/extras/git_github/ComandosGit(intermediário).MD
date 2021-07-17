# :bulb:Dicas e comandos git intermediário.

---

## 1 - Branch

* Comando para verificar os ramos(branch):

    `git branch`

* Criando uma nova branch:

    `git branch <nomeDaBranch>`
    
* Mudando para outra branch:

    `git checkout <nomeDaBranch>`
    
* Deletando uma branch:

    `git branch -D <nomeDaBranch>`

---

## 2 - Merge
    
* Comando para unificar a branch com a master. 

  * Obs: é necessário estar conectado a branch master.

    `git merge <nomeDaBranch>`

---

## 3 - Clone
        
* Repositório local:

     `git clone C:\Users\usuario\Desktop\exemplo_git\pastaRepositorio`

* Pode acrescentar um "." (ponto final), comando para clonar exatamente dentro da pasta que está localizado:

    `git clone C:\Users\usuario\Desktop\exemplo_git\pastaRepositorio .`

* Atenção, por boas práticas, nunca criar pastas e arquivos com "espaço" pois isso pode causar problemas na clonagem no terminal.
    
* Clone de um diretório do Github:

    `git clone https://github.com/exemplo`

---

## 4 - Push

* Comando utilizado para enviar arquivos a um repositório centralizador(bare), que pode ser local, ou remoto(github).

    `git push`

---
## 5 - Bare

* Comando para criar um repositório bare local(centralizador)

   `git init --bare`

---
## 6 - Fetch

* Comando utilizando para fazer o download dos arquivos, ainda sem fazer o merge:

    `git fetch`

* Seguido do comando para fazer o merge:

    `git rebase`

* Podemos também utilizar outro comando, para fazer o fetch + rebase ao mesmo tempo:

    `git pull`

---
## 7 - Tags

* Comando:

    `git tag <argumentos>`

* Similar aos branchs as tags podem ser utilizadas de diversas formas, para dividir setores, tarefas, versões...

* Exemplo para criar taguma tag de versão:

    `git tag v1.0`

* Comando para enviar essa informação para um centralizador(Bare):

    `git push origin v1.0`

* Exemplo para retornar a uma antiga versão com comando checkout:

    `git checkout v0.5`

* Para retornar a master:

    `git checkout master`

---

:point_right: [Comandos Git (básico)](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial/blob/master/pasta_essencial/git_github/ComandosGit(b%C3%A1sico).MD) 
:point_right: [Programador Essencial](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
