**Tutorial Completo das Operações Terminais da API `java.util.stream` em Java**

A API `java.util.stream` oferece uma ampla gama de operações terminais para concluir o processamento de streams, obtendo resultados ou realizando ações finais nos elementos. Neste tutorial, vamos explorar detalhadamente cada uma dessas operações, fornecendo exemplos práticos para ajudar você a entender como aplicá-las em suas próprias aplicações Java.

Vamos começar com uma lista de números que usaremos para ilustrar cada exemplo:

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```

### 1. **`forEach(Consumer<T> action)`**

A operação `forEach` executa uma ação em cada elemento do stream. Isso é útil para realizar uma ação em cada item sem alterá-los.

**Exemplo 1: Imprimindo números ao quadrado**

```java
numeros.stream()
       .forEach(numero -> System.out.println("Número ao quadrado: " + numero * numero));
```

Neste exemplo, estamos imprimindo o quadrado de cada número da lista.

**Exemplo 2: Multiplicando números por 2**

```java
numeros.stream()
       .forEach(numero -> System.out.println("Número multiplicado por 2: " + numero * 2));
```

Aqui, estamos imprimindo cada número multiplicado por 2.

### 2. **`count()`**

A operação `count` retorna o número de elementos no stream como um valor inteiro.

**Exemplo 1: Contando números pares**

```java
long quantidadePares = numeros.stream()
                              .filter(numero -> numero % 2 == 0)
                              .count();

System.out.println("Quantidade de números pares: " + quantidadePares);
```

Neste exemplo, estamos contando quantos números pares existem na lista.

**Exemplo 2: Contando números maiores que 5**

```java
long quantidadeMaioresQue5 = numeros.stream()
                                    .filter(numero -> numero > 5)
                                    .count();

System.out.println("Quantidade de números maiores que 5: " + quantidadeMaioresQue5);
```

Aqui, estamos contando quantos números são maiores que 5.

### 3. **`collect(Collector<T, A, R> collector)`**

A operação `collect` permite coletar os elementos do stream usando um coletor especificado para criar uma estrutura de dados, como uma lista, conjunto ou mapa.

**Exemplo 1: Coletando números pares em um conjunto**

```java
Set<Integer> numerosParesSet = numeros.stream()
                                      .filter(numero -> numero % 2 == 0)
                                      .collect(Collectors.toSet());

System.out.println("Números pares em um conjunto: " + numerosParesSet);
```

Neste exemplo, estamos coletando os números pares em um conjunto.

**Exemplo 2: Coletando o quadrado dos números em uma lista**

```java
List<Integer> quadrados = numeros.stream()
                                .map(numero -> numero * numero)
                                .collect(Collectors.toList());

System.out.println("Quadrados dos números em uma lista: " + quadrados);
```

Aqui, estamos coletando o quadrado de cada número em uma lista.

### 4. **`reduce(T identity, BinaryOperator<T> accumulator)`**

A operação `reduce` combina os elementos do stream usando um operador binário e um valor de identidade inicial.

**Exemplo 1: Somando todos os números**

```java
Optional<Integer> somaTotal = numeros.stream()
                                    .reduce(0, (acumulador, numero) -> acumulador + numero);

System.out.println("Soma de todos os números: " + somaTotal.orElse(0));
```

Neste exemplo, estamos somando todos os números da lista.

**Exemplo 2: Concatenando strings**

```java
List<String> palavras = Arrays.asList("Olá", "Mundo", "Stream");

Optional<String> frase = palavras.stream()
                                 .reduce((acumulador, palavra) -> acumulador + " " + palavra);

System.out.println("Frase concatenada: " + frase.orElse(""));
```

Aqui, estamos concatenando as strings para formar uma frase.

### 5. **`min(Comparator<T> comparator)`**

A operação `min` retorna o menor elemento do stream com base no comparador fornecido.

**Exemplo 1: Encontrando o menor número**

```java
Optional<Integer> menorNumero = numeros.stream()
                                      .min(Integer::compareTo);

System.out.println("Menor número: " + menorNumero.orElse(0));
```

Neste exemplo, estamos encontrando o menor número da lista.

**Exemplo 2: Encontrando a menor string em ordem lexicográfica**

```java
List<String> palavras = Arrays.asList("maçã", "banana", "uva");

Optional<String> menorPalavra = palavras.stream()
                                       .min(String::compareTo);

System.out.println("Menor palavra: " + menorPalavra.orElse(""));
```

Aqui, estamos encontrando a menor palavra em ordem lexicográfica.

### 6. **`max(Comparator<T> comparator)`**

A operação `max` retorna o maior elemento do stream com base no comparador fornecido.

**Exemplo 1: Encontrando o maior número**

```java
Optional<Integer> maiorNumero = numeros.stream()
                                      .max(Integer::compareTo);

System.out.println("Maior número: " + maiorNumero.orElse(0));
```

Neste exemplo, estamos encontrando o maior número da lista.

**Exemplo 2: Encontrando a maior string em ordem lexicográfica**

```java
List<String> palavras = Arrays.asList("maçã", "banana", "uva");

Optional<String> maiorPalavra = palavras.stream()
                                       .max(String::compareTo);

System.out.println("Maior palavra: " + maiorPalavra.orElse(""));
```

Aqui, estamos encontrando a maior palavra em ordem lexicográfica.

### 7. **`anyMatch(Predicate<T> predicate)`**

A operação `anyMatch` verifica se pelo menos um elemento do stream atende à condição especificada.

**Exemplo 1: Verificando se há números pares**

```java
boolean temNumeroPar = numeros.stream()
                              .anyMatch(numero -> numero % 2 == 0);

System.out.println("Tem número par? " + temNumeroPar);
```

Neste exemplo, estamos verificando se há pelo menos um número par na lista.

**Exemplo 2: Verificando se há números negativos**

```java
boolean temNumeroNegativo = numeros.stream()
                                  .anyMatch(numero -> numero < 0);

System.out.println("Tem número negativo? " + temNumeroNegativo);
```

Aqui, estamos verificando se há pelo menos

 um número negativo na lista.

### 8. **`allMatch(Predicate<T> predicate)`**

A operação `allMatch` verifica se todos os elementos do stream atendem à condição especificada.

**Exemplo 1: Verificando se todos os números são positivos**

```java
boolean saoTodosPositivos = numeros.stream()
                                  .allMatch(numero -> numero > 0);

System.out.println("São todos positivos? " + saoTodosPositivos);
```

Neste exemplo, estamos verificando se todos os números da lista são positivos.

**Exemplo 2: Verificando se todas as palavras têm mais de 3 letras**

```java
List<String> palavras = Arrays.asList("casa", "carro", "sol");

boolean todasComMaisDe3Letras = palavras.stream()
                                       .allMatch(palavra -> palavra.length() > 3);

System.out.println("Todas as palavras têm mais de 3 letras? " + todasComMaisDe3Letras);
```

Aqui, estamos verificando se todas as palavras da lista têm mais de 3 letras.

### 9. **`noneMatch(Predicate<T> predicate)`**

A operação `noneMatch` verifica se nenhum elemento do stream atende à condição especificada.

**Exemplo 1: Verificando se não há números negativos**

```java
boolean naoTemNegativos = numeros.stream()
                                .noneMatch(numero -> numero < 0);

System.out.println("Não tem números negativos? " + naoTemNegativos);
```

Neste exemplo, estamos verificando se não há números negativos na lista.

**Exemplo 2: Verificando se não há palavras vazias**

```java
List<String> palavras = Arrays.asList("casa", "carro", "sol");

boolean naoTemVazias = palavras.stream()
                             .noneMatch(palavra -> palavra.isEmpty());

System.out.println("Não tem palavras vazias? " + naoTemVazias);
```

Aqui, estamos verificando se não há palavras vazias na lista.

### 10. **`findFirst()`**

A operação `findFirst` retorna o primeiro elemento do stream.

**Exemplo 1: Encontrando o primeiro número par**

```java
Optional<Integer> primeiroPar = numeros.stream()
                                       .filter(numero -> numero % 2 == 0)
                                       .findFirst();

System.out.println("Primeiro número par: " + primeiroPar.orElse(0));
```

Neste exemplo, estamos encontrando o primeiro número par da lista.

**Exemplo 2: Encontrando o primeiro número maior que 5**

```java
Optional<Integer> primeiroMaiorQue5 = numeros.stream()
                                             .filter(numero -> numero > 5)
                                             .findFirst();

System.out.println("Primeiro número maior que 5: " + primeiroMaiorQue5.orElse(0));
```

Aqui, estamos encontrando o primeiro número maior que 5.

### 11. **`findAny()`**

A operação `findAny` retorna qualquer elemento do stream.

**Exemplo 1: Encontrando qualquer número par**

```java
Optional<Integer> qualquerPar = numeros.stream()
                                      .filter(numero -> numero % 2 == 0)
                                      .findAny();

System.out.println("Qualquer número par: " + qualquerPar.orElse(0));
```

Neste exemplo, estamos encontrando qualquer número par da lista.

**Exemplo 2: Encontrando qualquer número menor que 3**

```java
Optional<Integer> qualquerMenorQue3 = numeros.stream()
                                            .filter(numero -> numero < 3)
                                            .findAny();

System.out.println("Qualquer número menor que 3: " + qualquerMenorQue3.orElse(0));
```

Aqui, estamos encontrando qualquer número menor que 3.

### 12. **`toArray()`**

A operação `toArray` converte os elementos do stream em um array.

**Exemplo 1: Convertendo números para um array**

```java
Integer[] arrayNumeros = numeros.stream()
                                .toArray(Integer[]::new);

System.out.println("Array de números: " + Arrays.toString(arrayNumeros));
```

Neste exemplo, estamos convertendo os números do stream em um array.

**Exemplo 2: Convertendo palavras para um array de strings**

```java
List<String> palavras = Arrays.asList("casa", "carro", "sol");

String[] arrayPalavras = palavras.stream()
                                .toArray(String[]::new);

System.out.println("Array de palavras: " + Arrays.toString(arrayPalavras));
```

Aqui, estamos convertendo as palavras do stream em um array de strings.

### 13. **`iterator()`**

A operação `iterator` retorna um iterador para percorrer os elementos do stream.

**Exemplo 1: Usando um iterador para percorrer e imprimir números**

```java
Iterator<Integer> iterador = numeros.stream()
                                   .iterator();

while (iterador.hasNext()) {
    System.out.println(iterador.next());
}
```

Neste exemplo, estamos usando um iterador para percorrer e imprimir os números do stream.

**Exemplo 2: Usando um iterador para verificar se há números pares**

```java
Iterator<Integer> iterador = numeros.stream()
                                   .iterator();

boolean temNumeroPar = false;
while (iterador.hasNext()) {
    int numero = iterador.next();
    if (numero % 2 == 0) {
        temNumeroPar = true;
        break;
    }
}

System.out.println("Tem número par? " + temNumeroPar);
```

Aqui, estamos usando um iterador para verificar se há números pares no stream.

---

Esses exemplos abrangentes demonstram o uso prático de cada operação terminal da API `java.util.stream`. Ao dominar essas operações, você será capaz de manipular e processar coleções de dados de forma eficiente e expressiva em suas aplicações Java. Utilize esses exemplos como referência e comece a aproveitar ao máximo o poder das streams em sua programação!

