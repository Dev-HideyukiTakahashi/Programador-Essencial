# :gem: Data e hora

---

### O java.util.date

- Métodos úteis

| Método          | Retorno     | Descrição                                                  |
| --------------- | ----------- | ---------------------------------------------------------- |
| after(Date)     | boolean     | Checa se o obj Date de referência é posterior ao comparado |
| before(Date)    | boolean     | Checa se o obj Date de referência é anterior ao comparado  |
| compareTo(Date) | int         | Compara 2 obj Date                                         |
| equals(Date)    | boolean     | Checa se os objetos são iguais                             |
| getTime()       | long        | Retorna a data em milissegundos                            |
| setTime(long)   | void        | Define uma data com base em milissegundos                  |
| from(Instant)   | Static Date | Define uma data com base em um instant                     |
| toInstant()     | Instant     | Retorna um Instant com base em um Date                     |

- Date(long date)

  - Método utilizado para retornar a data no tipo long em milisegundos:
    - `long <obj> = System.currentTimeMillis();`
  - Criando um Date a partir do resultado obtido em milisegundos:
    - `Date <obj> = new Date(<objLong>);`

- A partir do Java 8 alguns exemplos:
  - LocalDate:
    - `LocalDate hoje = LocalDate.now();`
    - O LocalDate por padrão imprime dados em "yyyy-MM-dd"
    - Exemplo para ver um dia anterior:
      `LocalDate ontem = hoje.minusDays(1);`
  - LocalTime:
    - `LocalTime agora = LocalTime.now();`
      Retorna apenas a hora exata que foi chamado o método.
    - Exemplo para adicionar 1 hora:
      `LocalTime maisUmaHora = agora.plusHours(1);`
  - LocalDateTime:
    - `LocalDateTime agora = LocalDateTime.now();`
      Um método completo para impressão de data e hora.

---

- Função útil para retornar a diferença de dias:

```Java
public long diferencaDeDias(){

	//A função getTime() retorna o valor em milisegundos no tipo Long.
	//Nesse caso é subtraido o valor de milisegundos da data 2 pela data 1
	long dif = <data2>.getTime() - <data1>.getTime();
	//Depois basta converter esse valor em dias, também podendo ser mês ou ano.
	return TimeUnit.DAYS.convert(dif, TimeUnit.MILLISECONDS);

}

```

- Função útil para retornar a diferença entre horas:

```JAVA

public void returnTime(CarRental carRental) {
	//Armazenando o tempo em millisegundos
	long t1 = <data1>.getTime();
	long t2 = <data2>.getTime();
/*Tirando a diferença em milisegundos (t2 - t1)
- Divide por 1000, transforma de milisegundos para segundos
- Divide por 60, transforma segundos para minuto
- Divide por 60, transforma minutos para hora
*/
	double hours = (t2 - t1) / 1000 / 60 / 60;
	//Armazena o valor em horas

	TimeUnit.HOURS.convert(t2-t1,TimeUnit.MILLISECONDS );
}
```

---

- **Padrão ISO 8601**

  - Formato:
    - `yyyy-MM-ddTHH:mm:ssZ`
  - Exemplo:
    - `2021-02-09T23:13:02Z`

- Utilizando "Instant".
  - Sintaxe para instanciar:
    - `Date date = Date.from(Instant.parse("yyyy-MM-ddTHH:mm:ssZ"))`
  - Sintaxe em um obj Date já criado:
    `Instant <obj> = <objDate>.toInstant();`
    - Estrutura:

```Java
package curso_java;

import java.time.Instant;
import java.util.Date;

public class Datas {

	public static void main(String[] args) {

		Date date;

		date = Date.from(Instant.parse("2021-02-09T23:13:02Z"));
		System.out.println(date);

	}
}
```

- OUTPUT:
  Tue Feb 09 20:13:02 BRT 2021

---

- **SimpleDateFormat**

  - Para converter uma String de data recebida para a classe Date, precisamos definir o formato esperado utilizando a classe SimpleDateFormat.
  - Sintaxe exemplos:
    `SimpleDateFormat <nomeObj> = new SimpleDateFormat("dd/MM/yyyy");`
    `SimpleDateFormat <nomeObj> = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");`

- Para converter de String para Date, utilizaremos o método parse() do objeto formato:
  - `Date dataFormatada = formato.parse(dataRecebida);`
    - "formato.parse()" seria o nome do obj que foi instanciado a partir da classe SimpleDateFormat.
- Para que seja impresso o objeto data no formato que foi definido no `SimpleDateFormat` usaremos o método format() do objeto `SimpleDateFormat`
- Para criar um objeto com a data atual do sistema, sintaxe:
  - `Date <nomeObj> = new Date();`

---

- Exemplos manipulando data/hora:

```Java
package curso_java;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.time.Instant;
import java.util.Date;
import java.util.TimeZone;

public class Datas {

	public static void main(String[] args) throws ParseException {


		//Criando o objeto a partir do formato de data/hora
		SimpleDateFormat sdf1 = new SimpleDateFormat("dd/MM/yyyy");
		SimpleDateFormat sdf2 = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

		//Criando o objeto passando os argumentos com "parse"
		Date dia1 = sdf1.parse("10/02/2021");
		Date dia2 = sdf2.parse("10/02/2021 20:30:02");


		System.out.println("Objeto dia 1: "+dia1);
		System.out.println("Objeto dia 2: "+dia2);

		//Saída de Dados:
		//Objeto dia 1: Wed Feb 10 00:00:00 BRT 2021
		//Objeto dia 2: Wed Feb 10 20:30:02 BRT 2021

		System.out.println("Objeto dia 1: "+sdf1.format(dia1));
		System.out.println("Objeto dia 2: "+sdf2.format(dia2));

		//Saída de Dados:
		//Objeto dia 1: 10/02/2021
		//Objeto dia 2: 10/02/2021 20:30:02

		//Criando um objeto com a data atual no sitema
		Date dataAtual = new Date();

		System.out.println("Data atual: "+ dataAtual);

		//Saída de Dados:
		//Data atual: Wed Feb 10 20:50:54 BRT 2021

		System.out.println("Data atual com SimpleDateFormat: "+sdf2.format(dataAtual));

		//Saída de Dados:
		//Data atual com SimpleDateFormat: 10/02/2021 20:52:50

		//Criando uma data no formato UTC padrão
		Date dateUTC = Date.from(Instant.parse("2021-02-09T23:13:02Z"));
		System.out.println("Data UTC: "+dateUTC);
		//Saída de Dados:
		//Data UTC: Tue Feb 09 20:13:02 BRT 2021


		//Criando um objeto para convertar a hora para o horário UTC - no exemplo convertido do horário GMT para UTC:
		SimpleDateFormat sdf3 = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
		sdf3.setTimeZone(TimeZone.getTimeZone("GMT"));
		System.out.println("Data UTC: "+sdf3.format(dateUTC));

		//Saída de Dados:
		//Data UTC: 09/02/2021 23:13:02

	}
}
```

- Classe Calendar:

  - Essa classe pode produzir os valores de todos os campos de calendário necessários para implementar a formatação de data e hora.
  - Com a classe Calendar também se consegue manipular a data e hora com os métodos que são fornecidos.
  - Exemplos mostrando na tela data/hora:
    - Instanciando um obj a partir da classe Calendar.
      `Calendar c = Calendar.getInstance();`

```Java
System.out.println("Data/Hora atual: "+c.getTime());
System.out.println("Ano: "+c.get(Calendar.YEAR));
System.out.println("Mês: "+c.get(Calendar.MONTH));
System.out.println("Dia do Mês: "+c.get(Calendar.DAY_OF_MONTH));
```

- Exemplos alterando data/hora:

```Java
Calendar c = Calendar.getInstance();
c.set(Calendar.YEAR, 1995);
c.set(Calendar.MONTH, Calendar.MARCH);
c.set(Calendar.DAY_OF_MONTH, 20);
```

- Exemplos interagindo com usuário:

```Java

import java.util.Calendar;

public class Msg_Boas_Vindas_Calendar{

	public static void main(String[] args) {
		Calendar c1 = Calendar.getInstance();
		int hora = c1.get(Calendar.HOUR_OF_DAY);

if(hora > 6 && hora < 12){
			System.out.println("Bom Dia");
		}else if(hora > 12 && hora < 18){
			System.out.println("Boa Tarde");
		}else{
			System.out.println("Boa Noite");
		}
	}
}
```

- Exemplo:

```JAVA
package curso_java;

import java.text.SimpleDateFormat;
import java.time.Instant;
import java.util.Calendar;
import java.util.Date;

public class Main {

	public static void main(String[] args) {

		System.out.println("Modificando uma unidade de tempo ");


		SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
		Date dia = Date.from(Instant.parse("2021-02-10T21:59:07Z"));

		System.out.println(sdf.format(dia));
		//Saída de Dados:
		//10/02/2021 18:59:07

		//Criando um objeto da classe Calendar
		Calendar cal = Calendar.getInstance();
		//Configurando o dia do cal para o dia instanciado no objeto dia da clase Date
		cal.setTime(dia);

		//Adicionando 4 horas do dia ao objeto cal
		cal.add(Calendar.HOUR_OF_DAY, 4);
		//Atualizando o objeto dia da classe Date, utilizando o objeto cal
		dia = cal.getTime();

		System.out.println(sdf.format(dia));
		//Saída de Dados:
		//10/02/2021 22:59:07
		System.out.println();


		System.out.println("Obtendo uma unidade de tempo ");



		SimpleDateFormat sdf2 = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
		Date dia2 = Date.from(Instant.parse("2021-02-10T22:08:07Z"));

		System.out.println(sdf2.format(dia2));

		Calendar cal2 = Calendar.getInstance();
		cal2.setTime(dia2);
		int minutes = cal2.get(Calendar.MINUTE);
		//O Calendar começa como mês 0, sendo necessário acrescentar 1
		int month = 1 + cal2.get(Calendar.MONTH);
		int hour = cal2.get(Calendar.HOUR_OF_DAY);

		System.out.println("Minutos: "+minutes);
		System.out.println("Mês: "+month);
		System.out.println("Hora: "+hour);
		//Saída de Dados:
		//Minutos: 8
		//Mês: 2
		//Hora: 19

	}

}
```

---

### JAVA 8 ++

---

- Método para gerar a data exato do computador local

```java
LocalDate date1 = LocalDate.now();
System.out.println("Date1: " + date1);
// OUT : 2022-08-04
```

- Método para gerar o horário/data exato do computador local no formato ISO

```java
LocalDateTime date2 = LocalDateTime.now();
System.out.println("Date2: " + date2);
// OUT : 2022-08-04T17:37:05.631094300
```

- Método para gerar o horário/data GMT no formato ISO

```java
Instant date3 = Instant.now();
System.out.println("Date3: " + date3);
// OUT: 2022-08-04T20:38:32.723257900Z
```

- Gerando data com argumentos

```java
LocalDateTime newDate = LocalDateTime.of(2022, 07, 20, 1, 30);
System.out.println("NewDate: " + newDate);
// OUT: 2022-07-20T01:30
```

- Recebendo datas com parse

```java
LocalDate date4 = LocalDate.parse("2022-07-20");
System.out.println("Date4: " + date4);
// OUT: 2022-07-20
```

```java
LocalDateTime date5 = LocalDateTime.parse("2022-07-20T01:30:26");
System.out.println("Date5: " + date5);
// OUT : 2022-07-20T01:30:26
```

- Data adicionando Z para indicar o padrão UTC

```java
Instant date6 = Instant.parse("2022-07-20T01:30:26Z");
System.out.println("Date6: " + date6);
// OUT : 2022-07-20T01:30:26Z
```

- Informando horário de São Paulo (UTC-3:00), o output é o horário UTC somado ao argumento

```java
Instant date7 = Instant.parse("2022-07-20T01:30:26-03:00");
System.out.println("Date7: " + date7);
// OUT: 2022-07-20T04:30:26Z
```

- Formatando datas
  - https://docs.oracle.com/javase/8/docs/api/java/time/format/DateTimeFormatter.html

```java
DateTimeFormatter dateFormat1 = DateTimeFormatter.ofPattern("dd/MM/yyyy");
DateTimeFormatter dateFormat2 = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");

// Basta informar o segundo parâmetro com o objeto formatador
LocalDate date8 = LocalDate.parse("20/07/2022", dateFormat1);
System.out.println("Date8: " + date8);
// OUT : 2022-07-20
```

```java
LocalDate formatoDireto = LocalDate.parse("27/07/2022", DateTimeFormatter.ofPattern("dd/MM/yyyy"));
System.out.println("FormatoDireto: " + formatoDireto);
// OUT : 2022-07-27
```

```java
LocalDateTime date9 = LocalDateTime.parse("20/07/2022 01:30:00", dateFormat2);
System.out.println("Date9: " + date9);
// OUT: 2022-07-20T01:30
```

- Reaproveitando data 4,5,6 para customizar a formatação

```java
System.out.println("Date4 formatado = " + dateFormat1.format(date4));
//System.out.println("Date4 formatado = " + date4.format(DateTimeFormatter.ofPattern("dd/MM/yyyy")));
// OUT : 20/07/2022
```

```java
System.out.println("Date5 formatado = " + dateFormat2.format(date5));
// OUT: 20/07/2022 01:30:26
```

- Formatando padrão ISO já no padrão UTC - 3:00

```java
DateTimeFormatter dateFormat3 = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss").withZone(ZoneId.systemDefault());
System.out.println("Date6 formatado = " + dateFormat3.format(date6));
// OUT: 19/07/2022 22:30:26
```

- Converter data data-hora global para local
- Brasil = UTC - 3:00 (São Paulo)
  - Exemplo usado = Date6: 2022-07-20T01:30:26Z

```java
// ZoneId.systemDefault considera o timezone do computador local
LocalDate r1 = LocalDate.ofInstant(date6, ZoneId.systemDefault());
System.out.println("Date6 convertida " + r1);
// OUT : Date6 convertida 2022-07-19
```

```java
LocalDateTime r2 = LocalDateTime.ofInstant(date6, ZoneId.of("America/Sao_Paulo")); // Brazil/East
System.out.println("Date6 convertida " + r2);
// OUT: Date6 convertida 2022-07-19T22:30:26
```

- Obtendo elementos

```java
System.out.println("Dia " + date5.getDayOfMonth());
System.out.println("Mês " + date5.getMonthValue());
System.out.println("Hora " + date5.getHour());
System.out.println("Minutos " + date5.getMinute());

// OUT: Dia 20
// Mês 7
// Hora 1
// Minutos 30
```

- Calculos com data
  - Exemplo data 5 : 20/07/2022 01:30:26

```java
LocalDateTime semanaPassada = date5.minusDays(7);
System.out.println("Semana Passada: " + semanaPassada);
// OUT: Semana Passada: 2022-07-13T01:30:26
System.out.println(dateFormat2.format(semanaPassada));
// OUT: 13/07/2022 01:30:26
```

```java
LocalDateTime proximaSemana = date5.plusDays(7);
System.out.println("Próxima semana: " + proximaSemana);
// OUT : Próxima semana: 2022-07-27T01:30:26

LocalDateTime proximoAno = date5.plusYears(1);
System.out.println("Próximo ano: " + proximoAno);
// OUT : Próximo ano: 2023-07-20T01:30:26
```

```java

LocalDateTime maisDuasHoras = date5.plusHours(2);
System.out.println("MaisDuasHoras: " + maisDuasHoras);
// OUT: MaisDuasHoras: 2022-07-20T03:30:26
```

- Instant basta passar o argumento e ChronoUnit

```java
Instant pastWeek = date6.minus(7, ChronoUnit.DAYS);
System.out.println("Instant semana passada : " + pastWeek);
// OUT: Instant semana passada : 2022-07-13T01:30:26Z
```

- Calculando diferença

```java
Duration duration1 = Duration.between(semanaPassada, date5);
System.out.println("Diferença entre dias: " + duration1.toDays());
System.out.println("Diferença entre horas: " + duration1.toHours());
// OUT: Diferença entre dias: 7
// OUT: Diferença entre horas: 168
```

---

:coffee:[Voltar Java](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)
