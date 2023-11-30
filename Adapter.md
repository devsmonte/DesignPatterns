# Explicação e exemplo de implementação.
Aplique o padrão de projeto adapter para criar um adaptador que permita que um objeto do tipo Pato seja usado como se fosse um objeto do tipo
Galinha. Use as classes AdaptadorPato e AdaptadorPatoDemo para demonstrar o uso da classe AdaptadorPato.


```tsx
// Interface Galinha
class Galinha {
  cacarejar() {
    return "Cocoricó!";
  }

  bicar() {
    return "Bicando milho.";
  }
}

// Implementação do Pato
class Pato {
  grasnar() {
    return "Quack!";
  }

  voar() {
    return "Voando alto.";
  }
}

// Adapter para adaptar um Pato para se comportar como Galinha
class AdaptadorPato extends Galinha {
  constructor(pato) {
    super();
    this.pato = pato;
  }

  cacarejar() {
    return this.pato.grasnar(); // Adaptando o grasnar do Pato para o cacarejar da Galinha
  }

  bicar() {
    return "Bicando ração."; // Comportamento de bicar diferente da Galinha, apenas para exemplo
  }
}

// Demo para demonstrar o uso da classe AdaptadorPato
class AdaptadorPatoDemo {
  static executar() {
    const pato = new Pato();
    const adaptador = new AdaptadorPato(pato);

    console.log("Comportamento do Pato:");
    console.log(`Grasnando: ${pato.grasnar()}`);
    console.log(`Voando: ${pato.voar()}`);

    console.log("\nUsando o AdaptadorPato como se fosse uma Galinha:");
    console.log(`Cacarejando: ${adaptador.cacarejar()}`);
    console.log(`Bicando: ${adaptador.bicar()}`);
  }
}

// Executando a demonstração
AdaptadorPatoDemo.executar();
```
