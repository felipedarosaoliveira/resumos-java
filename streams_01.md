**Tutorial sobre a API `java.util.stream` em Java**

A API `java.util.stream` é uma poderosa ferramenta oferecida pelo Java para lidar com coleções de dados de forma eficiente e expressiva. Ela introduz o conceito de processamento de streams, que permite realizar operações em sequências de elementos de maneira declarativa. Neste tutorial, vamos explorar a fundo tanto as operações intermediárias quanto as operações terminais da API `java.util.stream`, bem como entender os conceitos fundamentais por trás dela. Vamos mergulhar em exemplos práticos para cada operação, para que você possa começar a aproveitar ao máximo essa ferramenta essencial em sua programação Java.

### **Fundamentos da API `java.util.stream`**

Antes de mergulharmos nas operações intermediárias e terminais, é importante entender os conceitos fundamentais da API `java.util.stream`.

A API `Stream` em Java oferece uma abstração para processar sequências de elementos de forma declarativa. Ela permite que você execute operações em elementos de uma coleção (ou outros tipos de fontes de dados) de maneira eficiente e paralela.

#### Características principais da API `Stream`:

- **Pipeline de Processamento:** As operações de stream são organizadas em pipelines, que consistem em operações intermediárias (que transformam o stream) e uma operação terminal (que produz um resultado).

- **Operações Intermediárias:** Essas operações permitem transformações e filtragens nos elementos do stream. Elas são preguiçosas, o que significa que não são executadas até que uma operação terminal seja chamada.

- **Operações Terminais:** As operações terminais encerram o pipeline de processamento e produzem um resultado. Elas são ação final que executa o pipeline completo.

- **Não Destrutivas:** As operações de stream não alteram os dados originais, elas criam novos streams com as transformações aplicadas.

- **Processamento Paralelo:** A API permite que operações sejam executadas em paralelo, aproveitando melhor o poder de processamento multi-core.

### **Operações Intermediárias da API `java.util.stream`**

As operações intermediárias transformam ou filtram os elementos do stream. Elas são preguiçosas, o que significa que não são executadas até que uma operação terminal seja chamada. Vamos explorar algumas das operações intermediárias mais comuns:

1. **`filter(Predicate<T> predicate)`**: Filtra os elementos do stream com base em um predicado.

   **Exemplo: Filtrando Números Pares**

   ```java
   List<Integer> numerosPares = numeros.stream()
                                       .filter(numero -> numero % 2 == 0)
                                       .collect(Collectors.toList());
   ```

2. **`map(Function<T, R> mapper)`**: Transforma cada elemento do stream aplicando uma função.

   **Exemplo: Dobrando os Números**

   ```java
   List<Integer> numerosDobrados = numeros.stream()
                                          .map(numero -> numero * 2)
                                          .collect(Collectors.toList());
   ```

3. **`flatMap(Function<T, Stream<R>> mapper)`**: Transforma e achatada os elementos de um stream de stream em um único stream.

   **Exemplo: Obtendo Palavras Únicas de uma Lista de Frases**

   ```java
   List<String> palavrasUnicas = frases.stream()
                                       .flatMap(frase -> Arrays.stream(frase.split(" ")))
                                       .distinct()
                                       .collect(Collectors.toList());
   ```

4. **`distinct()`**: Remove elementos duplicados do stream.

   **Exemplo: Removendo Números Duplicados**

   ```java
   List<Integer> numerosUnicos = numeros.stream()
                                        .distinct()
                                        .collect(Collectors.toList());
   ```

5. **`sorted(Comparator<T> comparator)`**: Ordena os elementos do stream com base em um comparador.

   **Exemplo: Ordenando Números em Ordem Crescente**

   ```java
   List<Integer> numerosOrdenados = numeros.stream()
                                          .sorted()
                                          .collect(Collectors.toList());
   ```

6. **`peek(Consumer<T> action)`**: Permite realizar uma ação em cada elemento do stream sem alterá-los.

   **Exemplo: Imprimindo Números Multiplicados por 10**

   ```java
   numeros.stream()
          .peek(numero -> System.out.println(numero * 10))
          .collect(Collectors.toList());
   ```

### **Operações Terminais da API `java.util.stream`**

As operações terminais encerram o pipeline de processamento e produzem um resultado. Vamos explorar algumas das operações terminais mais utilizadas:

1. **`forEach(Consumer<T> action)`**: Executa uma ação em cada elemento do stream.

   **Exemplo: Imprimindo Números ao Quadrado**

   ```java
   numeros.stream()
          .forEach(numero -> System.out.println(numero * numero));
   ```

2. **`count()`**: Conta o número de elementos no stream.

   **Exemplo: Contando Números Pares**

   ```java
   long quantidadePares = numeros.stream()
                                 .filter(numero -> numero % 2 == 0)
                                 .count();
   ```

3. **`collect(Collector<T, A, R> collector)`**: Coleta os elementos do stream usando um coletor especificado.

   **Exemplo: Coletando Números Pares em um Conjunto**

   ```java
   Set<Integer> numerosParesSet = numeros.stream()
                                         .filter(numero -> numero % 2 == 0)
                                         .collect(Collectors.toSet());
   ```

4. **`reduce(T identity, BinaryOperator<T> accumulator)`**: Combina os elementos do stream usando um operador binário e um valor de identidade inicial.

   **Exemplo: Calculando a Soma de Todos os Números**

   ```java
   int somaTotal = numeros.stream()
                         .reduce(0, (acumulador, numero) -> acumulador + numero);
   ```

5. **`min(Comparator<T> comparator)`**: Retorna o menor elemento do stream com base no comparador.

   **Exemplo: Encontrando o Menor Número**

   ```java
   Optional<Integer> menorNumero = numeros.stream()
                                          .min(Integer::compareTo);
   ```

6. **`max(Comparator<T

> comparator)`**: Retorna o maior elemento do stream com base no comparador.

   **Exemplo: Encontrando o Maior Número**

   ```java
   Optional<Integer> maiorNumero = numeros.stream()
                                          .max(Integer::compareTo);
   ```

7. **`anyMatch(Predicate<T> predicate)`**: Verifica se pelo menos um elemento do stream atende à condição especificada.

   **Exemplo: Verificando se Há Números Pares**

   ```java
   boolean temPar = numeros.stream()
                           .anyMatch(numero -> numero % 2 == 0);
   ```

8. **`allMatch(Predicate<T> predicate)`**: Verifica se todos os elementos do stream atendem à condição especificada.

   **Exemplo: Verificando se Todos os Números São Positivos**

   ```java
   boolean saoTodosPositivos = numeros.stream()
                                      .allMatch(numero -> numero > 0);
   ```

9. **`noneMatch(Predicate<T> predicate)`**: Verifica se nenhum elemento do stream atende à condição especificada.

   **Exemplo: Verificando se Não Há Números Negativos**

   ```java
   boolean naoTemNegativos = numeros.stream()
                                    .noneMatch(numero -> numero < 0);
   ```

10. **`findFirst()`**: Retorna o primeiro elemento do stream.

    **Exemplo: Encontrando o Primeiro Número Par**

    ```java
    Optional<Integer> primeiroPar = numeros.stream()
                                           .filter(numero -> numero % 2 == 0)
                                           .findFirst();
    ```

11. **`findAny()`**: Retorna qualquer elemento do stream.

    **Exemplo: Encontrando Qualquer Número Menor que 5**

    ```java
    Optional<Integer> qualquerMenorQue5 = numeros.stream()
                                                 .filter(numero -> numero < 5)
                                                 .findAny();
    ```

12. **`toArray()`**: Converte os elementos do stream em um array.

    **Exemplo: Convertendo Números para um Array**

    ```java
    Integer[] arrayNumeros = numeros.stream()
                                    .toArray(Integer[]::new);
    ```

13. **`iterator()`**: Retorna um iterador para percorrer os elementos do stream.

    **Exemplo: Usando um Iterador para Verificar Números Pares**

    ```java
    Iterator<Integer> iterador = numeros.stream()
                                       .iterator();

    boolean temPar = false;
    while (iterador.hasNext()) {
        int numero = iterador.next();
        if (numero % 2 == 0) {
            temPar = true;
            break;
        }
    }
    ```
