# Explicação e exemplo de implementação.
Aplique o padrão de projeto decorator para criar um sanduíche de frango assado com pepperoni e queijo mussarela
ralado. O projeto deve seguir os seguintes critérios:

* Deve imprimir no console: Sanduíche de Carne, Bacon, QueijoMussarelaRalado custa $7,49.
* O sanduíche de frango assado custa $4,50. - o ingrediente adicional pepperoni custa $0,99.
* O ingrediente adicional queijo mussarela ralado custa $2,00.

crie as classes necessárias: FrangoAssado, Pepperoni e QueijoMussarelaRalado.


```tsx
// Interface para o sanduíche
class Sanduiche {
    descricao() {
      return "";
    }
  
    preco() {
      return 0.0;
    }
  }
  
  // Implementação do sanduíche de frango assado
  class FrangoAssado extends Sanduiche {
    descricao() {
      return "Sanduíche de Frango Assado";
    }
  
    preco() {
      return 4.5;
    }
  }
  
  // Decorator para o pepperoni
  class Pepperoni extends Sanduiche {
    constructor(sanduiche) {
      super();
      this.sanduiche = sanduiche;
    }
  
    descricao() {
      return this.sanduiche.descricao() + ", Pepperoni";
    }
  
    preco() {
      return this.sanduiche.preco() + 0.99;
    }
  }
  
  // Decorator para o queijo mussarela ralado
  class QueijoMussarelaRalado extends Sanduiche {
    constructor(sanduiche) {
      super();
      this.sanduiche = sanduiche;
    }
  
    descricao() {
      return this.sanduiche.descricao() + ", Queijo Mussarela Ralado";
    }
  
    preco() {
      return this.sanduiche.preco() + 2.0;
    }
  }
  
  // Criando o sanduíche de frango assado com os decoradores
  let sanduiche = new FrangoAssado();
  sanduiche = new Pepperoni(sanduiche);
  sanduiche = new QueijoMussarelaRalado(sanduiche);
  
  // Obtendo a descrição e o preço final do sanduíche
  console.log(`${sanduiche.descricao()} custa $${sanduiche.preco().toFixed(2)}.`);
```
