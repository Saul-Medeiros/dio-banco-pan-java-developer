# Dominando IDE's Java

## História do Java

* Java é uma linguagem de programação orientada a objetos desenvolvida na década de 90, na empresa Sun Microsystems e posteriormente adquirida pela Oracle em 2008.

* Desde seu lançamento, em maio de 1995, a plataforma Java foi adotada mais rapidamente do que qualquer outra linguagem de programação na história da computação.

* Tornou-se popula pelo seu uso na internet e está presente em navegadores, programas e jogos de computador, celular, calculadoras, e etc...

---

## Características do Java

Programa.java → Compilador → Programa.class (bytecode) → JVM (Java Virtual Machine) → `1000001001010101100101` (linguagem de máquina)
Diferente das linguagens de programação compiladas, (a compilação de código se dá ainda em tempo de desenvolvimento) a linguagem Java é compilada para um bytecode que é interpretado por uma máquina virtual (JVM).

---

## Plataforma x Linguagem

* A linguagem de programação Java é a linguagem convencional da plataforma Java, mas não é sua única linguagem.

* Uma grande vantagem da plataforma é a de não estar presa a um único sistema operacional ou hardware, pois seus programas rodam através de uma máquina virtual que pode ser emulada.

* **Java SE** (Java Platform, Standard Edition) → base da plataforma, traz classes em comum entre as plataformas
* **Java EE** (Java Platform, Enterprise Edition) → cuida do desenvolvimento web
* **Java ME** (Java Platform, Micro Edition) → cuida do desenvolvimento de dispositivos móveis e embarcados (calculadora, modem, urna, etc.)

---

## Fases da Execução Java

1. Escrevemos o seu código-fonte (arquivo com a extensão .java)
2. Utilizamos o JDK para compilar o seu código-fonte e gerar o arquivo bytecode (arquivo com a extensão .class)
3. Para executar o seu programa, a JVM lê o arquivo compilado (.class) e as bibliotecas padrões do Java que estão no JRE

<div>
    <fieldset>
        <legend>JDK</legend>
        java, javac, jdb, appletviewer, javah, javaw, jar, rmi...
        <fieldset>
            <legend>JRE</legend>
            Class Loader, Bye Code Verifier, Java API, Runtime Libraries
            <fieldset>
                <legend>JVM</legend>
                Java Interpreter, JIT(Just In Time), Garbage Collector, Thread Sync...
            </fieldset>
        </fieldset>
    </fieldset>
</div>

---

## Java Virtual Machine

Java Source File → Java Compiler → Java Class File → Java Virtual Machine [Interpreter] → Operating System

---

## JDK x JRE

* JDK (Java Development Kit) - é o Kit de Desenvolvimento Java responsável por compilar código-fonte (.java) em bytecode (.class)
* JVM (Java Virtual Machine) - é a Máquina Virtual do Java responsável por executar o bytecode (.class)
* JRE (Java Runtime Environment) - Ambiente de Execução do Java que fornece as bibliotecas padrões do Java para o JDK compilar o seu código e para a JVM executar o seu programa

---

## Versões Java

* Principal diferença entre OpenJDK e JDK Oracle: O OpenJDK é um Java totalmente open source com uma GNU General Public License e já o JDK Oracle requer uma licença comercial sob o Contrato de Licença de Código Binário Oracle
* Os lançamentos das versões OpenJDK LTS (suporte de longo prazo) acontecem pelo menos a cada quetro anos.

---

## O que é IDE?

* IDE, ou ambiente de desenvolvimento integrado, é um software que combina ferramentas comusn de desenvolvimento em uma única interface gráfica do usuário (GUI), facilitando o desenvolvimento de aplicações.
* O Java possui um conjunto de ferramentas para se desenvolver programas baseados nele, que são conhecidos como Java Development Kit ou JDK, sendo este o ambiente voltado para os desenvolvedores.
* A JDK faz parte do funionamento das IDE's - programas de desenvolvimento como IntelliJ, Eclipse, NetBeans, entre outros.

Eclipse é uma IDE para desenvolvimento Java, porém suporta várias outras linguagens. Ele foi feito em Java e segue o modelo open source de desenvovimento de software.

O IntelliJ IDEA é um ambiente de desenvolvimento integrado escrito em Java para o desenvolvimento de software de computador. Está disponível como uma edição da comunidade licenciada Apache 2, [6] e em uma edição comercial proprietária.

---

## Instalando Java, IDE's e o Git

[Siga o link clicando aqui](https://github.com/cami-la/curso-dio-dominando-ides-java/blob/master/README.md)
