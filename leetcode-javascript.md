Aqui estão alguns exemplos de perguntas técnicas comuns em entrevistas de programação JavaScript, juntamente com soluções de exemplo e suas complexidades de tempo Big O:

1. **Encontrar o número duplicado**

Pergunta: Dado um array de inteiros onde cada valor aparece duas vezes, exceto um que aparece apenas uma vez, como você encontraria o valor único?

Resolução:

```javascript
function findUnique(nums) {
    let unique = 0;
    for (let num of nums) {
        unique ^= num;
    }
    return unique;
}
```

Big O: O(n), onde n é o número de elementos no array. Isso ocorre porque a função percorre cada elemento do array uma vez.

2. **Ordenação de array**

Pergunta: Como você ordenaria um array de inteiros em ordem crescente?

Resolução:

```javascript
function sortArray(nums) {
    return nums.sort((a, b) => a - b);
}
```

Big O: O(n log n), onde n é o número de elementos no array. Isso ocorre porque a função sort() do JavaScript usa um algoritmo de ordenação que tem uma complexidade de tempo de O(n log n).

3. **Fatorial**

Pergunta: Como você calcularia o fatorial de um número?

Resolução:

```javascript
function factorial(n) {
    if (n === 0) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}
```

Big O: O(n), onde n é o valor do número. Isso ocorre porque a função faz n chamadas recursivas.

4. **Encontrar o maior elemento em um array**

Pergunta: Como você encontraria o maior elemento em um array de números?

Resolução:

```javascript
function findMax(nums) {
    return Math.max(...nums);
}
```

Big O: O(n), onde n é o número de elementos no array. Isso ocorre porque a função Math.max() percorre cada elemento do array uma vez.

5. **Verificar se uma string é um palíndromo**

Pergunta: Como você verificaria se uma string é um palíndromo?

Resolução:

```javascript
function isPalindrome(s) {
    let reversed = s.split('').reverse().join('');
    return s === reversed;
}
```

Big O: O(n), onde n é o número de caracteres na string. Isso ocorre porque a função split() percorre cada caractere da string uma vez.