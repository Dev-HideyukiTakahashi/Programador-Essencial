# :gem: Interface Comparable
---
https://docs.oracle.com/javase/10/docs/api/java/lang/Comparable.html

---

* Sintaxe:
```JAVA
public interface Comparable<T> {
    int compareTo (T o);
}
```

* Method compareTo:
    * Parameters: **o** - the object to be compared.
    * Returns: a negative integer, zero, or a positive integer as this object is less than, equal to, or greater than the specified object.

---
* Exemplo:
```Java
package entities;

public class Employee implements Comparable<Employee> {
    private String name;
    private Double salary;

    public Employee(String name, Double salary) {
        this.name = name;
        this.salary = salary;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Double getSalary() {
        return salary;
    }

    public void setSalary(Double salary) {
        this.salary = salary;
    }

    //Método para comparar 2 classes.
    //retorna negativo para menor
    //retorna 0 para igual
    //retorna positivo para maior
    @Override
    public int compareTo(Employee other) {
        return name.compareTo(other.getName());
    }
}
```


* Input possível
System.out.println("maria".compareTo("alex"));
System.out.println("alex".compareTo("maria"));
System.out.println("maria".compareTo("maria"));
* Outuput possível:
12 //Maria é maior que Alex (Ordem alfabética)
-12 //Alex é menor que Maria (Ordem alfabética)
0  //Maria é igual Maria (Ordem alfabética)
---


:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)