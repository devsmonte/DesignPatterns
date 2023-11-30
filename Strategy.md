# Explicação e exemplo de implementação.
aplique o padrão de projeto Strategy para criar uma simples calculadora. Os requisitos para avaliar o projeto são:

- implementar uma interface Strategy com o método abstrato execute(). Deve haver três classes concretas que implementam a Strategy para realizar as operações de Soma, Subtração e Multiplicação de números inteiros;

- o método execute() deve receber dois números inteiros como parâmetros e retornar o resultado também como número inteiro;

- como input do usuário, a aplicação deve receber o primeiro valor, depois o segundo e, por último, a operação matemática que deve realizar;

- no final, a aplicação deve definir qual Strategy será usada, com base na operação informada, e imprimir o resultado da operação.



```tsx
// Interface Strategy
class Strategy {
  execute(num1, num2) {}
}

// Classe concreta para a operação de soma
class Soma extends Strategy {
  execute(num1, num2) {
    return num1 + num2;
  }
}

// Classe concreta para a operação de subtração
class Subtracao extends Strategy {
  execute(num1, num2) {
    return num1 - num2;
  }
}

// Classe concreta para a operação de multiplicação
class Multiplicacao extends Strategy {
  execute(num1, num2) {
    return num1 * num2;
  }
}

// Contexto da calculadora
class Calculadora {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  executarOperacao(num1, num2) {
    return this.strategy.execute(num1, num2);
  }
}

// Função para receber entrada do usuário
function getUserInput(promptMessage) {
  return parseInt(prompt(promptMessage));
}

// Função principal
function main() {
  const num1 = getUserInput("Digite o primeiro número: ");
  const num2 = getUserInput("Digite o segundo número: ");
  const operacao = prompt("Digite a operação (+ para soma, - para subtração, * para multiplicação): ");

  let strategy;

  // Definindo a estratégia com base na operação informada
  switch (operacao) {
    case '+':
      strategy = new Soma();
      break;
    case '-':
      strategy = new Subtracao();
      break;
    case '*':
      strategy = new Multiplicacao();
      break;
    default:
      console.log("Operação inválida.");
      return;
  }

  const calculadora = new Calculadora(strategy);
  const resultado = calculadora.executarOperacao(num1, num2);

  console.log(`O resultado da operação é: ${resultado}`);
}

// Chamada da função principal para iniciar a aplicação
main();
```
