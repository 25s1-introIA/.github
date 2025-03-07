**Busca Uniforme em Algoritmos de Busca**

A busca uniforme, também conhecida como busca de custo uniforme (Uniform Cost Search - UCS), é um algoritmo de busca utilizado em inteligência artificial e teoria dos grafos. Ele é um caso especial da busca em largura, mas em vez de expandir os nós por níveis, expande sempre o nó com o menor custo acumulado desde o nó inicial. Esse tipo de busca é particularmente útil em situações onde o custo das transições entre estados varia e encontrar a solução mais barata é essencial.

## Funcionamento

1. **Inicialização**: O algoritmo começa inserindo o nó inicial em uma fila de prioridade (geralmente implementada como uma heap mínima), onde a prioridade é determinada pelo custo acumulado do caminho até aquele nó.

2. **Expansão do Nó**: O nó com o menor custo acumulado é retirado da fila. Se for o nó objetivo, a busca termina com sucesso.

3. **Geração de Sucessores**: Os nós filhos do nó expandido são gerados e adicionados à fila de prioridade com seus respectivos custos acumulados.

4. **Gerenciamento de Visitados**: Para evitar revisitar estados já explorados com menor custo, pode-se manter um conjunto de estados visitados e ignorar novos caminhos para esses estados se forem mais custosos.

5. **Continuidade do Processo**: O processo continua até encontrar o objetivo ou até que todos os nós tenham sido explorados sem encontrar uma solução.

## Propriedades

- **Completude**: A busca uniforme é completa, ou seja, se existir uma solução, ela será encontrada.
- **Otimidade**: Se o custo das arestas for positivo, UCS encontra sempre o caminho de menor custo.
- **Complexidade**: Dependendo do espaço de busca e da granularidade dos custos, pode ser mais eficiente que a busca em largura ou mais custosa que a busca A\*.

## Exemplo de Aplicação

A busca de custo uniforme é amplamente utilizada em aplicações como:

- Sistemas de navegação GPS, onde o objetivo é encontrar a rota mais curta em termos de tempo ou distância.
- Jogos e Inteligência Artificial, para calcular os caminhos mais eficientes para personagens e agentes.
- Planejamento de tarefas, onde é necessário otimizar a sequência de execução de operações.

## Comparação com Outros Algoritmos

| Algoritmo               | Completude          | Otimidade                        | Estratégia                                  |
| ----------------------- | ------------------- | -------------------------------- | ------------------------------------------- |
| Busca em Largura        | Sim                 | Apenas se os custos forem iguais | Expande por níveis                          |
| Busca de Custo Uniforme | Sim                 | Sim                              | Expande pelo menor custo acumulado          |
| Busca Gulosa            | Não necessariamente | Não                              | Expande pelo menor custo heurístico         |
| A\*                     | Sim                 | Sim (com heurística admissível)  | Expande pelo menor custo f(n) = g(n) + h(n) |

## Exemplo de Código

Aqui está um exemplo de implementação da busca de custo uniforme em Python:

```python
import heapq

def uniform_cost_search(graph, start, goal):
    priority_queue = [(0, start)]  # (custo, nó)
    visited = {}
    
    while priority_queue:
        cost, node = heapq.heappop(priority_queue)
        
        if node in visited and visited[node] <= cost:
            continue
        
        visited[node] = cost
        
        if node == goal:
            return cost
        
        for neighbor, weight in graph.get(node, []):
            heapq.heappush(priority_queue, (cost + weight, neighbor))
    
    return float('inf')  # Retorna infinito se não houver caminho

# Exemplo de uso
graph = {
    'A': [('B', 1), ('C', 4)],
    'B': [('C', 2), ('D', 5)],
    'C': [('D', 1)],
    'D': []
}

start, goal = 'A', 'D'
cost = uniform_cost_search(graph, start, goal)
print(f"Custo mínimo de {start} para {goal}: {cost}")
```

Em resumo, a busca uniforme é uma abordagem eficaz para encontrar caminhos de menor custo em grafos ponderados, sendo útil em diversas aplicações do mundo real.

