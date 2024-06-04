Big O é uma notação usada em ciência da computação para descrever o desempenho ou a complexidade de um algoritmo. Big O especificamente descreve o pior caso de desempenho de um algoritmo em termos de tempo ou espaço.

Aqui estão alguns exemplos de notações Big O:

1. **O(1)**: Tempo constante - Independentemente do tamanho da entrada, o tempo de execução é o mesmo. Por exemplo, acessar um elemento de um array por índice.

```javascript
function getItem(array, index) {
    return array[index];
}
```

2. **O(n)**: Tempo linear - O tempo de execução aumenta linearmente com o tamanho da entrada. Por exemplo, encontrar o maior número em um array não ordenado requer a verificação de cada número uma vez.

```javascript
function findMax(array) {
    let max = -Infinity;
    for (let i = 0; i < array.length; i++) {
        if (array[i] > max) {
            max = array[i];
        }
    }
    return max;
}
```

3. **O(n^2)**: Tempo quadrático - O tempo de execução aumenta quadraticamente com o tamanho da entrada. Um exemplo comum é a ordenação de bolha.

```javascript
function bubbleSort(array) {
    for (let i = 0; i < array.length; i++) {
        for (let j = 0; j < array.length - i - 1; j++) {
            if (array[j] > array[j + 1]) {
                let temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
    return array;
}
```

4. **O(log n)**: Tempo logarítmico - O tempo de execução aumenta logaritmicamente com o tamanho da entrada. Um exemplo comum é a busca binária.

```javascript
function binarySearch(array, target) {
    let left = 0;
    let right = array.length - 1;
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        if (array[mid] === target) {
            return mid;
        } else if (array[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}
```

5. **O(n log n)**: Tempo linearítmico - O tempo de execução aumenta linearmente e logaritmicamente com o tamanho da entrada. Um exemplo comum é o algoritmo de ordenação merge sort.

```javascript
function mergeSort(array) {
    if (array.length <= 1) {
        return array;
    }
    let mid = Math.floor(array.length / 2);
    let left = mergeSort(array.slice(0, mid));
    let right = mergeSort(array.slice(mid));
    return merge(left, right);
}

function merge(left, right) {
    let result = [];
    while (left.length && right.length) {
        if (left[0] < right[0]) {
            result.push(left.shift());
        } else {
            result.push(right.shift());
        }
    }
    return result.concat(left, right);
}
```

Lembre-se de que a notação Big O descreve o pior caso de desempenho, então um algoritmo com uma complexidade de tempo de O(n) pode não necessariamente levar n operações para cada entrada, mas é garantido que não levará mais do que isso.