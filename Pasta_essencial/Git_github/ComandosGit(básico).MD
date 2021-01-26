# **:bulb:Dicas e comandos git básico.** 
---


## Ciclo de vida dos arquivos no git:
---


* Untracked
* Tracked
* Modified
* Staged
---
## Para ignorar arquivos ou diretórios, basta criar um arquivo:
**.gitignore**

Dentro do arquivo .gitignore basta incluir o nome exato do arquivo que será ignorado, desta forma: "arquivoignorado.extensão"
Exemplo: 

**arquivo02.c**

Exemplo para ignorar um diretório inteiro, dentro do arquivo .gitignore:

****pasta1**

Exemplo para ignorar todos arquivos em uma determinada extensão, dentro do arquivo .gitignore:

***.java**

---

# :bulb:Lista de comandos git para uso através do terminal:
---
## 1 - `git status`

O comando `git status` exibe as condições do diretório de trabalho e da área de staging(área temporária).

Documentação git sobre status: https://git-scm.com/docs/git-status/pt_BR

---

## 2 - `git init`
O comando `git init` funciona para criar um novo repositório.

O status passa então de "Untracked" para "Tracked".

---

## 3 - Comandos de identificação de usuário:
Após criar um repositório, criar de imediato a identificação de usuário com os comandos:   
`git config user.name "nomeDeUsuario"`

`git config user.email "meuEmail@email.com"`

Para incluir o usuário em modo global e não apenas no repositório em questão, basta incluir: 

`git config --global`

---
        
## 4 - Movendo arquivos no ciclo de vida para o status "Tracked":
`git add exemplo.java`

`git add .` (adiciona todos arquivos para o estado Tracked)

---

## 5 - Commits : O arquivo passa do estado "Tracked" para o estado "Modified":
`git commit -m "exemploTexto"`

Os commits são necessários após qualquer criação ou modificação de arquivos e códigos, cria um 
snapshoot do arquivo no estado atual.

---

## 6 - Buscar o histórico:

Comando para buscar commits: 

`git log`
```
Dentro do git log:
"/" Utilizada para buscar palavras chaves identificadas nos commmits.
"q" quit.
"b" próximo commit com a mesma palavra chave.
```

`git log --oneline` (comando reduzido para exibir commits)

`git log -- author="nomeDoUsuario"` (comando para buscar o commit de um determinado user)

---

## 7 - Comando para alterar o head/master para uma outra branch. Comando pode ser utilizado para movimentar-se entre outros commits, possibilitando ver como estava o código no passado.
`git checkout <7primeirosNumerosIDrash>`

Lembrando que podemos acessar o IDrash através do git log.

Exemplo: `git checkout 59271d9`

Comando para retornar para o master principal:

`git checkout master`

Comando para desfazer todas as alterações atuais do arquivo e voltar ao último ponto de partida.

`git checkout <nomeDoArquivo.extensão>`

---

## 8 - Renomear ou mover arquivo pelo terminal:
`git mv <origem> <destino>`

 ---

## 9 - Verificar a diferença nas alterações do arquivos, antes do commit:
`git diff --staged` 

Para comparar dois commits:

`git diff <hashID>..<hashID>`

Lembrando as "hashID" são os 7 primeiros dígitos do arquivo, que podem ser localizados através do comando 

`git --oneline`.

---

:point_right: [ComandosGit(intermediário)](https://github.com/Dev-HideyukiTakahashi/Git-Github/blob/main/ComandosGit(intermedi%C3%A1rio).MD) 


