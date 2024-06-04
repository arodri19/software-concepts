Estruturas de dados são uma maneira de organizar e armazenar dados para que possam ser acessados e trabalhados de maneira eficiente. Aqui estão alguns exemplos de estruturas de dados:

1. **Array**: Uma coleção de elementos identificados por índices ou chaves. Em JavaScript, um exemplo de um array seria:

```javascript
let array = [1, 2, 3, 4, 5];
```

2. **Pilha (Stack)**: Uma coleção de elementos com o princípio de que o último elemento adicionado será o primeiro a ser removido (LIFO - Last In, First Out). Aqui está um exemplo de uma pilha em JavaScript:

```javascript
class Stack {
    constructor() {
        this.items = [];
    }
    push(item) {
        this.items.push(item);
    }
    pop() {
        if (this.items.length == 0) return "Underflow";
        return this.items.pop();
    }
}
```

3. **Fila (Queue)**: Uma coleção de elementos que segue o princípio de que o primeiro elemento adicionado será o primeiro a ser removido (FIFO - First In, First Out). Aqui está um exemplo de uma fila em JavaScript:

```javascript
class Queue {
    constructor() {
        this.items = [];
    }
    enqueue(item) {
        this.items.push(item);
    }
    dequeue() {
        if (this.items.length == 0) return "Underflow";
        return this.items.shift();
    }
}
```

4. **Lista Ligada (Linked List)**: Uma coleção de elementos chamados nós, em que cada nó tem uma referência ao próximo nó na sequência.

```javascript
class Node {
    constructor(data, next = null) {
        this.data = data;
        this.next = next;
    }
}

class LinkedList {
    constructor() {
        this.head = null;
    }
}
```

5. **Árvore (Tree)**: Uma estrutura de dados não linear que simula uma hierarquia com conjuntos de nós conectados por arestas.

```javascript
class Node {
    constructor(data) {
        this.data = data;
        this.children = [];
    }
}

class Tree {
    constructor() {
        this.root = null;
    }
}
```

6. **Grafo (Graph)**: Uma estrutura de dados não linear que consiste em nós e arestas. Os nós são às vezes também referidos como vértices e as arestas são linhas ou arcos que conectam quaisquer dois nós no grafo.

```javascript
class Graph {
    constructor() {
        this.adjacencyList = {};
    }
}
```

7. **Hash Table (Tabela Hash)**: Uma estrutura de dados que implementa uma matriz associativa, um tipo de estrutura que pode mapear chaves para valores. Uma tabela hash usa uma função hash para calcular um índice no array de baldes ou slots, a partir do qual o valor desejado pode ser encontrado.

```javascript
class HashTable {
    constructor(size = 53) {
        this.keyMap = new Array(size);
    }
}
```

Cada uma dessas estruturas de dados tem suas próprias vantagens e desvantagens e são usadas em diferentes situações, dependendo do problema específico que você está tentando resolver.