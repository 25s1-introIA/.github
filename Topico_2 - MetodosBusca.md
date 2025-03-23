# Métodos de Busca

## Estrutura da Aula (4 Horas)

### Parte 1: Fundamentos e Conceitos (1h30)
- Estruturas de Dados
- Introdução aos métodos de busca.
- Classificação: Busca Cega vs Busca Heurística.
- Importância da análise de complexidade computacional.

### Parte 2: Métodos Tradicionais (1h)
- Busca linear e busca binária.
- Aplicações e limitações.
- Exercícios práticos e discussões.

### Parte 3: Busca em Grafos (1h)
- BFS e DFS.
- Exemplos com representações gráficas.
- Implementação e comparação dos métodos.

### Parte 4: Algoritmos Avançados e Tendências (1h)
- Explicação do A* e comparação com BFS e DFS.
- Introdução às novas tendências.
- Discussão sobre aplicações reais.
- Desafios e exercícios avançados.


## Introdução
Os métodos de busca são algoritmos fundamentais da ciência da computação e inteligência artificial, utilizados para encontrar um determinado valor ou caminho dentro de um conjunto de dados ou estrutura específica, como [**listas**, **árvores** e **grafos**](Topico_2%20-%20EstruturaDados.md). Eles são amplamente aplicados em bancos de dados, sistemas de recomendação, inteligência artificial e redes computacionais.

---

## Tipos de Métodos de Busca
Os métodos de busca podem ser classificados em dois grandes grupos:

1. **Busca não informada (Cega)**
   - Não utiliza informações sobre o problema para guiar a busca.
   - Explora os estados do problema de forma sistemática, sem conhecimento adicional além das regras do problema.
   - Exemplos: 
     - [Busca em Largura (BFS)](Topico_2%20-%20BFS.md)
     - [Busca em Profundidade (DFS)](./Topico_2%20-%20DFS.md)
     - [Busca Uniforme](./Topico_2%20-%20BuscaUniforme.md)


2. [**Busca informada (Heurística)**](./busca_heuristica.md)
   - Utiliza informações adicionais (heurísticas) para melhorar a eficiência.
   - Faz uso de funções heurísticas para estimar o custo de alcançar a solução.
   - Exemplos:
     - A* (A estrela)
     - Busca Gananciosa (Greedy Best-First Search)
     - Algoritmo de Hill Climbing

---

## Métodos de Busca em Detalhe

### 1. Busca Linear
- **Definição**: Percorre uma lista elemento por elemento até encontrar o valor desejado.
- **Complexidade**: O(n), onde n é o número de elementos.
- **Limitações**: Ineficiente para grandes conjuntos de dados.
- **Aplicações**: Listas desordenadas, busca em arquivos de texto.

#### *Exercício*:
Dado um array de números inteiros, implemente a busca linear para encontrar um número específico e conte o número de comparações feitas.

---

### 2. Busca Binária
- **Definição**: Busca um elemento dividindo o espaço de busca ao meio em cada iteração.
- **Complexidade**: O(log n).
- **Limitações**: Requer que os dados estejam ordenados.
- **Aplicações**: Pesquisa em grandes bases de dados ordenadas, algoritmos de busca em dicionários.

####  *Exercício*:
Implemente a busca binária para encontrar um elemento em um array ordenado e conte quantas iterações foram necessárias para encontrar o número.

---

### 3. Busca em Largura (BFS - Breadth-First Search)
- **Definição**: Explora todos os nós em um nível antes de ir para o próximo.
- **Complexidade**: O(V + E), onde V é o número de vértices e E o número de arestas.
- **Limitações**: Pode consumir muita memória em grafos muito grandes.
- **Aplicações**: Resolução de labirintos, redes sociais, transmissão de pacotes na internet.

####  *Exercício*:
Dado um grafo representando um labirinto, implemente a BFS para encontrar o caminho mais curto até a saída.

---

### 4. Busca em Profundidade (DFS - Depth-First Search)
- **Definição**: Explora cada caminho ao máximo antes de retroceder.
- **Complexidade**: O(V + E).
- **Limitações**: Pode entrar em loops se não houver controle de nós visitados.
- **Aplicações**: Problemas de conectividade, jogos, análise de redes.

####  *Exercício*:
Dado um grafo, implemente a DFS para detectar ciclos e exibir os ciclos encontrados.

---

### 5. Algoritmo A*
- **Definição**: Usa heurística para encontrar o caminho mais curto com custo mínimo.
- **Complexidade**: O(b^d), onde b é o fator de ramificação e d é a profundidade da solução.
- **Limitações**: A eficiência depende da qualidade da heurística.
- **Aplicações**: Navegação GPS, jogos, sistemas de roteamento.

####  *Exercício*:
Implemente o A* para encontrar o caminho mais curto entre duas cidades em um mapa e compare com o BFS.

---

## Novas Tendências
- **Busca com Aprendizado de Máquina**: Uso de redes neurais para guiar a busca em problemas complexos.
- **Quantum Search Algorithms**: Uso de computação quântica para melhorar a eficiência de buscas em grandes volumes de dados.
- **Reforço Aprimorado**: Aplicação de Aprendizado por Reforço para otimizar estratégias de busca em ambientes dinâmicos.
- **Busca em Grandes Volumes de Dados (Big Data)**: Algoritmos especializados para busca eficiente em grandes bases de dados distribuídas.

---




# Desafios

- [Desafio 1](./desafio_1.md)
- [Desafio 2](./desafio_2.md)
- [Desafio 3](./desafio_3.md)
- [Desafio 4](./desafio_4.md)




# Para saber mais:

- [Algoritmo A*](https://www.datacamp.com/pt/tutorial/a-star-algorithm)
---