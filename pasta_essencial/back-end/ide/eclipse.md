# :gem:IDE Eclipse

---

### Configurar o GIT no Eclipse:

* No Eclipse clique com o botão direito no projeto, menu Team, Share Project.
* Clique em Create e selecione a pasta para gravação do seu GIT local. Recomendo criar a pasta com o mesmo nome do repositório remoto.
* Clique em Finish e Finish para confirmar a criação do repositório local.

### Configurar o repositório git remote no Eclipse

* Na guia Git repositories expanda as configurações do repositório e clique com o botão direito em Remotes, Create Remotes

* Informe o “alias” do repositório remoto. Exemplo: origin e clique em OK

* Clique em Change e informe a URL do repositório remoto

* Informe seu User e <s>Password</s> de acesso ao repositório remoto 
* **Atenção** : O sistema de autenticação no github mudou, a partir de agora podemos gerar um "token" de autenticação:
  * github > settings > <>Developer settings > Personal access tokens
  * O token gerado será utilizado no campo de password

* Clique em Finish e Save in Push
