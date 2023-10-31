# Explicação e exemplo de implementação.

Neste exemplo, temos uma interface Computer que define os atributos comuns para todos os tipos de computadores, como RAM, HDD, CPU e tipo. Existem duas classes concretas, PC e Server, que implementam essa interface e fornecem valores padrão para os atributos. As fábricas PCFactory e ServerFactory são responsáveis por criar instâncias dos computadores do tipo correspondente. O método toString está implementado em ambas as classes para imprimir os atributos do computador quando chamado.

```tsx
// Interface comum para produtos (Computadores)
interface Computer {
  ram: number; // em Gigabytes
  hdd: number; // em Gigabytes
  cpu: number; // em GHz
  type: string;
  toString(): string;
}

// Classe base abstrata para a fábrica
abstract class ComputerFactory {
  abstract createComputer(): Computer;
}

// Classe para criar computadores do tipo PC
class PCFactory extends ComputerFactory {
  createComputer(): Computer {
    return new PC();
  }
}

// Classe para criar computadores do tipo Server
class ServerFactory extends ComputerFactory {
  createComputer(): Computer {
    return new Server();
  }
}

// Classe concreta para computadores do tipo PC
class PC implements Computer {
  ram: number;
  hdd: number;
  cpu: number;
  type: string;

  constructor() {
    this.ram = 8; // 8 GB por padrão
    this.hdd = 500; // 500 GB por padrão
    this.cpu = 2.4; // 2.4 GHz por padrão
    this.type = "PC";
  }

  toString(): string {
    return `PC - RAM: ${this.ram}GB, HDD: ${this.hdd}GB, CPU: ${this.cpu}GHz`;
  }
}

// Classe concreta para computadores do tipo Server
class Server implements Computer {
  ram: number;
  hdd: number;
  cpu: number;
  type: string;

  constructor() {
    this.ram = 32; // 32 GB por padrão
    this.hdd = 1000; // 1 TB por padrão
    this.cpu = 3.0; // 3.0 GHz por padrão
    this.type = "Server";
  }

  toString(): string {
    return `Server - RAM: ${this.ram}GB, HDD: ${this.hdd}GB, CPU: ${this.cpu}GHz`;
  }
}

// Uso das fábricas para criar computadores
const pcFactory = new PCFactory();
const serverFactory = new ServerFactory();

const pc = pcFactory.createComputer();
const server = serverFactory.createComputer();

console.log(pc.toString());
console.log(server.toString());
```
