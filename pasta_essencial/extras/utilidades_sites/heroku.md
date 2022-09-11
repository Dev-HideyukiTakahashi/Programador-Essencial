# :hammer_and_wrench:Heroku

---

## :hammer: Configuração para deploy

- No pom xml:

```java
<build>
    ...
    <plugins>
        ...
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-dependency-plugin</artifactId>
            <executions>
                <execution>
                    <phase>package</phase>
                    <goals><goal>copy</goal></goals>
                    <configuration>
                        <artifactItems>
                            <artifactItem>
                                <groupId>com.heroku</groupId>
                                <artifactId>webapp-runner</artifactId>
                                <version>9.0.52.1</version>
                                <destFileName>webapp-runner.jar</destFileName>
                            </artifactItem>
                        </artifactItems>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

- Na pasta raíz onde o projeto está localizado no computador, abrir o terminal:

  - `mvn clean package`

- Na pasta raíz do projeto na IDE, criar um novo file com nome de `Procfile`, com seguinte conteúdo:

  - `web: java $JAVA_OPTS -jar target/dependency/webapp-runner.jar --port $PORT target/\*.war`

- 1º passo:
- Criando a aplicação no heroku

  - `heroku create nome_do_app`

- 2º passo:
- Criando a o banco de dados na aplicação no heroku

  - `heroku addons:create heroku-postgresql:hobby-dev --app nome_do_database`

- 3º passo:
- Recupera as credenciais para acessar o banco de dados

  - `heroku config --app nome_do_database`

  - Exemplo de resposta: `postgres://iu5edwe9okjppi:1c953ffrl9cf1kdu84cf226be32e9a7f358a4e11c7be21b0e619duy1078f8281@ec2-35-168-122-84.compute-1.amazonaws.com:5432/dcg6uji1u4056a`
  - Quebrando o resultado -> após ' // ' -> após ' : ' -> após ' @ '
    - `iu5edwe9okjppi` -> user
    - `1c953ffrl9cf1kdu84cf226be32e9a7f358a4e11c7be21b0e619duy1078f8281` -> senha
    - `ec2-33-162-122-84.compute-1.amazonaws.com:5432/crg6uji1u4056a` -> host:porta / nome do banco de dados

- 4º passo:
- Após adicionar as credenciais na configuração do sistema back-end, iniciar o git e fazer o commit(caso não tenha) e adicionar o remotamente o heroku
  - `git init`
  - `git add .`
  - `git commit -m "Ready to deploy"`
  - `heroku git:remote -a nome_do_database` // configurando o caminho da aplicação no heroku remota, no projeto local
  - `git push heroku master` // enviando o projeto local para aplicação no heroku

---

https://devcenter.heroku.com/articles/java-webapp-runner
