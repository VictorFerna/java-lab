# JAVA, JAVAC, BYTECODE, JVM, JDK

Java é frequentimente ensinado como uma sequência de palavras-chave: classe, objeto, herança, interface, exceção e coleção. Esse caminho permite desenvolver programas, mas não explica o por que de um mesmo arquivo **.class** rodar em sistemas diferentes, por que duas referências diferentes podem apontar para o mesmo objeto, ou por que uma aplicação **SpringBoot** continua sendo uma aplicação **Java** que obedece às mesmas regras da linguagem e da **JVM**.

## ORIGEM

No ínicio da década de 90, uma equipe da Sun Microsystems liderada por James Gosling trabalhou no green project, voltado a software para dispositivos **eletrônicos heterogêneos**.
```text
Eletrônicos heterogêneos: são equipamentos que podem possuir diferentes arquiteturas de processadores, componentes e sistemas, dificultando a execução de um mesmo programa em todos eles.
```
Assim a linguagem **OAK** foi criada, o problema central era executar software em equipamento com processadores e sistemas distintos sem ter que recompilar toda aplicação para cada alvo.
Com a popularização da **Web**, a premissa de um código intermediário portátil tornou-se atraente para distribuição de programas pela rede. Oak foi renomeada para **Java** e apresentada publicamente em 1995, com o slogan ***"Write once, run anywhere"***, isso não significa que Java roda magicamente em qualquer dispositivo: depedências nativas, sistemas de arquivos, codificação, UI e comportamento externo ainda importam. 

A ideia técnica é que o compilador produz um formato de classe definido por especificação e que uma JVM compatível pode executar esse formato em diferentes plataformas.

|Termo|O que é|Principal Função|
|:--------|:--------|:--------|
|Java|Linguagem e conjunto de especificações da plataforma|Sintaxe, tipos, semântica, APIs padronizadas e contrato de execução|
|JVM|Máquina virtual definida pela JVMS|Carregar/verificar classes e executar bytecode conforme o modelo especificado|
|JDK|Kit de desenvolvimento|Compilador javac, java launcher, javadoc, jlink, debugger e demais ferramentas|
|JRE|Conceito de ambiente de execução distribuído separadamente em JDKs antigos|Runtime + bibliotecas; desde Java 9, aplicações podem empacotar runtimes customizados|
|OpenJDK|Implementação open source da plataforma Java SE|Código do JDK, incluindo HotSpot nas builds usuais|
|Oracle JDK|Distribuição da Oracle baseada no OpenJDK|Binários, licenciamento/suporte e empacotamento específicos da Oracle|
|Java SE|Plataforma Standard Edition |Linguagem, JVM e APIs fundamentais|
|Jakarta EE|Conjunto de especificações enterprise sobre Java|Servlets, Persistence, CDI, Messaging e outras APIs empresariais|

```text
COMPARAÇÃO IMPORTANTE
Java ≠ Spring ≠ Spring Boot ≠ JPA ≠ Hibernate. Spring é um ecossistema de framework; Spring
Boot configura e empacota aplicações Spring; JPA/Jakarta Persistence é uma especificação de
persistência; Hibernate ORM é uma implementação popular dessa especificação. Nenhuma dessas
peças redefine a sintaxe da linguagem Java.
```

## MODELO
```text
Java source (.java)
 ↓ javac
class file (.class / bytecode)
 ↓ JVM compatível
OS + arquitetura da máquina
```

---

O **MODELO** de execução do Java separa o código-fonte escrito pelo programador da arquitetura física da máquina, onde a aplicação será executada.

O arquivo **.java** contém o código-fonte da aplicação. Nesse estágio, o programa ainda está representado utilizando a sintaxe e as regras da linguagem Java. O processador não executa diretamente instruções como **class**, **if**, **while**, chamadas de métodos ou criação de objetos.
```text
Antes da execução, o código-fonte precisa ser processado pelo compilador Java.
```
---

**JAVAC** é o compilador disponibilizado pelo JDK. Sua funçã é analisar o código-fonte Java e gerar arquivos de classe no formato definido pela especificação da JVM.
```text
MeuPrograma.java
      ↓
    javac
      ↓
MeuPrograma.class
```
Durante essa etapa, o compilador verifica diversos aspectos do programa, como sintaxe, tipos, declarações de variáveis, chamadas de métodos e compatibilidade entre operações.

---

**BYTECODE** O arquivo **.class** contém a representação intermediária do programa, conhecido como bytecode.

O bytecode não corresponde diretamente ao conjunto de instruções de um processador físico. Ele foi projetado para ser interpretado pela arquitetura abstrata definida pela Java Virtual Machine.

Essa camada intermediária é uma das principais razões da portabilidade do Java.

- Em linguagens que compilam diretamente para código nativo, pode existir uma relação semelhante a: você tem um código fonte de uma **linguagem compilada**, esse código fonte é compilado pelo **compilador** voltado a uma arquitetura especifíca, como a **x86_64**.
Nesse caso, o programa gerado depende da arquitetura utilizada durante a compilação.

No Java, existe uma etapa intermediária:
```text
Código-fonte (.java)
        ↓
       javac
        ↓
Arquivo .class
(contém bytecode)
        ↓
       JVM
        ↓
Interpretação / JIT
        ↓
Execução na máquina
```
Portanto, o mesmo arquivo **.class** pode ser utilizado em diferentes plataformas, desde que exista naquela plataforma uma **JVM** capaz de interpretar corretamente a versão e o formato daquele bytecode.

---

**JVM** a JVM - Java Virtual Machine, é a responsável por fornecer o ambiente de execução definido para programas Java, ela recebe os arquivos .class, carrega suas definições, verifica sua estrutura e executa as instruções presentes no bytecode.

É importante perceber que a JVM é chamada de **"máquina virtual"** porque apresenta ao programa um modelo computacional abstrato.

Para o bytecode, não importa diretamente se o computador real utiliza: Um sistema Operacional Windows + x86_64, um Linux + x86_64 ou macOS + ARM64, o programa foi **compilado para um modelo da JVM**, e não diretamente para uma dessas arquiteturas ou sistemas.

A implementação concreta da JVM, por outro lado, precisa conhecer o sistema operacional e a arquitetura da máquina onde está sendo executada.
```text
Programa Java
     ↓
   Bytecode
     ↓
----------------------
     JVM
----------------------
     ↓
Sistema operacional
     ↓
Arquitetura física
```

O **bytecode** permanece essencialmente o mesmo, enquanto a implementação da **JVM** é adaptada para cada plataforma. Por esse motivo, não é correto interpretar o slogan Write once, run anywhere como se exatamente o mesmo ambiente de execução existisse fisicamente em todas as máquinas.

O que existe é um contrato comum definido pelas especificações Java, implementado por runtimes diferentes para cada plataforma.

---

**JVM COMPATÍVEL**
A expressão **"JVM compatível"** é importante porque nem todo bytecode pode necessariamente ser executado por qualquer versão antiga da JVM. Ao compilar um código Java, o javac gera arquivos **.class** associados a determinada versão do formato de classe.

Uma JVM precisa compreender aquela versão para carregá-la.

Por exemplo, um programa compilado utilizando recursos de uma versão mais recente do Java pode não funcionar em uma JVM muito antiga. Nesse caso, podem ocorrer erros relacionados à **incompatibilidade da versão** do arquivo de classe.

Portanto:
```text
.class
  ↓
JVM que compreende aquela versão
```
É uma descrição mais precisa do que simplesmente afirmar que qualquer JVM executará qualquer programa Java.

**SISTEMA OPERACIONAL E ARQUITETURA** A JVM não excluí a existência do S.O e do processador, ela funciona acima dessas camadas.
```text
Aplicação Java
      ↓
Bytecode
      ↓
JVM
      ↓
Sistema operacional
      ↓
Arquitetura / CPU
```
A JVM instalada em um computador com processador x86-64 é construída para essa **arquitetura**. Uma JVM distribuída para ARM64 contém código nativo apropriado para ARM64. Dessa forma, a portabilidade é transferida principalmente para a **camada do runtime**.

O desenvolvedor produz bytecode relativamente independente da plataforma, enquanto quem fornece a JVM precisa implementar corretamente a interação com cada sistema operacional e arquitetura.

```text
    OQUE ACONTECE DENTRO DE UMA JVM ?
O modelo inicial pode ser expandido:

Java source (.java)
        ↓
      javac
        ↓
class file (.class)
        ↓
   Class Loader
        ↓
   Verificação
        ↓
       JVM
   ┌────┴─────┐
   ↓          ↓
Interpreter   JIT
   ↓          ↓
   └────┬─────┘
        ↓
Código de máquina
        ↓
OS / CPU
```
O **Class Loader** é responsável por localizar e carregar classes necessárias para a execução. Antes de executar determinadas classes, a JVM também realiza verificações para garantir que a estrutura do bytecode obedeça às regras esperadas pelo runtime.

Depois disso, as instruções podem ser executadas inicialmente através de interpretação e, dependendo da implementação da JVM, partes importantes do programa podem ser **compiladas dinamicamente** para código nativo.

---

**INTERPRETER E JIT** Historicamente, uma das descrições mais comuns de Java era a de uma linguagem "interpretada". Essa definição, isoladamente, é incompleta para JVMs modernas. Uma implementação como a HotSpot pode combinar diferentes estratégias.

O interpreter pode começar executando diretamente as instruções do bytecode.

```text
bytecode
   ↓
interpreter
   ↓
execução
```
Enquanto o programa executa, a JVM pode coletar informações sobre quais métodos e trechos de código são utilizados com maior frequência.

Esses trechos podem então ser processados pelo **JIT — Just-In-Time Compiler**.
```text
bytecode frequentemente executado
             ↓
            JIT
             ↓
código de máquina nativo
```

O código gerado pelo JIT já pode ser específico para a arquitetura atual.

Se a aplicação estiver executando em x86-64, a JVM pode produzir instruções nativas para x86-64. Se estiver executando em ARM64, outra implementação da JVM poderá gerar código apropriado para ARM64. Isso permite que o Java mantenha um formato intermediário portátil e, ao mesmo tempo, obtenha otimizações específicas da máquina durante a execução.

Portanto, o JIT não é uma etapa obrigatória para que o programa funcione. Ele é um mecanismo de compilação dinâmica utilizado por determinadas implementações da JVM para otimizar a execução.

---

**SEPARAÇÃO ENTRE COMPILAÇÃO E EXECUÇÃO** É util separar essas duas interfaces, a primeira é da **compilação**:
```text
    COMPILAÇÃO:
.java
 ↓
javac
 ↓
.class
```

E a segunda é a **execução**:
```text
    EXECUÇÃO:
.class
 ↓
JVM
 ↓
código nativo
 ↓
CPU
```
O **javac** e a **JVM** possuem responsabilidades diferentes.

O **javac** trabalha principalmente com o código Java e produz bytecode.
"Este código Java está correto e pode ser transformado em bytecode?"

A **JVM** trabalha principalmente com esse bytecode e fornece o ambiente necessário para sua execução.
"Como esse bytecode será carregado, executado e gerenciado nesta máquina?"

- O javac conhece as regras da linguagem Java. A JVM conhece as regras do bytecode e do modelo de execução da máquina virtual.
Esses dois mundos estão relacionados, mas não são exatamente a mesma coisa, por exemplo, linguagens diferentes de Java, como Kotlin, Scala e Groovy podem gerar bytecode compatível com a JVM.

```text
Java source
   (.java)
      ↓
    javac
      ↓
class file
   (.class)
      ↓
   bytecode
      ↓
     JVM
      ↓
Interpreter / JIT
      ↓
código de máquina
      ↓
     CPU
```