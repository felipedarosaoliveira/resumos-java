**Tutorial sobre Interfaces Funcionais e Expressões Lambda em Java**

As interfaces funcionais e as expressões lambda são recursos poderosos introduzidos no Java 8 que simplificam a programação funcional e melhoram a legibilidade e a concisão do código. Neste tutorial, vamos explorar o que são interfaces funcionais, como as expressões lambda se encaixam nelas e como utilizar esses recursos para criar código mais elegante e eficiente em Java.

### **O que são Interfaces Funcionais?**

Uma interface funcional é uma interface que contém exatamente um único método abstrato. Ela é usada como a base para a criação de expressões lambda e também é conhecida como **SAM (Single Abstract Method)** ou **interfaces de função**. Embora tenha apenas um método abstrato, uma interface funcional ainda pode conter métodos padrão e estáticos.

### **Benefícios das Interfaces Funcionais**

As interfaces funcionais trazem vários benefícios para o desenvolvimento de software em Java:

1. **Sintaxe Concisa:** Com a introdução de expressões lambda, você pode escrever blocos de código de forma mais compacta e clara.

2. **Legibilidade:** As expressões lambda permitem que você se concentre na lógica essencial e elimine a necessidade de escrever código repetitivo.

3. **Programação Funcional:** Com as interfaces funcionais, o Java tornou-se mais apto para programação funcional, permitindo tratar funções como valores de primeira classe.

### **Sintaxe de Expressões Lambda**

Uma expressão lambda é uma forma concisa de representar uma função anônima que pode ser passada como argumento para métodos ou atribuída a variáveis. A sintaxe básica de uma expressão lambda é a seguinte:

```java
(parametros) -> expressao
```

- `parametros`: Lista de parâmetros da função.
- `->`: Setas que separam os parâmetros da expressão.
- `expressao`: Corpo da função que realiza a operação desejada.

### **Exemplos de Interfaces Funcionais e Expressões Lambda**

Vamos explorar alguns exemplos de interfaces funcionais com suas respectivas expressões lambda:

1. **`Runnable` e Expressão Lambda**

   A interface funcional `Runnable` possui um único método abstrato `run()`. Vamos criar uma instância de `Runnable` usando uma expressão lambda para executar uma tarefa.

   ```java
   Runnable tarefa = () -> {
       System.out.println("Executando tarefa...");
   };
   ```

2. **`Comparator` e Expressão Lambda**

   A interface funcional `Comparator` é amplamente usada para definir a ordem de classificação entre elementos. Vamos criar uma instância de `Comparator` usando uma expressão lambda para ordenar uma lista de strings por comprimento.

   ```java
   List<String> palavras = Arrays.asList("maçã", "banana", "laranja");
   palavras.sort((s1, s2) -> s1.length() - s2.length());
   ```

3. **`ActionListener` e Expressão Lambda**

   No contexto de interfaces gráficas, a interface funcional `ActionListener` é usada para lidar com eventos de botão. Vamos criar uma instância de `ActionListener` usando uma expressão lambda para responder ao clique de um botão.

   ```java
   JButton botao = new JButton("Clique aqui");
   botao.addActionListener(evento -> {
       System.out.println("Botão clicado!");
   });
   ```

### **Interfaces Funcionais Pré-Definidas**

O Java 8 introduziu diversas interfaces funcionais pré-definidas no pacote `java.util.function` que abrangem uma variedade de casos de uso. Algumas das interfaces mais comuns são:

- **`Function<T, R>`**: Representa uma função que aceita um argumento do tipo `T` e retorna um valor do tipo `R`.
- **`Predicate<T>`**: Representa uma função que avalia um argumento do tipo `T` e retorna um valor booleano.
- **`Consumer<T>`**: Representa uma função que aceita um argumento do tipo `T` e não retorna valor.
- **`Supplier<T>`**: Representa uma função que não aceita argumentos e retorna um valor do tipo `T`.

### **Exemplos de Uso de Interfaces Funcionais Pré-Definidas**

Vamos explorar exemplos de uso das interfaces funcionais pré-definidas:

1. **`Function` e Expressão Lambda**

   A interface `Function` é usada para realizar transformações em um valor. Vamos criar uma instância de `Function` para converter uma string em maiúsculas.

   ```java
   Function<String, String> converterMaiusculas = texto -> texto.toUpperCase();
   String resultado = converterMaiusculas.apply("hello world");
   ```

2. **`Predicate` e Expressão Lambda**

   A interface `Predicate` é usada para realizar verificações em um valor. Vamos criar uma instância de `Predicate` para verificar se um número é par.

   ```java
   Predicate<Integer> ehPar = numero -> numero % 2 == 0;
   boolean resultado = ehPar.test(6);
   ```

3. **`Consumer` e Expressão Lambda**

   A interface `Consumer` é usada para realizar ações em um valor. Vamos criar uma instância de `Consumer` para imprimir uma mensagem.

   ```java
   Consumer<String> imprimirMensagem = mensagem -> System.out.println(mensagem);
   imprimirMensagem.accept("Olá, mundo!");
   ```

### **Conclusão**

As interfaces funcionais e as expressões lambda revolucionaram a maneira como escrevemos código em Java. Elas oferecem uma abordagem mais concisa e legível para definir funções anônimas e promovem a programação funcional no mundo da linguagem orientada a objetos. Com o conhecimento adquirido neste tutorial, você pode começar a aproveitar os benefícios das interfaces funcionais e das expressões lambda em seus projetos Java, criando código mais eficiente, elegante e modular. À medida que você se familiarizar com esses conceitos, estará pronto para explorar ainda mais os recursos avançados oferecidos pelo Java moderno.

