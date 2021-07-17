# :floppy_disk: Interfaces
---
* Interface é um tipo que define um conjunto de operações que uma classe deve implementar.
* A interface estabelece um contrato
que a classe deve cumprir.
* Sintaxe:
```JAVA
interface Shape {
double area();
double perimeter();
}
```
* Pra quê interfaces?
    * Para criar sistemas com baixo acoplamento e flexíveis.

* Diferença fundamental entre herança e interface:
    * Herança => reuso
    * Interface => contrato a ser cumprido

---

#### Inversão de controle
* Inversão de controle
    * Padrão de desenvolvimento que consiste em
responsabilidade de instanciar suas dependências.
retirar
da classe a
* Injeção de dependência
    * É uma forma de realizar a inversão de controle: um componente externo
instancia a dependência, que é então injetada no objeto "pai". Pode ser
implementada de várias formas:
        * Construtor
        * Classe de instanciação (builder / factory)
        * Container / framework
---

:coffee:[Voltar](https://github.com/Dev-HideyukiTakahashi/Programador-Essencial)

