# :bulb:Essencial para começar no github

---
---
##  Configurando a identificação:

`git config --global user.name "Seu nome"`

`git config --global user.email "Seu email de cadastro no github"`

`git config --list` (exibe as configurações)

---
##  Configurando a chave SSH:

* Comando em console:
`ssh-keygen -t ed25519 -C "your_email@example.com"`
```
Observação: Se você estiver usando um sistema legado que não é compatível com o algoritmo Ed25519, use:

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

```
---
##  Salvando primeira versão de um projeto no github:

* Em uma pasta local, no terminal:
  * `git init`
  * `git add .`
  * `git commit -m "Mensagem explicativa"`
  * `git branch -M main`
  * `git remote add origin git@github.com:seuusuario/seurepositorio.git`
    * esses dados acima podem ser coletados direto do site github, no repositório a qual será associado.
* `git push -u origin main`

---

##  Verificar o histórico de versões:

`git log`

`git log --oneline`

---

##  Verificar a diferença entre arquivos modificados:

`git diff exemplo.html`

---

##  Modificar temporariamente os arquivos ao estado de um commit ou branch:

* Código do commit, HEAD
  * Cada commit possui um código, que pode ser utilizado para referenciar o commit.
  * O último commit do histórico do branch pode ser referenciado pela palavra HEAD.
  * É possível referenciar um commit **N** versões antes de HEAD usando **~N**, por exemplo
    * HEAD~1(penúltimo commit)
    * HEAD~1(antepenúltimo commit)
  * `git checkout main`
    * Voltar ao estado original.

* IMPORTANTE: Se acidentalmente mudou alguma coisa, desfazer modificações:
  * Remover arquivos da área de Staged(add .)
    * `git reset`
  * `git clean -df`  
  * `git checkout -- .`  

---

## Desfazer o último commit sem deletar as modificações:

`git reset --soft HEAD~1`

---

## Desfazer o último commit e também deletar as modificações:

Voltar o projeto ao estado de um dado commit(deletar commits e alterações posteriores a esse commit)
`git reset --hard <código do commit>`

Voltar o projeto ao estado do penúltimo commit:
`git reset --hard HEAD~1>`

---

## Resolver push rejeitado por históricos diferentes:

* Não é permitido enviar um push se o repositório local está atrasado em relação ao histórico do repositório remoto.

  * `git pull <nome do remote> <nome do branch>`
* Caso o VIM executar:
  * tecla "i" para habilitar a edição.
  * Sair, salvando as alterações: "esc" > ":wq" > "enter"
  * Sair, descartando as alterações: "esc" > ":q!" > "enter"

---

## Resolver pull com conflito:

* `git pull <nome do remote> <nome do branch>`

* Caso um arquivo tenha sido modificado tanto no local como no remoto, é necessário resolver esse conflito editando um último commit com um merge.
  * `git status` (para confirmar o status, precisa estar em "both modified")
  * No visual studeo podemos verificar as diferenças entre os arquivos e escolher a melhor opção.
  * Depois é só realizar um novo commit.
---

* Para fazer um hiperlink, basta adicionar <[nome do link](exemplo de site)> :

 



---
:point_right: [Github](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial/blob/master/pasta_essencial/extras/git_github/Github.MD)

:point_right: [Programador Essencial](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)



