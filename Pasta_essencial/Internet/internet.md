# :computer:Como funciona a Internet

---


* Estrutura da Internet

A estrutura praticamente é sempre a mesma, nosso computador se
conecta a rede de um provedor de acesso, e a rede do provedor de acesso se
conecta a um dos backbones de cada país, que por sua vez, recebe o sinal
através de satélites ou cabos submarinos.

imagem1



A velocidade da Internet é muito maior nos provedores de acesso e
backbones do que no local onde está localizado o seu computador.
Então, para que os computadores possam se comunicar entre si, eles
precisam de uma linguagem comum, essa linguagem de comunicação é
formada por dois componentes:

imagem2



Cada computador recebe um número de identificação, chamado IP, que
é exclusivo, sendo que dois computadores não podem possuir o mesmo
número, ou seja, o mesmo IP.
O TCP cuida para que as informações pedidas por um computador a
outro computador, cheguem sem erros e com segurança, cito como exemplo:
seria como uma estrada que liga duas cidades, cada cidade seria um IP e a
estrada o protocolo TCP que faria a ligação entre as duas cidades, sem errar o
caminho.



* Conexão

A conexão dos computadores à internet é feita através dos Provedores
de Acesso (Empresa que tem instalada uma conexão de alta capacidade, com
uma grande rede de computadores, e que disponibiliza aos usuários o acesso
a essa rede, por meio de linhas telefônicas ou cabos, que cobram ou não pelo
serviço).

imagem 3



a) Conexão Discada: esta conexão é feita através de uma linha fixa de
telefone. Para isso, o computador precisa ter um modem instalado. E para
utilizar este serviço, o usuário deve contratar um provedor de acesso gratuito
ou pago, e deve pagar também os pulsos da ligação telefônica correspondente
ao tempo em que permanecer conectado à Internet.

b) Conexão a Rádio: esta conexão funciona através da repetição de
sinais feitas por antenas e recebida por outra antena instalada no local onde
fica o computador.

c) Conexão ADSL – esta conexão é feita através do compartilhamento
do cabo da linha do telefone fixo. Para utilizar este serviço, o usuário deve
contratar o acesso à Internet de um provedor e o serviço ADSL da operadora
local de telefonia fixa. Este tipo de serviço, também chamado de “banda larga”,
tem sido muito utilizado por usuários domésticos e também por empresas, por
permitir o compartilhamento com mais de um computador no mesmo local.

* HTML

Abreviação de Hypertext Markup Language, em português: Linguagem
de Marcação para Hipertexto é a linguagem padrão para escrever páginas
para serem visualizadas na Internet. 



# Como funciona Protocolo HTTP

HTTP: HyperText Transfer Protocol, que em português, quer dizer:
Protocolo de transferência de Hipertexto, é o conjunto de regras que permite
a transferência de informações na Internet.

* Características gerais

 Protocolo da camada de aplicação;

 Funciona baseado na troca de requisição resposta;

 Cabeçalho das mensagens é texto puro (não
binário);

 Não orientado a conexões;

 Não guarda estado entre conexões distintas, isto
é, cada conexão é nova para o servidor.

Exemplo (http://www.eu.com.br/index.html)

imagem7

* Requisição HTTP

 -Sintaxe geral de uma requisição HTTP (RFC822):
 -A primeira linha é chamada linha de comando
 -Podem haver vários cabeçalhos de requisição
 -Alguns comandos HTTP: GET, POST, HEAD,
PUT, DELETE, outros

 Comando GET
 Solicita ao servidor um recurso (página HTML, figura
GIF, documento do word, etc.)

 A URI do recurso pode conter dados separados por '?‘
 Exemplo: /index.html?dado1=valor1&dado2=valor2

 Comando POST 
 Usado para enviar dados para o servidor (p.e., upload
de arquivo, dados de formulário HTML)
 Ao contrário do GET, os dados seguem após a linha
em branco que separa cabeçalhos dos dados

URIs e URLs
 URI = URL + URN
 URI = Identificador Uniforme de Recursos
 URL = Localizador Uniforme de Recursos
 URN = Nome Uniforme de Recurso

 Sintaxe geral de uma URL:
<protocolo>://<servidor>:<porta>/<caminho>/<recurso>

 A porta é opcional para serviços em portas default
 Caminho e recurso podem ser omitidos (URLs
parciais)
 URLs podem conter dados depois do nome do recurso

* Resposta HTTP

 -Sintaxe geral de uma resposta HTTP (RFC-822):
 -A primeira linha é chamada linha de status
- Podem haver vários cabeçalhos de resposta
 -Os dados podem ser texto (página HTML) ou
binário (figura GIF)








# Como funcionam os Browsers

A funcionalidade principal do navegador
A funcionalidade principal de um navegador é apresentar o recurso da web escolhido por você por meio de uma 
solicitação ao servidor e exibição na janela do navegador. O recurso geralmente é um documento HTML, mas também 
pode ser um PDF, uma imagem ou outro tipo de arquivo. O local desses recursos é especificado pelo usuário
por meio de um URI (Identificador Uniforme de Recursos).

A forma como o navegador interpreta e exibe arquivos HTML é apresentadas nas especificações de HTML e CSS. 
Essas especificações são mantidas pelo W3C (Consórcio World Wide Web), a organização que controla os padrões 
para a web.
Por muitos anos, os navegadores mantiveram-se parcialmente de acordo com as especificações e desenvolveram 
as próprias extensões. Isso causou sérios problemas de compatibilidade para autores da web. Hoje a maioria 
dos navegadores está relativamente de acordo com as especificações.

As interfaces do usuário dos navegadores têm muito em comum. Entre os elementos comuns às interfaces 
do usuário estão:

 * Barra de endereço para inserção do URI
 * Botões voltar e avançar
 * Opções para adicionar favoritos
 * Botões atualizar e parar para atualizar e parar o carregamento dos documentos atuais
 * Botão Início que o leva à página inicial

O primeiro passo para navegar na web é ter uma conexão com a
Internet, através de um provedor de acesso. O provedor geralmente fornece as
instruções de configuração e criação da conexão no seu computador.
Após conectar-se à Internet como usuário, abrirá para você o Browser
(Navegador), que é o programa com o qual você visualiza as páginas na
Internet.

A estrutura de nível superior do navegador
Os principais componentes do navegador são :

1- A interface do usuário , que inclui a barra de endereço, o botão voltar/avançar, o menu de favoritos, etc. 
Todas as áreas do display do navegador, exceto a janela principal em que você visualiza a página solicitada.

2- O mecanismo de navegação , que faz a triagem das ações entre a interface do usuário e o mecanismo de 
renderização.

3- O mecanismo de renderização, responsável pela exibição do conteúdo solicitado. Por exemplo, se o conteúdo 
solicitado estiver em HTML, ele é responsável pela análise do HTML e do CSS e pela exibição do conteúdo analisado 
na tela.

4- Networking, utilizado para chamadas de rede, como solicitações HTTP. Possui interface independente de 
plataforma e sub-implementações para cada plataforma.

5- Back-end da interface do usuário, utilizada para desenhar widgets básicos como caixas de combinação e janelas. 
Exibe uma interface genérica que não é específica à plataforma. Sob a interface, utiliza os métodos da interface 
do usuário do sistema operacional.

6- Intérprete JavaScript Utilizado para analisar e executar o código JavaScript.

7- Armazenamento de dados. Esta é uma camada persistente. O navegador precisa salvar dados de diversos tipos no disco rígido, como cookies. A nova especificação HTML (HTML5) define "banco de dados da web", que é um banco de dados completo (embora leve) no navegador.

imagem8



* Transferência de dados

* Upload

imagem4

A transferência de dados foi outro grande benefício obtido com a
Internet. A melhor e mais fácil maneira de transmitir dados pela Internet é com
o protocolo FTP (Protocolo de transferência de Arquivos), que permite a
transferência de grande volume de dados em formato de arquivo de maneira
fácil e padronizada entre os computadores, sendo possível disponibilizarmos
arquivos para outros usuários copiarem ou para copiarmos arquivos de outros
usuários

* Download

Download é o ato de copiar os arquivos que outros usuários
disponibilizam na Internet para o seu computador.

imagem5

Tipos de programas disponíveis na Internet para download:

imagem6

Shareware – você pode copiar e testar no seu computador, mas deve pagar
um valor ao autor do programa para continuar utilizando.

Demo – são versões que contêm algumas funções demonstrativas do
programa completo.

Trial – são versões para teste que depois de um tempo deixam de funcionar,
sendo necessário adquirir o programa.

Freeware – são programas para serem copiados e utilizados livremente, por
serem gratuitos.

Adware – são programas gratuitos, porém cheios de propagandas e alguns
instalam vírus no seu computador. Cuidado!






# Como funciona  Nomes de Domínio (DNS)

- O DNS é um “sistema de nomes” cujo objetivo
primário é mapear, em escala global, nomes de
domínios de rede e nomes de máquinas em
endereços IP, processo conhecido por “resolução
de nomes”.

- O DNS possui também a funcionalidade reversa,
traduzindo endereços IP em nomes.

imagem9

O DNS é estruturado na forma de um banco de
dados hierárquico distribuído, onde cada servidor
é responsável por manter uma tabela com os
endereços IP e nomes dos hosts em seu sub
- domínio.


Após a identificação do domínio há a identificação do referido país,
como: .br (para o Brasil), .fr (para a França), .us (para os Estados
Unidos).

Ex: google.com.br

Abaixo segue a lista de alguns domínios:
com - Indica que o site é uma organização comercial;
gov - Indica que o site é uma organização governamental;
edu - Indica que o site é uma organização educacional.
org - Indica que o site é uma organização;
ind - Indica que o site é uma organização industrial
net - Indica que o site é uma organização de redes


Dentro do Editor de Zona DNS, é possível encontrar alguns registros de tipos de DNS que você pode editar, 
adicionar ou remover.

Os tipos de registros de DNS disponíveis são:

A (Host). É o registro básico de DNS onde você pode adicionar um novo Host, TTL (Time to Live) e Aponta Para.

CNAME (Alias). Registro que serve como um alias para outro domínio. Você pode adicionar um novo Host,
TTL (Time to Live) e Aponta Para.

MX (Mail Exchange). Registro para identificar o servidor que trabalha com o seu email. Você pode adicionar 
um novo Host, TTL (Time to Live) e Aponta Para.

TXT (Texto). Registro que permite que você tenha informações em texto. Você pode colocar um novo Host, 
TTL (Time to Live) e Aponta Para.

AAAA (Registro de Endereço IPV6). É o A Record (Registro A), só que para protocolos IPV6. Você pode colocar um 
novo Host, IPV6 e TTL (Time to Live).

NS (Nameserver). É o registro do servidor DNS. É possível adicionar um novo Host, Valor TXT e TTL (Time to Live).

SRV. É o registro para um tipo específico de dados em um DNS. É possível adicionar uma nova Prioridade, Nome, Peso,
Porta, Aponta Para e TTL (Time to Live).



# HOSTING

* O que é serviço de hosting?

Podemos dizer que o host é qualquer máquina ou computador que esteja conectado a uma rede e que apresente um 
endereço IP. Esse endereço é o número que reconhece o site no mundo virtual — e, para simplificar 
o acesso ao site, esse número é associado a um nome. Os hosts, então, são os equipamentos responsáveis 
por armazenar tudo que se encontra em um site.

Nesse sentido, um bom serviço de hosting precisa garantir que, caso haja algum problema em um dos servidores,
outro assumirá imediatamente o encargo.

* Como funciona esse serviço de hospedagem?

De fato, o acesso a um site exige alguns procedimentos específicos. Quando você digita um endereço em seu 
navegador, rapidamente se inicia uma conexão com o servidor em que ele está hospedado. 
Uma solicitação de busca das informações armazenadas é remetida ao servidor. Então, acontece uma conversão 
de “nome do site” para o endereço IP, e todo o seu conteúdo surge na tela.

Por trás de todas essas ações está o DNS, a sigla em inglês para Sistema de Nomes de Domínios. 
Ele é o responsável por promover toda a conversão do nome do site em um endereço IP. Vale dizer, 
portanto, que é fundamental que o seu domínio seja dirigido para o DNS da prestadora de hospedagem, 
de maneira que a conversão das informações aconteça de modo prático e correto.








*fonte https://blog.intnet.com.br/o-que-e-servico-de-hosting/
*fonte https://www.html5rocks.com/pt/tutorials/internals/howbrowserswork/#:~:text=A%20funcionalidade%20principal%20de%20um,ou%20outro%20tipo%20de%20arquivo.
*fonte https://cin.ufpe.br/~erp/DesenvWeb/aulas/http_servlet/http.pdf
*fonte http://www.crescabrasil.com.br/pessoas/347/material/Diagrama%C3%A7%C3%A3o%20Internet%20para%20Iniciante.pdf