# :floppy_disk: Trabalhando com arquivos em JAVA.
---
### Classes
* File - Representação abstrata de um arquivo e seu caminho
    * https://docs.oracle.com/javase/10/docs/api/java/io/File.html
* Scanner - Leitor de texto
    * https://docs.oracle.com/javase/10/docs/api/java/util/Scanner.html
* IOException (Exception)
    * https://docs.oracle.com/javase/10/docs/api/java/io/IOException.html

---
### Sintaxes
* Sintaxe da classe **File** para instanciar um novo arquivo:
```JAVA
File file = new File(<caminho do arquivo>);
```
* Sintaxe exemplo para ler um arquivo com **Scanner**:
```Java
Scanner input = null;
//Como a instância pode dar um erro, essa exception precisa ser tratada
try{
    input = new Scanner(file);
}catch(IOException e){
    System.out.println("Error: " + e.getMessage())
}finally {
        //Uma boa prática é fechar o arquivo no "finally"
        //independente da execução do arquivo ter sucesso ou não,
        //dessa forma o arquivo vai ser fechado com toda certeza.
        if (input != null) {
            input.close();
        }

```
---
### Classes
* FileReader (stream de leitura de caracteres a partir de arquivos)
    * stream(sequência de leitura)
    * https://docs.oracle.com/javase/10/docs/api/java/io/FileReader.html
* BufferedReader (mais rápido)
    * https://docs.oracle.com/javase/10/docs/api/java/io/BufferedReader.html
* Discussão sobre a diferença entre as duas classes:
    * https://stackoverflow.com/questions/9648811/specific-difference-between-
bufferedreader-and-filereader
* Bloco try-with-resources
    * É um bloco try que declara um ou mais recursos, e garante que esses
    recursos serão fechados ao final do bloco.

* Exemplo:
```Java
public static void main(String[] args) {

        String path = "/home/hideyuki-takahashi/file/in.txt";
        //Começa uma stream(sequência de leitura) a partir do caminho informado (path)
        try (BufferedReader br = new BufferedReader(new FileReader(path))) {
           
            //Cria-se uma String para ler a próxima linha do 'path'
            String line = br.readLine();

            while (line != null) {
                System.out.println(line);
                line = br.readLine();
            }
        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }

    }
```
---
### Classes
* FileWriter (stream de escrita de caracteres em de arquivos)
    * https://docs.oracle.com/javase/10/docs/api/java/io/FileWriter.html
        * Cria/recria o arquivo: new FileWriter(path)
        * Acrescenta ao arquivo existente: new FileWriter(path, true)
* BufferedWriter (mais rápido)
    * https://docs.oracle.com/javase/10/docs/api/java/io/BufferedWriter.html
* Exemplo:
```Java
 public static void main(String[] args) {
        String[] lines = new String[]{"Good morning", "Good afternoon", "Good night"};

        //Criando o arquivo de destino que não existe ainda
        String path = "/home/hideyuki-takahashi/file/out.txt";

        //Definindo o caminho para inserção das 'lines' no 'path'
        //OBS: no new FileWriter(path, true) . . .
        //Poderia ser incluído 'true' caso não queira recriar o arquivo e apenas acrescentar dados
        try (BufferedWriter bw = new BufferedWriter(new FileWriter(path))) {
            for (String line : lines) {
                //Comando para escrever uma linha da String 'lines'
                bw.write(line);
                //comando para pular uma linha \n
                bw.newLine();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
```

---

### Manipulando pastas com File

```Java
public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.println("Enter a folder path: ");
        //Resposta: /home/hideyuki-takahashi (OBS: utilizando linux)
        //A String vai salvar o caminho do diretório
        String strPath = input.nextLine();

        File path = new File(strPath);

        //Criando uma string de File para listar todos arquivos da pasta, com um lambda no argumento
        //Nesse caso, listar diretórios
        File[] folders = path.listFiles(File::isDirectory);
        System.out.println("FOLDERS: ");
        for (File folder : folders) {
            System.out.println(folder);
        }
        //A mesma situação acima, agora imprimindo os arquivos da pasta
        File[] files = path.listFiles(File::isFile);
        System.out.println("Files: ");
        for (File file : files) {
            System.out.println(file);
        }

        //criando uma subpasta no diretório

        //para indicar se deu certo ou não com 'boolean
        //esperado a criação de um diretório: /home/hideyuki-takahashi/newFolder
        boolean success = new File(strPath + "/newFolder").mkdir();
        System.out.println("Directory created?: " + success);

        input.close();

    }
```

---

### Informações do caminho do arquivo

```Java
public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.println("Enter a file path: ");
        String strPath = input.nextLine();
        File path = new File(strPath);

        //Para acessar o nome do arquivo, desprezando o caminho:
        System.out.println("getName: " + path.getName());

        //Para acessar só o caminho sem o nome do arquivo, desprezando o nome
        System.out.println("getParent: " + path.getParent());

        //Para acessar o caminho completo
        System.out.println("getPath: " + path.getPath());

        input.close();
    }
```

---
:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)