**Explorando as Operações Intermediárias da API `java.util.stream` em Java**

A API `java.util.stream` oferece uma série de operações intermediárias que permitem manipular, filtrar e transformar elementos de uma coleção de forma elegante e eficiente. Neste artigo, vamos explorar cada uma dessas operações intermediárias em detalhes, fornecendo exemplos práticos e explicativos para cada uma delas.

Antes de prosseguirmos, vamos considerar um exemplo básico: uma lista de produtos com nome e preço.

```java
class Produto {
    private String nome;
    private double preco;

    public Produto(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }

    public String getNome() {
        return nome;
    }

    public double getPreco() {
        return preco;
    }
}

List<Produto> produtos = Arrays.asList(
    new Produto("Celular", 800),
    new Produto("Notebook", 1500),
    new Produto("TV", 300),
    new Produto("Fones de Ouvido", 50)
);
```

Agora, vamos explorar cada operação intermediária:

### 1. `filter(Predicate<T> predicate)`

A operação `filter` permite filtrar elementos com base em uma condição definida pelo predicado. Somente os elementos que atendem à condição são incluídos no novo stream resultante.

```java
List<Produto> produtosCaros = produtos.stream()
                                      .filter(produto -> produto.getPreco() > 100)
                                      .collect(Collectors.toList());
```

Nesse exemplo, a lista `produtosCaros` conterá apenas os produtos com preço acima de 100.

### 2. `map(Function<T, R> mapper)`

A operação `map` transforma cada elemento do stream usando a função fornecida.

```java
List<String> nomesProdutos = produtos.stream()
                                     .map(produto -> produto.getNome())
                                     .collect(Collectors.toList());
```

A lista `nomesProdutos` conterá os nomes dos produtos.

### 3. `flatMap(Function<T, Stream<R>> mapper)`

A operação `flatMap` transforma e achatna os resultados de streams internos.

```java
List<List<Integer>> listasDeNumeros = Arrays.asList(
    Arrays.asList(1, 2, 3),
    Arrays.asList(4, 5, 6),
    Arrays.asList(7, 8, 9)
);

List<Integer> numeros = listasDeNumeros.stream()
                                       .flatMap(lista -> lista.stream())
                                       .collect(Collectors.toList());
```

Nesse exemplo, a lista `numeros` conterá todos os números das listas internas.

### 4. `distinct()`

A operação `distinct` remove elementos duplicados.

```java
List<Integer> numeros = Arrays.asList(1, 2, 2, 3, 3, 3, 4, 4, 5);

List<Integer> numerosUnicos = numeros.stream()
                                     .distinct()
                                     .collect(Collectors.toList());
```

A lista `numerosUnicos` conterá apenas os números únicos da lista original.

### 5. `sorted()`

A operação `sorted` ordena os elementos.

```java
List<Integer> numeros = Arrays.asList(5, 2, 8, 1, 4, 3);

List<Integer> numerosOrdenados = numeros.stream()
                                       .sorted()
                                       .collect(Collectors.toList());
```

A lista `numerosOrdenados` conterá os números em ordem crescente.

### 6. `peek(Consumer<T> action)`

A operação `peek` executa uma ação em cada elemento do stream.

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

List<Integer> numerosModificados = numeros.stream()
                                         .peek(numero -> System.out.println("Processando: " + numero))
                                         .collect(Collectors.toList());
```

Essa operação apenas imprime uma mensagem para cada número processado.

### 7. `limit(long maxSize)`

A operação `limit` limita o número de elementos no stream.

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

List<Integer> primeirosNumeros = numeros.stream()
                                        .limit(3)
                                        .collect(Collectors.toList());
```

A lista `primeirosNumeros` conterá apenas os primeiros três números.

### 8. `skip(long n)`

A operação `skip` pula os primeiros elementos.

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

List<Integer> numerosPulados = numeros.stream()
                                     .skip(2)
                                     .collect(Collectors.toList());
```

A lista `numerosPulados` conterá os números após pular os dois primeiros.

### 9. `takeWhile(Predicate<T> predicate)`

A operação `takeWhile` retorna elementos enquanto a condição for verdadeira.

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

List<Integer> numerosAteTres = numeros.stream()
                                     .takeWhile(numero -> numero <= 3)
                                     .collect(Collectors.toList());
```

A lista `numerosAteTres` conterá os números até que a condição seja falsa.

### 10. `dropWhile(Predicate<T> predicate)`

A operação `dropWhile` pula elementos enquanto a condição for verdadeira.

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

List<Integer> numerosAposTres = numeros.stream()
                                      .dropWhile(numero -> numero <= 3)
                                      .collect(Collectors.toList());
```

A lista `numerosAposTres` conterá os números após pular os números menores ou iguais a três.

### 11. `unordered()`

A operação `unordered` remove a ordem introduzida por operações anteriores.

```java
List<Integer> numeros = Arrays.asList(5, 2, 8, 1, 4, 3);

List<Integer> numerosDesordenados = numeros.stream()
                                          .sorted()
                                          .unordered()
                                          .collect(Collectors.toList());
```

A lista `numerosDesordenados` conterá os números em ordem, mas a operação `unordered` remove qualquer ordem anterior.

Em resumo, as operações intermediárias da API `java.util.stream` permitem uma manipulação flexível e precisa dos elementos do stream. Ao aplicar essas operações de acordo com a necessidade do seu projeto, você pode transformar e filtrar dados de maneira eficiente e elegante. Portanto, domine essas operações para tornar seu código mais conciso e eficaz no processamento de coleções.

