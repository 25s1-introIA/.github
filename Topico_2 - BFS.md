# Busca em Largura (BFS - Breadth-First Search)

A Busca em Largura (BFS - Breadth-First Search) é um algoritmo de busca em grafos utilizado para percorrer ou buscar elementos em uma estrutura de grafo ou árvore de maneira sistemática. A BFS explora todos os vértices de um grafo a uma mesma distância da raiz antes de prosseguir para os vértices mais distantes.

## Funcionamento

A BFS utiliza uma fila (“queue”) para gerenciar os vértices que devem ser visitados. O algoritmo segue os seguintes passos:

1. **Inicialização**: Escolhe-se um vértice inicial (raiz) e ele é marcado como visitado. Esse vértice é adicionado à fila.
2. **Exploração**: O primeiro vértice da fila é removido, e todos os seus vértices adjacentes não visitados são marcados como visitados e adicionados à fila.
3. **Repetição**: O passo 2 é repetido até que a fila esteja vazia, ou seja, todos os vértices acessíveis tenham sido visitados.

O processo garante que os vértices mais próximos da raiz sejam visitados antes dos mais distantes, tornando a BFS uma excelente escolha para encontrar o caminho mínimo em grafos não ponderados.

## Implementação da BFS

Abaixo, um exemplo de implementação da BFS em Python utilizando uma fila:

```python
from collections import deque

def bfs(grafo, inicio):
    visitados = set()
    fila = deque([inicio])
    visitados.add(inicio)
    
    while fila:
        vertice = fila.popleft()
        print(vertice, end=" ")
        
        for vizinho in grafo[vertice]:
            if vizinho not in visitados:
                visitados.add(vizinho)
                fila.append(vizinho)

# Exemplo de uso
grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F', 'G'],
    'D': ['B'],
    'E': ['B', 'H'],
    'F': ['C'],
    'G': ['C'],
    'H': ['E']
}

bfs(grafo, 'A')
```

### Explicação da Implementação
- Utilizamos uma fila (deque) para armazenar os vértices a serem explorados.
- O conjunto `visitados` garante que um vértice não seja visitado mais de uma vez.
- Começamos pelo vértice inicial, marcamos como visitado e adicionamos na fila.
- Enquanto a fila não estiver vazia, removemos o primeiro elemento, imprimimos e adicionamos seus vértices vizinhos não visitados.

## Complexidade
A complexidade da BFS depende da representação do grafo:
- **Lista de Adjacência**: \(O(V + E)\), onde V é o número de vértices e E o número de arestas.
- **Matriz de Adjacência**: \(O(V^2)\), pois é necessário verificar todas as conexões entre os vértices.

## Aplicações
A BFS é amplamente utilizada em diversas áreas, incluindo:
1. **Caminho mínimo em grafos não ponderados** (exemplo: labirintos, redes de transporte).
2. **Sistemas de recomendacão** (exemplo: redes sociais, busca de conexões entre usuários).
3. **Web Crawling** (varredura de links para indexação de páginas).
4. **Inteligência Artificial** (pesquisa de estados em problemas como o jogo dos 8-puzzles).

## Conclusão
A Busca em Largura é uma técnica fundamental em teoria dos grafos, eficiente para encontrar caminhos mínimos e explorar grafos de forma sistemática. Seu uso é essencial em diversas aplicações computacionais e em inteligência artificial.

