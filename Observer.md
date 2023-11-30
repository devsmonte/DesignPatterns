# Explicação e exemplo de implementação.
Aplique o padrão de projeto Observer para criar um simples editor de texto. 

- implementar uma subclasse da classe Editor chamada TextEditor;

- aplicar o método insertLine, que recebe os parâmetros lineNumber e text;

- inserir o texto na ordem correspondente a lineNumber e deslocar as linhas posteriores se necessário;
  
- aplicar o método removeLine, que recebe lineNumber como parâmetro, deleta o texto da linha correspondente e desloca as linhas posteriores se necessário;

-instanciar um TextEditor e disparar o evento “open”;

- receber as linhas de texto, que serão inseridas no objeto texteditor, do usuário até que ele envie o texto “EOF”, que não deve ser inserido no objeto textEditor,

- por fim, o texteditor deve disparar o evento “save” para que o conteúdo seja salvo no arquivo configurado e imprimir todo o conteúdo do arquivo na tela.


```tsx
// Classe Observer
class Observer {
  constructor() {
    this.observers = [];
  }

  subscribe(fn) {
    this.observers.push(fn);
  }

  unsubscribe(fnToRemove) {
    this.observers = this.observers.filter(fn => fn !== fnToRemove);
  }

  notify(data) {
    this.observers.forEach(fn => fn(data));
  }
}

// Classe Editor
class Editor {
  constructor() {
    this.content = [];
    this.events = new Observer();
  }

  insertLine(lineNumber, text) {
    this.content.splice(lineNumber - 1, 0, text);
    this.events.notify({ action: 'insertLine', content: this.content });
  }

  removeLine(lineNumber) {
    this.content.splice(lineNumber - 1, 1);
    this.events.notify({ action: 'removeLine', content: this.content });
  }

  open() {
    this.events.notify({ action: 'open', content: this.content });
  }

  save() {
    this.events.notify({ action: 'save', content: this.content });
  }
}

// Subclasse TextEditor
class TextEditor extends Editor {
  constructor() {
    super();
    this.events.subscribe(this.logContent.bind(this));
  }

  logContent(data) {
    if (data.action === 'open' || data.action === 'save') {
      console.log("Conteúdo do arquivo:");
      console.log(data.content.join('\n'));
    }
  }
}

// Função para receber entrada do usuário
function getUserInput(promptMessage) {
  return prompt(promptMessage);
}

// Função principal
function main() {
  const textEditor = new TextEditor();
  textEditor.open();

  let line = getUserInput("Digite uma linha de texto (ou 'EOF' para terminar): ");

  while (line !== 'EOF') {
    textEditor.insertLine(textEditor.content.length + 1, line);
    line = getUserInput("Digite uma linha de texto (ou 'EOF' para terminar): ");
  }

  textEditor.save();
}

// Chamada da função principal para iniciar o editor de texto
main();
```
