
## **Acesso Indevido aos Atributos**

Suponha que temos uma classe `Pessoa` sem encapsulamento adequado:

```java
public class Pessoa {
    public String nome;
    public int idade;
}
```

Aqui, os atributos `nome` e `idade` são públicos, o que permite acesso direto a eles sem controle. Isso pode levar a alterações indevidas:

```java
Pessoa pessoa = new Pessoa();
pessoa.nome = "Alice";  // Acesso direto ao atributo sem validação
pessoa.idade = -30;    // Acesso direto ao atributo sem validação

System.out.println(pessoa.nome);  // Saída: Alice
System.out.println(pessoa.idade); // Saída: -30
```

## **Duplicação de Validações**

Sem encapsulamento, validações podem ser repetidas em várias partes do código, levando a duplicação e dificuldade de manutenção. Por exemplo, considere uma classe `ContaBancaria` sem encapsulamento:

```java
public class ContaBancaria {
    public String titular;
    public double saldo;
}
```

A validação de depósito positivo pode ser feita em diferentes lugares:

```java
// Em um lugar do código
if (valorDeposito > 0) {
    conta.saldo += valorDeposito;
}

// Em outro lugar do código
if (novoSaldo > conta.saldo) {
    conta.saldo = novoSaldo;
}
```

## **Fragilidade na Evolução do Código**

Quando os atributos não são encapsulados, mudanças internas na implementação podem afetar o código externo. Suponha que tenhamos uma classe `Carro` sem encapsulamento:

```java
public class Carro {
    public String marca;
    public String modelo;
}
```

Se decidirmos alterar o atributo `marca` para `fabricante`, isso afetará o código em várias partes:

```java
// Antes da mudança
carro.marca = "Toyota";

// Após a mudança
carro.fabricante = "Toyota"; // Agora requer alteração no código externo
```

## **Dificuldade de Evolução e Manutenção**

Sem encapsulamento, a adição de novas funcionalidades pode exigir modificações em várias partes do código. Suponha que tenhamos uma classe `Produto` sem encapsulamento:

```java
public class Produto {
    public String nome;
    public double preco;
}
```

Se quisermos adicionar uma validação de preço mínimo, precisamos atualizar o código em vários lugares:

```java
// Antes da mudança
produto.preco = 50.0;

// Após a mudança
if (novoPreco >= 0) {
    produto.preco = novoPreco;
}
```

## **Conclusão**

Os exemplos acima demonstram problemas que podem surgir quando os atributos não são encapsulados de forma adequada. A falta de encapsulamento pode resultar em acesso indevido, duplicação de validações, fragilidade no código e dificuldade de evolução e manutenção. O encapsulamento, por outro lado, oferece uma abordagem mais segura e organizada para lidar com os atributos e suas operações. Ao aplicar o encapsulamento corretamente, você estará criando um código mais robusto, modular e fácil de manter, além de evitar armadilhas comuns que podem surgir devido à falta de encapsulamento.

