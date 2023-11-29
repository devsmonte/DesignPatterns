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
