**Processos de Decisão de Markov (MDP - Markov Decision Processes)**

Os Processos de Decisão de Markov (MDP) modelam a interação entre agentes e ambientes dinâmicos para otimização de decisões. São amplamente utilizados em áreas como robótica, planejamento em inteligência artificial e jogos, onde um agente deve tomar decisões sequenciais para maximizar uma recompensa ao longo do tempo.

---

## **1. Conceitos Fundamentais**

### **1.1 Definição Formal**
Um MDP é definido por uma tupla $(S, A, P, R, \gamma)$, onde:
- **$S$ (Estados)**: Conjunto de estados possíveis do ambiente.
- **$A$ (Ações)**: Conjunto de ações disponíveis para o agente.
- **$P(s' | s, a)$ (Modelo de Transição)**: Probabilidade de transição para um novo estado $s'$ dado um estado atual $s$ e uma ação $a$.
- **$R(s, a)$ (Recompensa)**: Recompensa recebida ao tomar uma ação $a$ no estado $s$.
- **$\gamma$ (Fator de desconto)**: Parâmetro que controla a importância de recompensas futuras.

### **1.2 Propriedades**
- **Tomada de decisão sequencial**: O agente escolhe ações a cada instante com base no estado atual.
- **Princípio de optimalidade de Bellman**: A política ótima pode ser obtida de forma recursiva, garantindo a maximização da recompensa acumulada.
- **Política ($\pi$)**: Função que define qual ação o agente deve tomar em cada estado para maximizar sua recompensa esperada.

---

## **2. Aplicações**

### **2.1 Robótica**
MDPs são usados para planejamento e controle de robôs, permitindo que eles escolham ações de forma otimizada com base no estado do ambiente.

#### **Exemplo Prático**
Um robô aspirador pode usar um MDP para decidir se deve continuar limpando, voltar para a base ou procurar uma nova área, levando em consideração o nível de bateria e a quantidade de sujeira detectada.

### **2.2 Inteligência Artificial em Jogos**
MDPs são amplamente utilizados para modelar agentes em jogos que tomam decisões estratégicas para maximizar sua pontuação.

#### **Exemplo Prático**
Em um jogo de tabuleiro, um agente pode usar um MDP para decidir seus movimentos com base na probabilidade de vitória e nas ações do oponente.

---

## **3. Exercícios**

### **3.1 Exercício 1 - Implementação de um MDP Básico**
Implemente um MDP simples em Python que:
1. Defina um conjunto de estados e ações.
2. Simule transições e recompensas.
3. Complete a implementação para encontrar uma política ótima.

#### Código inicial:
```python
import numpy as np
import gym
from gym import spaces

class SimpleMDP:
    def __init__(self):
        self.states = ["A", "B", "C"]  # Estados possíveis
        self.actions = ["esquerda", "direita"]  # Ações possíveis
        self.transitions = {
            "A": {"esquerda": "A", "direita": "B"},
            "B": {"esquerda": "A", "direita": "C"},
            "C": {"esquerda": "B", "direita": "C"},
        }
        self.rewards = {"A": 0, "B": 1, "C": 5}  # Recompensas por estado

    def step(self, state, action):
        next_state = self.transitions[state][action]
        reward = self.rewards[next_state]
        return next_state, reward

# TODO: Implementar um método para encontrar a política ótima

print("Modelo de MDP configurado. Complete a implementação para encontrar a política ótima.")
```

### **3.2 Exercício 2 - Algoritmo de Iteração de Valores**
Modifique o código acima para incluir um método que implemente o algoritmo de Iteração de Valores para encontrar a política ótima.

---

## **4. Respostas e Explicações**

### **4.1 Solução para Exercício 1**
O código abaixo adiciona um método para encontrar a melhor política para o MDP.
```python
def find_optimal_policy(mdp, gamma=0.9, iterations=100):
    V = {s: 0 for s in mdp.states}  # Inicializa os valores de estado
    
    for _ in range(iterations):
        new_V = V.copy()
        for s in mdp.states:
            new_V[s] = max(
                sum([V[mdp.transitions[s][a]] * gamma + mdp.rewards[mdp.transitions[s][a]]])
                for a in mdp.actions
            )
        V = new_V
    
    policy = {}
    for s in mdp.states:
        policy[s] = max(mdp.actions, key=lambda a: V[mdp.transitions[s][a]])
    
    return policy

mdp = SimpleMDP()
policy = find_optimal_policy(mdp)
print("Política ótima encontrada:", policy)
```
Explicação:
- `V[s]` representa o valor esperado de um estado $s$.
- O algoritmo itera para atualizar os valores de estado com base nas recompensas e nas transições.
- A política ótima é determinada escolhendo a ação que leva ao estado com maior valor esperado.

### **4.2 Solução para Exercício 2**
Abaixo, o código modificado para usar a Iteração de Valores.
```python
def value_iteration(mdp, gamma=0.9, theta=1e-6):
    V = {s: 0 for s in mdp.states}
    while True:
        delta = 0
        new_V = V.copy()
        for s in mdp.states:
            q_values = [
                sum([V[mdp.transitions[s][a]] * gamma + mdp.rewards[mdp.transitions[s][a]]])
                for a in mdp.actions
            ]
            new_V[s] = max(q_values)
            delta = max(delta, abs(V[s] - new_V[s]))
        V = new_V
        if delta < theta:
            break
    
    policy = {s: max(mdp.actions, key=lambda a: V[mdp.transitions[s][a]]) for s in mdp.states}
    return policy

optimal_policy = value_iteration(mdp)
print("Política ótima usando Iteração de Valores:", optimal_policy)
```
Explicação:
- `value_iteration` aplica a equação de Bellman iterativamente até a convergência.
- `theta` define um critério de parada para evitar execuções infinitas.
- A política ótima é extraída após a convergência do algoritmo.

---

Os Processos de Decisão de Markov são ferramentas fundamentais na modelagem de agentes inteligentes. Seu uso se estende desde robótica até inteligência artificial em jogos, proporcionando um framework matemático sólido para tomada de decisões ótimas em ambientes dinâmicos.





[Retornar](./Topico3-ReprConhecimento.md)