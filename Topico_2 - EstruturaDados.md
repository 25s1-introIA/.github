# Estruturas de Dados: Listas, Árvores e Grafos

## Introdução
Estruturas de dados são formas organizadas de armazenar e gerenciar informações para facilitar a manipulação e busca de dados. Entre as principais estruturas, destacam-se as **listas**, **árvores** e **grafos**, cada uma adequada para diferentes tipos de problemas computacionais.

---

## 1. Listas
### Conceito
Uma lista é uma coleção ordenada de elementos onde a posição dos itens é significativa. Ela pode armazenar qualquer tipo de dado e permite operações como inserção, remoção e busca.

### Tipos de Listas
- **Lista Simplesmente Encadeada**: Cada elemento (nó) aponta para o próximo.
- **Lista Duplamente Encadeada**: Cada nó possui referências tanto para o próximo quanto para o anterior.
- **Lista Circular**: A última posição referencia o primeiro elemento, formando um ciclo.
- **Array (Vetor)**: Uma sequência contínua de elementos acessados por índice.

### Aplicações
- Armazenamento de coleções ordenadas.
- Implementação de filas e pilhas.
- Representação de sequências dinâmicas de elementos.

### Exemplo de Implementação (Python)
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
    
    def append(self, data):
        if not self.head:
            self.head = Node(data)
            return
        temp = self.head
        while temp.next:
            temp = temp.next
        temp.next = Node(data)
```

---

## 2. Árvores
### Conceito
Uma árvore é uma estrutura hierárquica composta por nós conectados por arestas. Cada nó pode ter filhos, formando uma estrutura em formato de "árvore" invertida.

### Tipos de Árvores
- **Árvore Binária**: Cada nó tem no máximo dois filhos.
- **Árvore de Busca Binária (BST)**: Os nós seguem a regra de que valores menores ficam à esquerda e maiores à direita.
- **Árvore Balanceada (AVL, Red-Black)**: Mantém um equilíbrio para garantir operações eficientes.
- **Heap**: Estrutura especializada para acesso rápido ao menor ou maior elemento.

### Aplicações
- Indexação em bancos de dados.
- Implementação de compiladores e linguagens.
- Estruturas de decisão e inteligência artificial.

### Exemplo de Implementação (Python - Árvore Binária de Busca)
```python
class TreeNode:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

def insert(root, key):
    if root is None:
        return TreeNode(key)
    if key < root.val:
        root.left = insert(root.left, key)
    else:
        root.right = insert(root.right, key)
    return root
```

---

## 3. Grafos
### Conceito
Um grafo é uma estrutura composta por um conjunto de **vértices (ou nós)** conectados por **arestas**. Ele pode ser direcionado ou não-direcionado.

### Tipos de Grafos
- **Grafo Direcionado**: As conexões possuem direções.
- **Grafo Não-Direcionado**: As conexões não possuem direção específica.
- **Grafo Ponderado**: Cada aresta possui um peso associado.
- **Grafo Cíclico e Acíclico**: Define se há ciclos na estrutura.

### Aplicações
- Modelagem de redes sociais.
- Algoritmos de roteamento na internet.
- Representação de mapas e caminhos.

### Exemplo de Implementação (Python - Lista de Adjacência)
```python
class Graph:
    def __init__(self):
        self.graph = {}
    
    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        self.graph[u].append(v)
```

---

## Conclusão
Cada estrutura de dados possui características distintas que as tornam mais adequadas para diferentes tipos de problemas. Listas são ideais para sequências ordenadas, árvores são eficientes para buscas estruturadas e grafos são utilizados para modelar conexões complexas. Escolher a estrutura correta é fundamental para garantir eficiência e escalabilidade nos algoritmos computacionais.

---

## **Exercícios Práticos - Entrega na próxima aula** 

### 1. Lista Encadeada: Implementação de Blockchain Simples
**Descrição:** Implemente uma blockchain simples usando uma lista encadeada. Cada bloco deve conter:
- Um identificador único (hash).
- Um dado armazenado.
- Um ponteiro para o bloco anterior.

**Objetivo:** Criar uma estrutura de blockchain onde novos blocos podem ser adicionados e a integridade da cadeia possa ser verificada.

---

### 2. Árvore: Sistema Especialista para Diagnóstico Médico
**Descrição:** Implemente um sistema especialista baseado em uma árvore de decisão para diagnóstico médico.
- Cada nó representa uma pergunta.
- As folhas contêm diagnósticos possíveis.
- O sistema deve permitir a navegação por meio das respostas do usuário.

**Objetivo:** Modelar um sistema que, dado um conjunto de respostas do usuário, leve a um diagnóstico baseado na estrutura da árvore. Apresentar uma POC

---

### 3. Grafo: Roteamento de Entregas
**Descrição:** Considere um sistema de entregas em uma cidade, onde os pontos de entrega são representados por nós e as estradas por arestas com pesos (distâncias ou tempos de viagem).
- Modele a malha de estradas como um grafo ponderado.
- Use o algoritmo de Dijkstra para encontrar o caminho mais curto entre o depósito e um destino específico.

**Objetivo:** Desenvolver um programa que auxilie no cálculo da melhor rota para minimizar o tempo ou distância de uma entrega.

---



## Para saber mais:

- [Algortitmo Dijkstra](https://www.datacamp.com/pt/tutorial/dijkstra-algorithm-in-python)
- [Estruturas de Dados e Algoritmos - Heap](https://joaoarthurbm.github.io/eda/posts/heap/)
