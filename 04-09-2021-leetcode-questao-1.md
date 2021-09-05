# LeetCode: Two Sum (soma de dois números)

* Link: https://leetcode.com/problems/two-sum/
* Vídeo com explicação: https://www.youtube.com/watch?v=Aa1tbEXdDqk

## Pré-requisitos
* Array
* For Loop
* Hash Tables (dictionary)
* Complexidade* (opcional)

## Enunciado

Dado um array de números inteiros `nums` a um número inteiro `target`, retorne os *índices* dos dois números cuja soma é igual ao `target`.

Assuma que cada entrada do problema tem **exatamente uma única solução**.

A ordem da resposta não importa.

### Exemplo 1

**Entrada**: `nums = [2, 7, 11, 15], target = 9`

**Saída**:  `[0, 1]`, porque `nums[0] + nums[1] == 9`

### Exemplo 2

**Entrada**: `nums = [3, 2, 4], target = 6`

**Saída**:  `[1, 2]`, porque `nums[1] + nums[2] == 6`

### Exemplo 3

**Entrada**: `nums = [3, 3], target = 6`

**Saída**:  `[0, 1]`, porque `nums[0] + nums[1] == 6`


## Solução

### Solução 1: O(nˆ2), utilizando 2 iteradores

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        # nums = [2,7,11,15]
        #         0 1 2  3
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                vi = nums[i]
                vj = nums[j]
                
                if vi + vj == target:
                    return [i, j]
```

### Solução 2: O(n) utilizando Hashmap

```python
class Solution(object):
    def twoSum(self, nums, target):
        # Tabela {complement: índice do complemento}
        # complement = target - current
        # onde current é o valor do número visitado na iteração atual
        complement_table = {}
        
        # Para cada valor, calcular o complemento dele cuja soma = target.
        # Caso o complemento exista na tabela
        # buscar o valor do índice desse complemento na tabela.
        #
        # Caso contrário
        # inserir o índice do valor atual como valor para o complemento calculado na tabela.
        for index, current in enumerate(nums):
            complement = target - current
            if complement in complement_table:
                return [index, complement_table[complement]]

            complement_table[current] = index
```

Complexidade: nossa solução itera o array de entrada apenas uma vez, ou seja, O(n). Inserir e buscar elementos em uma *tabela Hash* é O(1).

Então nossa solução tem complexidade O(n) * O(1) => O(n).