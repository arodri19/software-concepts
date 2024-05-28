**SOLID** é um acrônimo para cinco princípios de design de software orientado a objetos e sistemas. Aqui estão eles com exemplos em JavaScript:

1. **Princípio da Responsabilidade Única (SRP)**: Uma classe deve ter apenas um motivo para mudar. Isso significa que deve ter apenas uma tarefa ou responsabilidade.

```javascript
// Ruim
class UserSettings {
    constructor(user) {
        this.user = user;
    }

    changeSettings(settings) {
        if (this.verifyCredentials()) {
            // ...
        }
    }

    verifyCredentials() {
        // ...
    }
}

// Bom
class UserAuth {
    constructor(user) {
        this.user = user;
    }

    verifyCredentials() {
        // ...
    }
}

class UserSettings {
    constructor(user) {
        this.user = user;
        this.auth = new UserAuth(user);
    }

    changeSettings(settings) {
        if (this.auth.verifyCredentials()) {
            // ...
        }
    }
}
```

2. **Princípio Aberto-Fechado (OCP)**: As entidades de software (classes, módulos, funções, etc.) devem estar abertas para extensão, mas fechadas para modificação.

```javascript
// Ruim
class Rectangle {
    constructor(width, height) {
        this.width = width;
        this.height = height;
    }
}

class AreaCalculator {
    constructor(shapes) {
        this.shapes = shapes;
    }

    sum() {
        return this.shapes.reduce((acc, shape) => {
            if (shape instanceof Rectangle) {
                acc += shape.width * shape.height;
            }
            return acc;
        }, 0);
    }
}

// Bom
class Shape {
    area() {
        throw new Error('Area method should be implemented');
    }
}

class Rectangle extends Shape {
    constructor(width, height) {
        super();
        this.width = width;
        this.height = height;
    }

    area() {
        return this.width * this.height;
    }
}

class AreaCalculator {
    constructor(shapes) {
        this.shapes = shapes;
    }

    sum() {
        return this.shapes.reduce((acc, shape) => {
            acc += shape.area();
            return acc;
        }, 0);
    }
}
```

3. **Princípio da Substituição de Liskov (LSP)**: As subclasses devem ser substituíveis por suas classes base.

```javascript
// Ruim
class Bird {
    fly() {
        // ...
    }
}

class Duck extends Bird {
    // ...
}

class Ostrich extends Bird {
    fly() {
        throw new Error('Cannot fly');
    }
}

// Bom
class Bird {
    // ...
}

class FlyingBirds extends Bird {
    fly() {
        // ...
    }
}

class Duck extends FlyingBirds {
    // ...
}

class Ostrich extends Bird {
    // ...
}
```

4. **Princípio da Segregação de Interface (ISP)**: Os clientes não devem ser forçados a depender de interfaces que não usam.

```javascript
// Ruim
class Worker {
    work() {
        // ...
    }

    eat() {
        // ...
    }
}

// Bom
class Worker {
    work() {
        // ...
    }
}

class Eater {
    eat() {
        // ...
    }
}

class Human implements Worker, Eater {
    work() {
        // ...
    }

    eat() {
        // ...
    }
}
```

5. **Princípio da Inversão de Dependência (DIP)**: Dependa de abstrações, não de concreções.

```javascript
// Ruim
class Fetch {
    request(url) {
        // return fetch(url).then(r => r.json());
    }
}

class NewsFeed {
    constructor() {
        this.fetch = new Fetch();
    }

    get() {
        return this.fetch.request('http://someapi.com');
    }
}

// Bom
class Fetch {
    request(url) {
        // return fetch(url).then(r => r.json());
    }
}

class NewsFeed {
    constructor(fetch) {
        this.fetch = fetch;
    }

    get() {
        return this.fetch.request('http://someapi.com');
    }
}

const newsFeed = new NewsFeed(new Fetch());
```