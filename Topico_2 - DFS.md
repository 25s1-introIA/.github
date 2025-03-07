## Busca em Profundidade (Depth-First Search - DFS)

A **Busca em Profundidade** (DFS - Depth-First Search) é um dos principais algoritmos para exploração de grafos. Ele é amplamente utilizado em diversas aplicações, incluindo análise de grafos, resolução de labirintos e inteligência artificial.

### Como Funciona?
O DFS explora um grafo começando por um nó inicial e percorrendo o máximo possível em uma única direção antes de retroceder. O algoritmo pode ser implementado de forma recursiva ou iterativa usando uma pilha.

### Algoritmo DFS Recursivo

1. Marcar o nó atual como visitado.
2. Para cada vizinho do nó atual que ainda não foi visitado:
   - Chamar recursivamente o DFS para esse vizinho.

**Exemplo de implementação em Python:**

```python
# Implementação do DFS recursivo

def dfs_recursivo(grafo, no, visitado):
    visitado.add(no)
    print(no, end=' ')
    
    for vizinho in grafo[no]:
        if vizinho not in visitado:
            dfs_recursivo(grafo, vizinho, visitado)

# Exemplo de uso
grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

visitado = set()
dfs_recursivo(grafo, 'A', visitado)
```

### Algoritmo DFS Iterativo
O DFS também pode ser implementado usando uma pilha explícita para evitar a limitação de recursão da linguagem.

**Exemplo de implementação em Python:**

```python
# Implementação do DFS iterativo

def dfs_iterativo(grafo, inicio):
    visitado = set()
    pilha = [inicio]
    
    while pilha:
        no = pilha.pop()
        if no not in visitado:
            print(no, end=' ')
            visitado.add(no)
            pilha.extend(reversed(grafo[no]))

# Exemplo de uso
dfs_iterativo(grafo, 'A')
```

### Complexidade de Tempo
- **Pior caso**: O DFS percorre todos os nós e arestas uma vez, resultando em **O(V + E)**, onde:
  - `V` é o número de vértices.
  - `E` é o número de arestas.

### Aplicações do DFS
- Verificação de conectividade em grafos.
- Detecção de ciclos.
- Ordenação topológica em grafos direcionados acíclicos (DAGs).
- Resolução de quebra-cabeças, como o problema do labirinto.

### Conclusão
A busca em profundidade é uma técnica essencial para a exploração de grafos. Sua escolha depende do problema e das restrições do sistema, sendo a versão iterativa mais indicada para evitar problemas de estouro de pilha em grandes grafos.

