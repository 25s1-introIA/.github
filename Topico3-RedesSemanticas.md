# Redes Semânticas

## Introdução
As **redes semânticas** são uma forma de representação do conhecimento baseada em grafos, onde **nós** representam conceitos e **arestas** representam relações entre esses conceitos. Essa estrutura é amplamente utilizada em inteligência artificial, banco de dados semânticos e na web semântica.

## Conceitos Fundamentais
### Nós e Arestas
- **Nós**: Representam objetos, conceitos ou entidades (por exemplo, "Gato", "Mamífero").
- **Arestas**: Representam relações entre os nós (por exemplo, "Gato" **é um** "Mamífero").

### Tipos de Relações
- **Hierárquicas**: Indicam uma relação de herança (ex: "Cachorro" **é um** "Mamífero").
- **Associações**: Ligam conceitos relacionados (ex: "Gato" **tem** "Cauda").
- **Propriedades**: Definem atributos (ex: "Gato" **tem cor** "Cinza").

## Exemplo de Rede Semântica
Considere a seguinte representação:

- "Gato" é um "Mamífero"
- "Mamífero" é um "Animal"
- "Gato" tem "Cauda"
- "Gato" tem cor "Cinza"

Podemos representar essa rede graficamente ou usando um script em Python.

---
## Implementação Prática em Python (Google Colab)

Vamos utilizar a biblioteca **networkx** para criar e visualizar uma rede semântica.

### Instalação da Biblioteca
Caso ainda não tenha o **networkx**, instale com:
```python
!pip install networkx matplotlib
```

### Criando a Rede Semântica
```python
import networkx as nx
import matplotlib.pyplot as plt

# Criando um grafo direcionado
G = nx.DiGraph()

# Adicionando nós (conceitos)
nodes = ["Gato", "Mamífero", "Animal", "Cauda", "Cinza"]
G.add_nodes_from(nodes)

# Adicionando arestas (relações)
relations = [("Gato", "Mamífero", "é um"),
             ("Mamífero", "Animal", "é um"),
             ("Gato", "Cauda", "tem"),
             ("Gato", "Cinza", "tem cor")]

for src, dst, label in relations:
    G.add_edge(src, dst, label=label)

# Desenhando o grafo
plt.figure(figsize=(8, 5))
pos = nx.spring_layout(G)
nx.draw(G, pos, with_labels=True, node_size=3000, node_color='lightblue', edge_color='gray')
labels = {(src, dst): lbl for src, dst, lbl in relations}
nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)
plt.show()
```

---
## Exercícios Práticos
### 1. Expanda a Rede
Adicione novos conceitos e relações ao grafo, como:
- Cachorro é um Mamífero
- Cachorro tem cor Marrom
- Cachorro tem Cauda

**Desafio**: Como você poderia representar outras propriedades, como "Peso" e "Altura"?

### 2. Busca de Conceitos
Implemente uma função que encontre todos os conceitos relacionados a um determinado nó.
```python
def find_related_concepts(graph, node):
    return list(graph.neighbors(node))

print(find_related_concepts(G, "Gato"))
```

### 3. Verifique Relações Específicas
Crie uma função para verificar se um conceito pertence a uma categoria:
```python
def is_a(graph, concept, category):
    return nx.has_path(graph, concept, category)

print(is_a(G, "Gato", "Animal"))  # Deve retornar True
```

---
## Conclusão
As redes semânticas são uma ferramenta poderosa para representar conhecimento de forma estruturada e interpretável por máquinas. Usando Python e **networkx**, podemos criar, visualizar e manipular redes semânticas de maneira eficiente.

**Desafio final**: Implemente uma rede semântica para representar o domínio "Meios de Transporte"!

---
**Próximos Passos**
- Explore grafos mais complexos, como **ontologias**.
- Investigue o uso de **banco de dados grafos** como **Neo4j**.
- Integre a rede semântica com **chatbots** ou **Sistemas Especialistas**.


[Retornar](./Topico3-ReprConhecimento.md)