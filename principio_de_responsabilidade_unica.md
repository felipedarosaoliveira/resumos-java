
**Princípio de Responsabilidade Única na POO: Garantindo a Coesão e Manutenibilidade do Código**

A Programação Orientada a Objetos (POO) trouxe consigo diversos princípios que auxiliam na criação de software de qualidade. Entre esses princípios, destaca-se o Princípio de Responsabilidade Única (SRP, do inglês Single Responsibility Principle). Neste artigo, exploraremos o SRP em profundidade, discutindo sua definição, importância e fornecendo exemplos práticos que ilustram situações onde o princípio não é respeitado e como refatorar o código para garantir uma aplicação eficaz do SRP.

## **O que é o Princípio de Responsabilidade Única?**

O Princípio de Responsabilidade Única é um dos cinco princípios do SOLID, um conjunto de diretrizes para escrever software mais legível, reutilizável e de fácil manutenção. O SRP afirma que uma classe deve ter apenas uma única razão para mudar, ou seja, ela deve ter apenas uma responsabilidade bem definida. Isso implica que uma classe deve encapsular apenas um conjunto coeso de funcionalidades.

## **Importância do SRP**

Respeitar o SRP é crucial para a manutenibilidade e escalabilidade do código. Quando uma classe possui múltiplas responsabilidades, qualquer mudança em uma das funcionalidades pode afetar inesperadamente outras partes do sistema, tornando o código frágil e difícil de manter. Ao aderir ao SRP, os benefícios incluem:

- **Facilitação da Manutenção:** Classes bem definidas e coesas tornam a manutenção mais fácil, uma vez que cada classe lida com uma única responsabilidade.

- **Reutilização de Código:** Classes com responsabilidades únicas podem ser reutilizadas em diferentes partes do sistema, aumentando a eficiência do desenvolvimento.

- **Maior Flexibilidade:** Mudanças em uma responsabilidade não afetarão outras partes do sistema, permitindo que você adapte o código sem impactos colaterais indesejados.

- **Legibilidade Aprimorada:** Código mais focado e coeso é mais legível, facilitando a compreensão tanto para o desenvolvedor quanto para outros membros da equipe.

## **Exemplos de Não Cumprimento do SRP**

Para entender o SRP, consideremos exemplos de situações onde o princípio não é respeitado:

**Exemplo 1: Classe "Pedido"**

```java
public class Pedido {
    public void calcularTotal() {
        // Lógica para calcular o total do pedido
    }
    
    public void salvarPedido() {
        // Lógica para salvar o pedido no banco de dados
    }
}
```

Neste exemplo, a classe `Pedido` possui duas responsabilidades: calcular o total do pedido e salvar o pedido no banco de dados. Isso torna a classe menos coesa e pode causar problemas quando as funcionalidades precisarem ser alteradas.

**Exemplo 2: Classe "Funcionario"**

```java
public class Funcionario {
    public void calcularSalario() {
        // Lógica para calcular o salário do funcionário
    }
    
    public void enviarEmail() {
        // Lógica para enviar e-mails aos funcionários
    }
}
```

Aqui, a classe `Funcionario` combina a responsabilidade de calcular o salário com a responsabilidade de enviar e-mails. Isso pode levar a problemas se as regras de cálculo ou o processo de envio de e-mails mudarem.

## **Refatorando para Respeitar o SRP**

Para cumprir o SRP, é necessário dividir essas responsabilidades em classes separadas:

**Exemplo 1: Classes Separadas para "Pedido"**

```java
public class Pedido {
    public void calcularTotal() {
        // Lógica para calcular o total do pedido
    }
}

public class RepositorioPedido {
    public void salvarPedido(Pedido pedido) {
        // Lógica para salvar o pedido no banco de dados
    }
}
```

Aqui, temos a classe `Pedido` com a responsabilidade de calcular o total, e a classe `RepositorioPedido` com a responsabilidade de salvar o pedido. Isso torna o código mais coeso e separa as preocupações.

**Exemplo 2: Classes Separadas para "Funcionario"**

```java
public class Funcionario {
    public void calcularSalario() {
        // Lógica para calcular o salário do funcionário
    }
}

public class NotificadorEmail {
    public void enviarEmail(Funcionario funcionario) {
        // Lógica para enviar e-mails aos funcionários
    }
}
```

Neste caso, a classe `Funcionario` lida apenas com o cálculo de salários, enquanto a classe `NotificadorEmail` trata do envio de e-mails. Essa separação de responsabilidades melhora a modularidade do código.

## **Conclusão**

O Princípio de Responsabilidade Única (SRP) é fundamental para a criação de código coeso, reutilizável e de fácil manutenção. Ao definir uma única responsabilidade para cada classe e método, você cria componentes mais focados e resilientes. Os exemplos apresentados ilustram a diferença entre não cumprir e cumprir o SRP, destacando a importância de refatorar para separar responsabilidades. Respeitar o SRP contribui para a qualidade do software, tornando-o mais adaptável a mudanças e mais compreensível para você e sua equipe de desenvolvimento.

