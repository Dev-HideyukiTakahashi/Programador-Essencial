# :bulb:Dicas e comandos para github no terminal:

---


## 1 - Repositório Remoto

* Comando para verificar qual repositório remoto:

    `git remote -v`

 * Comando para adicionar um repositório remoto no Github:
    `git remote add origin https://github.com/exemplo/exemplo`

---

## 2 - Push Remoto

`git push -u origin <branch>`

* Exemplo:

`git push -u origin master`

---

## 3 - Pull remoto

`git pull origin <branch>`

* Exemplo:

`git pull origin master`

---

## 4 - Comando para salvar usuário e senha no terminal:

`git config credential.helper store`

---

## 5 - Adicionando colaboradores no projeto:

Dentro do projeto clicar em: `Settings > Manage Access > Invite a collaborator`

---

## 6 - Comando para retornar ao último estado do código antes das modificações (desfazer checkout):

* Para todos arquivos:
    `git checkout -- .`

* Para um arquivo específico:
    `git checkout -- <nomeArquivo>`

---

## 7 - Comando para reverter o último commit, voltando ao estado anterior daquele ponto e inclusive criando um novo commit para log.

`git revert <commit id>`

---

## 8 - Comando para resetar o último commit, desfazendo o commit e retornando o arquivo para o status "modificado".

`git reset HEAD~1`  
 /*após o "~" podemos definir qual número  de commits resetar */

---

## 9 - Comando para armazenar usuário e senha:

`git config credential.helper store`

* Removendo usuário e senha:

`git config --unset credential.helper`

---

## 10 - Issues (Problemas)

* Comando para fechar a issue, é incluso no final da mensagem(-m) do commit:

Closes #<númeroDaIssue>

---
---

:point_right: [ComandosGit(básico)](https://github.com/Dev-HideyukiTakahashi/Git-Github/blob/main/ComandosGit(b%C3%A1sico).MD)

:point_right: [ComandosGit(intermediário)](https://github.com/Dev-HideyukiTakahashi/Git-Github/blob/main/ComandosGit(intermedi%C3%A1rio).MD) 







