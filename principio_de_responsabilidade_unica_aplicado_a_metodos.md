Pensar no Princípio de Responsabilidade Única (SRP) a nível de criação de métodos envolve garantir que cada método tenha uma única responsabilidade bem definida. Assim como o SRP se aplica a classes, ele também se aplica a métodos, buscando manter cada método coeso, legível e fácil de manter. Vamos explorar como podemos aplicar o SRP a nível de criação de métodos:

## **Identificando Responsabilidades dos Métodos**

Para garantir que um método respeite o SRP, é importante identificar claramente qual é a sua responsabilidade principal. Isso envolve responder à pergunta: "O que esse método está fazendo?". Se a resposta a essa pergunta abranger várias funcionalidades distintas, é um sinal de que o método está violando o SRP.

## **Sintomas de Métodos com Múltiplas Responsabilidades**

Aqui estão alguns sintomas que podem indicar que um método não está respeitando o SRP:

1. **Método Longo:** Se um método é muito longo e executa muitas tarefas diferentes, ele provavelmente está acumulando múltiplas responsabilidades.

2. **Comentários Excessivos:** Se você precisa adicionar muitos comentários para explicar o que o método faz, isso pode ser um sinal de que ele está fazendo coisas demais.

3. **Dificuldade de Nomear:** Se é difícil escolher um nome claro e conciso para o método, isso pode indicar que ele está tentando fazer muitas coisas ao mesmo tempo.

## **Dividindo Métodos com Base no SRP**

Para aplicar o SRP a nível de criação de métodos, considere as seguintes estratégias:

1. **Criação de Métodos Auxiliares:** Se um método está realizando várias ações, divida-o em métodos auxiliares, cada um responsável por uma ação específica. Isso ajuda a manter cada método coeso e fácil de entender.

2. **Extração de Funcionalidades:** Se parte do código dentro de um método pode ser reutilizado em outras partes do código, considere extrair essa parte em um método separado e reutilizável.

3. **Aplicação do Conceito de "Método Fazer uma Coisa":** Um método deve fazer uma coisa e fazê-la bem. Evite que métodos realizem tarefas diferentes e desconexas.

## **Exemplo de Aplicação do SRP a Nível de Métodos**

Suponha que você tenha um método que calcula o salário de um funcionário e envia um e-mail de notificação. Isso viola o SRP, já que envolver o cálculo de salário e o envio de e-mail são responsabilidades distintas. Vejamos como poderíamos dividir essas responsabilidades:

```java
public class Funcionario {
    public double calcularSalario() {
        // Lógica para calcular o salário
    }
}

public class NotificadorEmail {
    public void enviarEmail(String destinatario, String mensagem) {
        // Lógica para enviar e-mails
    }
}

// Antes da divisão das responsabilidades
public void calcularSalarioEEnviarEmail(Funcionario funcionario, String destinatario) {
    double salario = funcionario.calcularSalario();
    String mensagem = "Seu salário é: " + salario;
    notificadorEmail.enviarEmail(destinatario, mensagem);
}

// Após a divisão das responsabilidades
public void calcularSalario(Funcionario funcionario) {
    double salario = funcionario.calcularSalario();
}

public void enviarEmailDeSalario(String destinatario, double salario) {
    String mensagem = "Seu salário é: " + salario;
    notificadorEmail.enviarEmail(destinatario, mensagem);
}
```

No exemplo acima, dividimos as responsabilidades do método original em dois métodos separados: um para calcular o salário e outro para enviar o e-mail de notificação. Isso torna o código mais coeso e mais aderente ao SRP.

## **Conclusão**

O Princípio de Responsabilidade Única não se aplica apenas a classes, mas também a métodos. Ao criar métodos, é fundamental garantir que cada método tenha uma única responsabilidade bem definida. Isso ajuda a melhorar a legibilidade, a reutilização e a manutenibilidade do código. Identificar responsabilidades claras, evitar métodos longos e dividir funcionalidades em métodos auxiliares são práticas que ajudam a aplicar o SRP com sucesso a nível de métodos. Respeitar o SRP aprimora a qualidade do código, tornando-o mais claro, modular e eficiente.

