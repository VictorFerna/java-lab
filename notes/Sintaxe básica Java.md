# SINTEXE BÁSICA DE JAVA

A **Sintaxe** define as regras utilizadas para organizar os elementos da linguagem Java.

Assim como uma língua natural possui regras para organizar palavras e formar frases compreensíveis, uma linguagem de programação possui regras para organizar palavras-chave, indentificadores, operadores, expressões e blocos de código.

Um código pode representar uma ideia lógica correta e ainda assim não ser aceito pelo compilador caso esteja escrito fora das regras sintáticas da linguagem.

```text
LÓGICA → o que o programa deve fazer

SINTAXE → como essa ideia deve ser escrita segundo as regras da linguagem.
```

Aprender sintaxe, portanto, não significa decorar símbolos isoladamente.

O objetivo é conseguir olhar para um código Java e reconhecer como suas partes estão organizadas e qual papel cada uma delas desempenha.

---

## PRIMEIRO CÓDIGO

Um dos primeiros **programas** apresentados durante o estudo de Java normalmente possui esta estrutura:

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }

}
```

Inicialmente esse código parecer ter muitas informações ao mesmo tempo: ***"public, class, Main, static, void, main, String, args, System, out, println"***.

Algumas dessas construções pertecem a assuntos que serão estudados posteriomente, como classes, modificadores de acesso, métodos, parâmetros e tipos.

antes disso podemos enxergar o programa de maneira estrutural:

```text
classe
  ↓
método
  ↓
instrução
```

No exemplo:

```text
Main
  ↓
main
  ↓
System.out.println()
```

A classe **Main** contém o método **main**, o método contém uma instrução.

Essa estrutura simples já permite começar a entender como um programa java é organizado.

---

## ARQUIVO E CLASSE

No Java, o código-fonte normalmente é escrito em arquivos com a extensão `.java`. Esses arquivos contêm declarações que o compilador **javac** analisa para gerar o bytecode, geralmente armazenado em arquivos `.class`.

Uma das principais estruturas utilizadas para organizar o código Java é a **classe**.

Uma classe define uma estrutura na qual podemos organizar informações, comportamentos e outras declarações relacionadas.

Por exemplo, imagine que estamos desenvolvendo um sistema para cadastrar pessoas. Cada pessoa pode possuir informações como nome e idade, além de comportamentos como apresentar seus dados.

Em Java, podemos representar essa estrutura através de uma classe chamada `Pessoa`.

Antes de construir esse exemplo, precisamos entender como uma classe é declarada e quais regras ela deve seguir.

### DECLARAÇÃO DE UMA CLASSE

No modelo tradicional de programação Java, uma classe pública pode ser declarada da seguinte maneira:

```java
public class Main {

}
```

Podemos interpretar:

```text
public class Main
  │      │    │
  │      │    └── Nome da classe
  │      │
  │      └── Palavra-chave para declarar uma classe
  │
  └── Modificador de acesso
```

Cada elemento possui uma função:

- **`public`:** modificador de acesso que permite que a classe seja utilizada por outras classes, inclusive de outros pacotes, respeitando as regras de acesso e módulos do projeto.
- **`class`:** palavra-chave da linguagem Java utilizada para declarar uma classe.
- **`Main`:** identificador escolhido para representar o nome da classe.
- **`{ }`:** chaves que delimitam o corpo da classe, onde podemos declarar atributos, métodos, construtores e outras estruturas permitidas.

O nome `Main` não possui um significado especial para a linguagem Java. Ele é apenas um nome frequentemente utilizado para identificar a classe que contém o ponto de entrada de um programa.

Poderíamos utilizar outro nome:

```java
public class SistemaCadastro {

}
```

Nesse caso, estamos declarando uma classe pública chamada `SistemaCadastro`.

**Importante:** declarar uma classe não significa executar automaticamente as instruções do programa. Estamos apenas definindo uma estrutura que poderá ser utilizada durante a execução.

### NOME DO ARQUIVO E DA CLASSE

Quando declaramos uma classe pública de nível superior, o nome do arquivo `.java` deve corresponder ao nome dessa classe.

Por exemplo:

```java
public class Main {

}
```

O arquivo deve se chamar:

```text
Main.java
```

Outro exemplo:

```java
public class PaymentService {

}
```

O arquivo deve se chamar:

```text
PaymentService.java
```

Isso acontece porque o Java possui regras para organizar as declarações públicas de nível superior nos arquivos de código-fonte.

Entretanto, nem toda classe precisa ser pública.

Um arquivo `.java` pode conter várias classes, desde que respeite algumas regras:

- **Apenas uma classe pública de nível superior por arquivo:** se existir, seu nome deverá corresponder ao nome do arquivo.
- **Classes sem `public`:** podem existir no mesmo arquivo e possuem acesso de pacote (*package-private*).
- **Classes aninhadas:** podem ser declaradas dentro de outras classes, seguindo suas próprias regras de acesso e organização.

Se o arquivo se chamar `Main.java`, mas sua classe pública de nível superior for declarada como `SistemaCadastro`, o compilador normalmente apresentará um erro.

```java
// Arquivo: Main.java

public class SistemaCadastro {

}
```

Nesse caso, o nome correto do arquivo seria `SistemaCadastro.java`.

O compilador **javac** identifica essa incompatibilidade e interrompe a compilação. Portanto, não temos uma compilação bem-sucedida do programa.

### CLASSES PÚBLICAS E CLASSES SEM MODIFICADOR DE ACESSO

Observe as duas declarações:

```java
public class Main {

}
```

```java
class Pessoa {

}
```

Ambas representam classes Java, mas possuem regras diferentes de visibilidade.

A principal diferença está no modificador `public`.

| Característica | `public class` | `class` sem modificador |
|---|---|---|
| Visibilidade | Pode ser acessada por classes de outros pacotes, respeitadas as regras de acesso. | Pode ser acessada apenas pelas classes do mesmo pacote. |
| Modificador de acesso | `public` | Acesso de pacote (*package-private*). |
| Nome do arquivo | Deve corresponder ao nome da classe pública de nível superior. | Não precisa corresponder ao nome da classe. |
| Quantidade no arquivo | No máximo uma classe pública de nível superior. | Podem existir várias classes de nível superior sem `public`. |
| Utilização | Classes que precisam ficar acessíveis fora do pacote, quando permitido. | Classes utilizadas dentro do próprio pacote. |

Um **pacote**, ou *package*, é uma forma de organizar classes relacionadas em um projeto Java.

Por enquanto, basta compreender que o pacote estabelece um agrupamento lógico de classes e também influencia quais delas podem acessar determinados elementos.

Posteriormente, quando estudarmos pacotes e modificadores de acesso, veremos essas regras com mais detalhes.

---

## CLASSES DE NÍVEL SUPERIOR E CLASSES ANINHADAS

Sabemos que uma classe representa uma estrutura. Entretanto, uma dúvida comum é se podemos declarar várias classes dentro de um único arquivo Java.

A resposta é **sim**.

Podemos organizar essas classes de duas formas principais:

1. **Classes de nível superior (*top-level classes*):** declaradas diretamente no arquivo, fora de outras classes.
2. **Classes aninhadas (*nested classes*):** declaradas dentro do corpo de outra classe.

Essas estruturas não são equivalentes, pois possuem diferenças de organização, acesso e utilização.

### CLASSES DE NÍVEL SUPERIOR

Uma classe de nível superior é aquela declarada diretamente no arquivo, sem estar dentro de outra classe.

Por exemplo:

```java
public class Main {

}

class Pessoa {

}

class Endereco {

}
```

Nesse exemplo, temos três classes de nível superior: `Main`, `Pessoa` e `Endereco`.

Todas estão no mesmo arquivo, mas nenhuma foi declarada dentro de outra.

Observe a organização:

```text
Main.java
│
├── public class Main
│
├── class Pessoa
│
└── class Endereco
```

A classe `Main` possui o modificador `public`, enquanto `Pessoa` e `Endereco` não possuem modificadores de acesso explícitos.

Por isso, `Pessoa` e `Endereco` possuem acesso de pacote.

Essas classes podem ser utilizadas normalmente por outras classes do mesmo pacote.

Por exemplo, dentro de `Main`, poderíamos criar um objeto da classe `Pessoa`:

```java
Pessoa pessoa = new Pessoa();
```

Não precisamos escrever `Main.Pessoa`, pois `Pessoa` não está declarada dentro de `Main`.

Também não existe um limite específico de duas ou três classes desse tipo por arquivo. Podemos declarar várias classes de nível superior sem `public`, embora dividir classes relevantes em arquivos próprios normalmente facilite a organização e manutenção do projeto.

### CLASSES ANINHADAS

Uma classe aninhada é declarada dentro de outra classe.

Observe:

```java
public class Main {

    public static class Pessoa {

    }

}
```

Nesse caso, a classe `Pessoa` está dentro da classe `Main`.

Podemos representar a estrutura da seguinte maneira:

```text
Main.java
│
└── public class Main
    │
    └── public static class Pessoa
```

A classe `Main` é chamada de **classe externa**.

A classe `Pessoa` é chamada de **classe aninhada**.

Uma classe aninhada pode ajudar a organizar estruturas que possuem uma relação direta com a classe externa.

Isso não significa que ela seja obrigatoriamente mais importante, mais rápida ou mais poderosa que uma classe de nível superior.

A principal diferença está na maneira como essas classes são organizadas e em suas relações com a classe externa.

### O QUE SIGNIFICA `PUBLIC STATIC CLASS`?

Observe:

```java
public static class Pessoa {

}
```

Aqui temos dois modificadores:

**`public`:** indica que a classe aninhada pode ser acessada de fora da classe externa, desde que a própria classe externa seja acessível.

**`static`:** indica que a classe aninhada não depende de um objeto da classe externa para ser instanciada.

Esse segundo ponto é importante.

Imagine que declaramos:

```java
public class Main {

    public static class Pessoa {

    }

}
```

Podemos criar um objeto da classe `Pessoa` utilizando:

```java
Main.Pessoa pessoa = new Main.Pessoa();
```

Vamos interpretar:

```text
Main.Pessoa pessoa = new Main.Pessoa();
     │       │       │       │
     │       │       │       └── Construtor chamado
     │       │       │
     │       │       └── Criação de um novo objeto
     │       │
     │       └── Nome da variável
     │
     └── Classe Pessoa declarada dentro de Main
```

A expressão `Main.Pessoa` identifica a classe aninhada `Pessoa`, que pertence à estrutura da classe `Main`.

O operador `new` permite criar um novo objeto.

Uma **instância**, ou **objeto**, é uma representação concreta criada a partir de uma classe.

Por enquanto, podemos entender essa diferença de maneira simples:

```text
CLASSE → define uma estrutura.

OBJETO → representa uma instância dessa estrutura.
```

Por exemplo, a classe `Pessoa` define que uma pessoa pode possuir nome e idade.

Já um objeto dessa classe pode representar uma pessoa específica, com valores próprios para essas informações.

Esse conceito será aprofundado posteriormente em Programação Orientada a Objetos (POO).

**Importante:** utilizar `static` em uma classe aninhada não significa que todos os atributos e métodos declarados dentro dela serão estáticos. Cada membro possui suas próprias regras.

### PODEMOS DECLARAR `PUBLIC STATIC CLASS` FORA DE OUTRA CLASSE?

Não.

Uma classe de nível superior não pode ser declarada com o modificador `static`.

O seguinte código é inválido:

```java
public static class Pessoa {

}
```

Quando essa declaração aparece diretamente no arquivo, fora de outra classe, o compilador apresenta um erro.

Entretanto, a declaração passa a ser válida quando está dentro de outra classe:

```java
public class Main {

    public static class Pessoa {

    }

}
```

Portanto, a palavra `static`, nesse contexto, está relacionada à característica de uma classe aninhada.

Também podemos declarar classes aninhadas que não são `static`. Elas são chamadas de **classes internas** (*inner classes*) e possuem uma relação diferente com os objetos da classe externa.

Não precisamos aprofundar esse segundo tipo neste momento.

---

## ATRIBUTOS, MÉTODOS E OBJETOS

Agora que conhecemos a estrutura de uma classe, podemos entender o que ela pode conter.

Uma classe não precisa ficar vazia.

Podemos declarar informações e comportamentos relacionados à estrutura que queremos representar.

Imagine novamente uma classe `Pessoa`.

```java
class Pessoa {

    String nome;
    int idade;

    void apresentar() {
        System.out.println("Nome: " + nome);
        System.out.println("Idade: " + idade);
    }

}
```

Essa classe contém dois atributos e um método.

### O QUE SÃO ATRIBUTOS?

Os **atributos** são campos declarados em uma classe que podem representar informações e características dos objetos.

No exemplo:

```java
String nome;
int idade;
```

Temos dois atributos:

- `nome`: armazena uma referência a um texto do tipo `String`.
- `idade`: armazena um número inteiro do tipo `int`.

Quando criamos um objeto de `Pessoa`, ele possui seus próprios valores para esses atributos, pois eles não foram declarados como `static`.

Por exemplo:

```java
Pessoa pessoa = new Pessoa();

pessoa.nome = "Victor";
pessoa.idade = 23;
```

Nesse código:

1. Criamos um objeto da classe `Pessoa`.
2. Guardamos a referência desse objeto na variável `pessoa`.
3. Atribuímos o texto `"Victor"` ao atributo `nome`.
4. Atribuímos o número `23` ao atributo `idade`.

O ponto (`.`) permite acessar membros do objeto, respeitando suas regras de acesso.

Observe também que `String` e `int` representam tipos diferentes de dados.

Posteriormente, no tópico de variáveis e tipos de dados, estudaremos com mais detalhes como essas declarações funcionam.

### O QUE SÃO MÉTODOS?

Um **método é um bloco de código declarado em uma classe para representar uma operação ou comportamento**.

Ele permite organizar instruções que podem ser executadas quando o método é chamado.

No exemplo:

```java
void apresentar() {

    System.out.println("Nome: " + nome);
    System.out.println("Idade: " + idade);

}
```

Criamos um método chamado `apresentar()`.

Quando esse método é chamado, ele executa as instruções que estão dentro de suas chaves.

Observe:

```java
pessoa.apresentar();
```

Estamos solicitando que o objeto referenciado pela variável `pessoa` execute o método `apresentar()`.

A declaração do método e a chamada do método são coisas diferentes:

```java
// Declaração do método
void apresentar() {

    System.out.println("Olá!");

}
```

```java
// Chamada do método
pessoa.apresentar();
```

A declaração define o comportamento.

A chamada solicita sua execução.

Métodos também podem receber informações por meio de **parâmetros** e devolver resultados utilizando `return`.

Por exemplo:

```java
static boolean maiorDeIdade(int idade) {

    return idade >= 18;

}
```

Nesse caso:

- `boolean` indica que o método devolve um valor lógico.
- `maiorDeIdade` é o nome do método.
- `int idade` é um parâmetro utilizado para receber um número inteiro.
- `return` devolve o resultado da comparação.

A expressão `idade >= 18` verifica se o valor recebido é maior ou igual a 18.

O resultado será `true` ou `false`.

Vamos estudar métodos com mais profundidade em um tópico próprio. Neste momento, o importante é reconhecer como eles aparecem dentro das classes.

---

## EXEMPLO PRÁTICO: ORGANIZANDO CLASSES EM UM ÚNICO ARQUIVO

Agora podemos juntar os conceitos estudados em um exemplo completo.

Vamos desenvolver um pequeno programa de cadastro de pessoas.

Nosso programa deverá:

1. Criar uma pessoa e registrar seu nome e idade.
2. Apresentar as informações cadastradas.
3. Verificar se essa pessoa é maior de idade.
4. Registrar e apresentar seu endereço.
5. Exibir uma mensagem de finalização.

Para isso, utilizaremos um único arquivo `Main.java`, contendo classes aninhadas e classes de nível superior.

```java
public class Main {

    // 1. Classe aninhada estática
    public static class Pessoa {

        String nome;
        int idade;

        void apresentar() {
            System.out.println("Nome: " + nome);
            System.out.println("Idade: " + idade);
        }
    }

    // 2. Outra classe aninhada estática
    public static class Verificador {

        static boolean maiorDeIdade(int idade) {
            return idade >= 18;
        }
    }

    // 3. Ponto de entrada do programa
    public static void main(String[] args) {

        Main.Pessoa pessoa = new Main.Pessoa();

        pessoa.nome = "Victor";
        pessoa.idade = 23;

        pessoa.apresentar();

        boolean resultado =
            Main.Verificador.maiorDeIdade(pessoa.idade);

        System.out.println("Maior de idade: " + resultado);

        Endereco endereco = new Endereco();

        endereco.cidade = "Brasília";
        endereco.uf = "DF";

        endereco.mostrarEndereco();

        Mensagem.exibir();
    }
}

// 4. Classe de nível superior sem public
class Endereco {

    String cidade;
    String uf;

    void mostrarEndereco() {
        System.out.println("Cidade: " + cidade);
        System.out.println("UF: " + uf);
    }
}

// 5. Outra classe de nível superior sem public
class Mensagem {

    static void exibir() {
        System.out.println("Cadastro finalizado!");
    }
}
```

**Saída:**

```text
Nome: Victor
Idade: 23
Maior de idade: true
Cidade: Brasília
UF: DF
Cadastro finalizado!
```

Apesar de o programa possuir várias classes, todas elas foram declaradas no mesmo arquivo.

Vamos entender o papel de cada uma.

### 1. `PUBLIC CLASS MAIN`

```java
public class Main {

}
```

Essa é a classe pública de nível superior do programa.

Ela contém duas classes aninhadas e o método `main`, utilizado como ponto de entrada da execução tradicional.

É importante compreender que o nome `Main` não faz uma classe ser executada automaticamente.

O Java utiliza um método de entrada válido na classe que solicitamos executar.

### 2. `PUBLIC STATIC CLASS PESSOA`

```java
public static class Pessoa {

    String nome;
    int idade;

    void apresentar() {
        System.out.println("Nome: " + nome);
        System.out.println("Idade: " + idade);
    }
}
```

Essa é uma classe aninhada estática declarada dentro de `Main`.

Sua função é representar a estrutura de uma pessoa.

Ela contém informações, como nome e idade, e um comportamento, representado pelo método `apresentar()`.

Quando escrevemos:

```java
Main.Pessoa pessoa = new Main.Pessoa();
```

Criamos um novo objeto dessa classe.

Não precisamos criar um objeto de `Main` para fazer isso, pois `Pessoa` foi declarada como uma classe aninhada `static`.

Podemos criar vários objetos `Pessoa`:

```java
Main.Pessoa pessoa1 = new Main.Pessoa();
Main.Pessoa pessoa2 = new Main.Pessoa();

pessoa1.nome = "Ana";
pessoa2.nome = "Carlos";
```

Esses objetos são independentes e podem possuir valores diferentes para os mesmos atributos.

### 3. `PUBLIC STATIC CLASS VERIFICADOR`

```java
public static class Verificador {

    static boolean maiorDeIdade(int idade) {
        return idade >= 18;
    }
}
```

Essa também é uma classe aninhada estática, mas possui uma responsabilidade diferente.

Seu objetivo é agrupar uma operação que verifica se a idade informada é maior ou igual a 18.

Observe que o método `maiorDeIdade()` também possui o modificador `static`.

Isso permite chamá-lo diretamente pela classe:

```java
Main.Verificador.maiorDeIdade(23);
```

Não precisamos criar um objeto de `Verificador` para executar esse método.

Aqui temos uma diferença importante:

- **`static` na classe aninhada:** indica que sua instância não depende de uma instância da classe externa.
- **`static` no método:** indica que o método pertence à classe, não a um objeto específico.

São duas utilizações diferentes do mesmo modificador.

### 4. `CLASS ENDERECO`

```java
class Endereco {

    String cidade;
    String uf;

    void mostrarEndereco() {
        System.out.println("Cidade: " + cidade);
        System.out.println("UF: " + uf);
    }
}
```

Essa classe está fora do corpo de `Main`.

Portanto, é uma classe de nível superior com acesso de pacote.

Sua função é representar informações relacionadas a um endereço.

No método `main`, criamos um objeto:

```java
Endereco endereco = new Endereco();
```

Depois, atribuímos valores aos atributos e chamamos seu método:

```java
endereco.cidade = "Brasília";
endereco.uf = "DF";

endereco.mostrarEndereco();
```

Observe que não utilizamos `Main.Endereco`.

Isso acontece porque `Endereco` não foi declarada dentro de `Main`.

### 5. `CLASS MENSAGEM`

```java
class Mensagem {

    static void exibir() {
        System.out.println("Cadastro finalizado!");
    }
}
```

Essa também é uma classe de nível superior com acesso de pacote.

Entretanto, diferentemente da classe `Endereco`, nosso exemplo utiliza um método estático.

Por isso, podemos chamá-lo diretamente:

```java
Mensagem.exibir();
```

Perceba que não precisamos declarar `static` na própria classe para utilizar métodos estáticos.

Na verdade, uma classe de nível superior não pode possuir o modificador `static`, mas seus métodos podem.

### COMPARANDO AS ESTRUTURAS

| Declaração | Tipo | Função no exemplo |
|---|---|---|
| `public class Main` | Classe pública de nível superior | Organizar a estrutura principal e conter o método de entrada. |
| `public static class Pessoa` | Classe aninhada estática | Representar pessoas e seus dados. |
| `public static class Verificador` | Classe aninhada estática | Agrupar a operação de verificação da idade. |
| `class Endereco` | Classe de nível superior com acesso de pacote | Representar informações de endereço. |
| `class Mensagem` | Classe de nível superior com acesso de pacote | Agrupar a mensagem de finalização. |
| `public static void main(...)` | Método estático | Servir como ponto de entrada da execução tradicional. |

As classes não precisam executar tarefas diferentes apenas por possuírem declarações diferentes.

Uma classe de nível superior também pode representar pessoas, conter métodos estáticos ou realizar verificações.

A escolha entre uma classe independente e uma classe aninhada depende principalmente de como desejamos organizar os elementos do programa e das relações entre eles.

### COMO O JAVA ORGANIZA ESSAS CLASSES NA COMPILAÇÃO?

Quando compilamos o código utilizando:

```bash
javac Main.java
```

O compilador analisa as classes declaradas no arquivo e, em uma compilação bem-sucedida, normalmente gera:

```text
Main.java
│
├── Main.class
├── Main$Pessoa.class
├── Main$Verificador.class
├── Endereco.class
└── Mensagem.class
```

Observe que, embora todas as classes estejam no mesmo arquivo de código-fonte, elas possuem representações próprias no bytecode gerado.

O caractere `$`, nesse caso, aparece no nome binário gerado para as classes aninhadas.

Ao executar:

```bash
java Main
```

Estamos solicitando que a JVM inicie a aplicação utilizando a classe `Main`.

Entretanto, isso não significa que a JVM executará todas as classes automaticamente.

O programa seguirá as instruções do método de entrada e utilizará as demais classes conforme necessário.

---

## O MÉTODO MAIN

Agora que entendemos a estrutura de um arquivo Java, as classes, os atributos e os métodos, podemos retornar ao primeiro código apresentado neste documento:

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }

}
```

Sabemos que `public class Main` representa a declaração de uma classe.

Mas qual é a função de:

```java
public static void main(String[] args)
```

Na forma tradicional de execução de um programa Java, esse método funciona como o **ponto de entrada da aplicação**.

Isso significa que, quando solicitamos a execução da classe `Main`, a JVM procura um método de entrada válido e começa a executar as instruções definidas nele.

Vamos separar os elementos da declaração:

```text
public static void main(String[] args)
  │      │     │    │         │
  │      │     │    │         └── Parâmetro do método
  │      │     │    │
  │      │     │    └── Nome do método
  │      │     │
  │      │     └── Tipo de retorno
  │      │
  │      └── Modificador static
  │
  └── Modificador de acesso
```

### `PUBLIC` — MODIFICADOR DE ACESSO

O modificador `public` determina que o método pode ser acessado de fora da classe.

Na declaração tradicional do método `main`, utilizamos `public` para tornar o método acessível como ponto de entrada do programa.

### `STATIC` — MÉTODO DA CLASSE

O modificador `static` indica que o método pertence à classe e pode ser chamado sem a necessidade de criar um objeto dessa classe.

Por exemplo:

```java
Main.main(new String[0]);
```

Essa instrução realiza uma chamada direta ao método estático `main`, passando um array vazio de textos como argumento.

Isso é diferente de criar um objeto:

```java
Main objeto = new Main();
```

A criação desse objeto, por si só, não executa automaticamente o método `main`.

### `VOID` — TIPO DE RETORNO

A palavra `void` indica que o método não devolve um valor para quem o chamou.

Isso não significa que o método não possa realizar operações.

Por exemplo:

```java
public static void main(String[] args) {

    System.out.println("Hello, Java!");

}
```

O método executa uma instrução que apresenta uma mensagem no terminal, mesmo sem devolver um valor.

### `MAIN` — NOME DO MÉTODO

`main` é o nome tradicionalmente reconhecido pela JVM como método de entrada de uma aplicação Java.

Observe que `Main` e `main` são identificadores diferentes:

```java
public class Main {

    public static void main(String[] args) {

    }

}
```

- `Main`, com letra maiúscula, é o nome da classe.
- `main`, com letra minúscula, é o nome do método.

O Java diferencia letras maiúsculas e minúsculas. Essa característica é chamada de **case-sensitive**.

Portanto, `Main` e `main` não são a mesma coisa.

### `STRING[] ARGS` — PARÂMETRO DO MÉTODO

O trecho:

```java
String[] args
```

Representa um parâmetro capaz de receber um array de textos.

Podemos dividir essa declaração em duas partes:

- `String[]`: indica um array cujos elementos são do tipo `String`.
- `args`: é o nome escolhido para o parâmetro.

Um **parâmetro** é uma variável declarada na definição de um método para receber informações enviadas durante sua chamada.

Já um **argumento** é o valor efetivamente fornecido quando chamamos esse método.

No caso do `main`, os argumentos podem ser enviados pela linha de comando ao iniciar o programa.

Imagine o seguinte código:

```java
public class Main {

    public static void main(String[] args) {

        System.out.println(args[0]);
        System.out.println(args[1]);

    }

}
```

Após compilar, podemos executar:

```bash
java Main Victor 23
```

O programa recebe dois argumentos:

```text
args[0] → "Victor"

args[1] → "23"
```

A saída será:

```text
Victor
23
```

Observe que, embora `23` represente um número, ele foi recebido como texto, pois os argumentos do `main` são elementos de um array de `String`.

Também precisamos ter cuidado: se tentarmos acessar `args[1]` sem fornecer pelo menos dois argumentos, ocorrerá uma exceção por acessar uma posição inexistente do array.

Arrays e seus índices serão estudados posteriormente.

### O MÉTODO MAIN É OBRIGATÓRIO?

Na maneira tradicional de criar e executar aplicações Java, utilizamos:

```java
public static void main(String[] args)
```

Entretanto, isso não significa que toda classe precisa possuir um método `main`.

Por exemplo, podemos declarar:

```java
public class Pessoa {

    String nome;
    int idade;

}
```

Essa classe não possui `main`, mas continua sendo uma classe Java válida.

Ela pode ser utilizada por outras classes durante a execução do programa.

Também existem aplicações Java cuja execução é organizada por frameworks ou outros mecanismos.

Além disso, versões modernas da linguagem, como o Java 25, permitem formas simplificadas de declarar métodos de entrada.

Portanto, é mais correto afirmar que:

**O método `main` é a forma tradicional de definir o ponto de entrada de uma aplicação Java, mas nem toda classe precisa possuir esse método, e a linguagem moderna admite outras formas de inicialização.**

Neste estudo, utilizaremos inicialmente a declaração tradicional, pois ela permite compreender explicitamente a estrutura da classe, os modificadores, os métodos e os parâmetros.

### COMO O PROGRAMA É EXECUTADO?

Considere:

```java
public class Main {

    public static void main(String[] args) {

        System.out.println("Início");

        apresentar();

        System.out.println("Fim");
    }

    public static void apresentar() {

        System.out.println("Olá, Java!");

    }
}
```

A saída será:

```text
Início
Olá, Java!
Fim
```

A execução acontece da seguinte maneira:

```text
java Main
    │
    ▼
JVM inicia o programa
    │
    ▼
main(String[] args)
    │
    ├── Imprime "Início"
    │
    ├── Chama apresentar()
    │       │
    │       └── Imprime "Olá, Java!"
    │
    └── Imprime "Fim"
```

Quando o programa encontra a chamada `apresentar()`, ele executa as instruções desse método.

Depois que o método termina, a execução retorna ao ponto seguinte à chamada, dentro de `main`.

Perceba que o método `apresentar()` foi declarado depois do método `main`, mas isso não impede sua utilização.

A ordem em que os métodos aparecem no arquivo não determina, por si só, a ordem em que serão executados.

O que determina o fluxo da execução são as instruções e chamadas realizadas pelo programa.

### RESUMO

A estrutura básica de um programa Java pode ser compreendida da seguinte maneira:

```text
ARQUIVO .JAVA
    │
    └── CLASSE
         │
         ├── ATRIBUTOS
         │    └── Informações relacionadas à classe
         │
         ├── MÉTODOS
         │    └── Operações e comportamentos
         │
         ├── CLASSES ANINHADAS
         │    └── Outras classes declaradas internamente
         │
         └── MAIN
              └── Ponto de entrada tradicional
```

**Classe** define uma estrutura.

**Objeto** é uma instância criada a partir de uma classe.

**Atributo** representa um campo de informação declarado na classe.

**Método** representa uma operação ou comportamento que pode ser executado.

**Parâmetro** recebe informações fornecidas a um método durante sua chamada.

**`static`** possui diferentes aplicações, como permitir métodos pertencentes à classe e declarar classes aninhadas que não dependem de uma instância da classe externa.

**`main`** é o método tradicionalmente utilizado como ponto de entrada da aplicação Java.

Esses elementos ajudam a compreender como um programa é estruturado e como suas instruções são organizadas.

Até agora, utilizamos declarações como:

```java
String nome;
int idade;
boolean resultado;
```

Também utilizamos o operador `=` para atribuir valores a essas variáveis e atributos.

Mas o que significa declarar uma variável? Por que precisamos indicar um tipo? Qual é a diferença entre `int`, `double`, `boolean`, `char` e `String`?

Essas perguntas nos levam ao próximo conteúdo: **variáveis e tipos de dados em Java**.