# Explicação e exemplo de implementação.

Neste exemplo, temos uma classe abstrata Veiculo com um construtor e os métodos clone e represent. Em seguida, criamos duas subclasses, Carro e Moto, que estendem a classe Veiculo e implementam os métodos abstratos.

A classe Aplicacao contém métodos para criar veículos, clonar veículos e imprimir a representação dos veículos. A criação dos veículos é feita no método criarVeiculos, onde são criados dois carros e duas motos. O método clonarVeiculos clona os veículos usando o método clone, e o método imprimirRepresentacao imprime a representação de cada veículo clonado.

```tsx
abstract class Veiculo {
  constructor(
    public modelo: string,
    public marca: string,
    public cor: string,
    public numeroRodas: number
  ) {}

  abstract clone(): Veiculo;
  abstract represent(): void;
}

class Carro extends Veiculo {
  constructor(
    modelo: string,
    marca: string,
    cor: string,
    numeroRodas: number,
    public numeroPortas: number
  ) {
    super(modelo, marca, cor, numeroRodas);
  }

  clone(): Veiculo {
    return new Carro(this.modelo, this.marca, this.cor, this.numeroRodas, this.numeroPortas);
  }

  represent(): void {
    console.log(`Carro ${this.marca} ${this.modelo}, cor ${this.cor}, ${this.numeroRodas} rodas, ${this.numeroPortas} portas`);
  }
}

class Moto extends Veiculo {
  constructor(
    modelo: string,
    marca: string,
    cor: string,
    numeroRodas: number,
    public cilindradas: number
  ) {
    super(modelo, marca, cor, numeroRodas);
  }

  clone(): Veiculo {
    return new Moto(this.modelo, this.marca, this.cor, this.numeroRodas, this.cilindradas);
  }

  represent(): void {
    console.log(`Moto ${this.marca} ${this.modelo}, cor ${this.cor}, ${this.numeroRodas} rodas, ${this.cilindradas} cilindradas`);
  }
}

class Aplicacao {
  static criarVeiculos(): Veiculo[] {
    const veiculos: Veiculo[] = [];

    const carro1 = new Carro("Sedan", "Toyota", "Azul", 4, 4);
    const carro2 = new Carro("SUV", "Honda", "Vermelho", 4, 5);
    const moto1 = new Moto("CBR600", "Honda", "Preto", 2, 600);
    const moto2 = new Moto("Ninja 300", "Kawasaki", "Verde", 2, 300);

    veiculos.push(carro1, carro2, moto1, moto2);

    return veiculos;
  }

  static clonarVeiculos(veiculos: Veiculo[]): Veiculo[] {
    const clones: Veiculo[] = [];
    for (const veiculo of veiculos) {
      clones.push(veiculo.clone());
    }
    return clones;
  }

  static imprimirRepresentacao(veiculos: Veiculo[]): void {
    for (const veiculo of veiculos) {
      veiculo.represent();
    }
  }
}

const veiculos = Aplicacao.criarVeiculos();
const clones = Aplicacao.clonarVeiculos(veiculos);
Aplicacao.imprimirRepresentacao(clones);
```
