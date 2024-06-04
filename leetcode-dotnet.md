Aqui estão alguns exemplos de perguntas técnicas de entrevista de programação em C# com soluções e análise de complexidade de tempo (Big O):

1. **Inverter uma string**

Pergunta: Como você inverteria uma string em C#?

Resolução:

```csharp
public string ReverseString(string s) {
    char[] charArray = s.ToCharArray();
    Array.Reverse(charArray);
    return new string(charArray);
}
```

Big O: O(n), onde n é o comprimento da string. A operação de reversão percorre metade do array, trocando os elementos correspondentes nas posições i e n-i.

2. **Verificar se uma string é um palíndromo**

Pergunta: Como você verificaria se uma string é um palíndromo em C#?

Resolução:

```csharp
public bool IsPalindrome(string s) {
    int start = 0;
    int end = s.Length - 1;
    while (start < end) {
        if (s[start] != s[end]) {
            return false;
        }
        start++;
        end--;
    }
    return true;
}
```

Big O: O(n), onde n é o comprimento da string. O algoritmo percorre metade da string, comparando os caracteres correspondentes nas posições i e n-i.

3. **Encontrar o número máximo em um array**

Pergunta: Como você encontraria o número máximo em um array em C#?

Resolução:

```csharp
public int FindMax(int[] nums) {
    int max = nums[0];
    for (int i = 1; i < nums.Length; i++) {
        if (nums[i] > max) {
            max = nums[i];
        }
    }
    return max;
}
```

Big O: O(n), onde n é o número de elementos no array. O algoritmo percorre todo o array uma vez para encontrar o máximo.

4. **Encontrar a frequência de um número em um array**

Pergunta: Como você encontraria a frequência de um número em um array em C#?

Resolução:

```csharp
public int FindFrequency(int[] nums, int num) {
    int count = 0;
    for (int i = 0; i < nums.Length; i++) {
        if (nums[i] == num) {
            count++;
        }
    }
    return count;
}
```

Big O: O(n), onde n é o número de elementos no array. O algoritmo percorre todo o array uma vez para contar a frequência do número.

Lembre-se de que a análise de complexidade de tempo (Big O) é uma estimativa do pior caso do tempo de execução de um algoritmo em função do tamanho da entrada.