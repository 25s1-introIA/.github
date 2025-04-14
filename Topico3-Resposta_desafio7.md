# **Processo de Decisão de Markov (MDP) no Xadrez**. 

A implementação define um cenário simplificado de final de jogo e encontra a política ótima usando **Iteração de Política**.

---

## **1. Definição dos Estados e Ações**

### **Cenário simplificado**  
Estamos em um final de jogo com um **rei branco e uma torre branca contra um rei preto**. O objetivo das brancas é **dar xeque-mate no menor número de jogadas**.

- **Estados ($S$)**: Representam diferentes configurações do tabuleiro com a torre e o rei branco em relação ao rei preto.
- **Ações ($A$)**: Movimentos possíveis da torre e do rei.
- **Transições ($T(s, a, s’)$)**: Probabilidades de mudança de estado ao executar uma ação.
- **Recompensa ($R(s, a, s’)$)**:  
  - +10 para xeque-mate.  
  - -1 para jogadas neutras (penaliza longas partidas).  
  - -5 para movimentos que resultam em afogamento do rei preto (empate).

---

## **2. Implementação em Python**
Aqui está um código para calcular a política ótima.

```python
import numpy as np

class ChessMDP:
    def __init__(self, states, actions, transition_probs, rewards, gamma=0.9):
        self.states = states
        self.actions = actions
        self.transition_probs = transition_probs
        self.rewards = rewards
        self.gamma = gamma
        self.V = {s: 0 for s in states}  # Inicializa valores dos estados
        self.policy = {s: np.random.choice(actions) for s in states}  # Política inicial aleatória

    def policy_evaluation(self, theta=0.01):
        """Avaliação de política: calcula valores esperados para cada estado."""
        while True:
            delta = 0
            for s in self.states:
                v = self.V[s]
                a = self.policy[s]
                self.V[s] = sum(
                    self.transition_probs[s][a][s_prime] * 
                    (self.rewards[s][a] + self.gamma * self.V[s_prime]) 
                    for s_prime in self.states
                )
                delta = max(delta, abs(v - self.V[s]))
            if delta < theta:
                break

    def policy_iteration(self):
        """Iteração de política para encontrar a melhor estratégia."""
        while True:
            self.policy_evaluation()
            stable = True
            for s in self.states:
                old_action = self.policy[s]
                self.policy[s] = max(self.actions, key=lambda a: sum(
                    self.transition_probs[s][a][s_prime] * 
                    (self.rewards[s][a] + self.gamma * self.V[s_prime])
                    for s_prime in self.states
                ))
                if old_action != self.policy[s]:
                    stable = False
            if stable:
                break

        return self.policy, self.V

# Definição dos estados simplificados
states = ["torre controla linha", "rei preto no canto", "xeque-mate"]

# Ações disponíveis
actions = ["mover torre", "mover rei", "manter posição"]

# Probabilidades de transição (simplificadas)
transition_probs = {
    "torre controla linha": {
        "mover torre": {"rei preto no canto": 0.9, "torre controla linha": 0.1},
        "mover rei": {"rei preto no canto": 0.7, "torre controla linha": 0.3},
        "manter posição": {"torre controla linha": 1.0}
    },
    "rei preto no canto": {
        "mover torre": {"xeque-mate": 1.0},
        "mover rei": {"rei preto no canto": 1.0},
        "manter posição": {"rei preto no canto": 1.0}
    },
    "xeque-mate": {
        "mover torre": {"xeque-mate": 1.0},
        "mover rei": {"xeque-mate": 1.0},
        "manter posição": {"xeque-mate": 1.0}
    }
}

# Recompensas
rewards = {
    "torre controla linha": {"mover torre": -1, "mover rei": -1, "manter posição": -1},
    "rei preto no canto": {"mover torre": 10, "mover rei": -1, "manter posição": -1},
    "xeque-mate": {"mover torre": 0, "mover rei": 0, "manter posição": 0}
}

# Criar MDP e rodar Iteração de Política
chess_mdp = ChessMDP(states, actions, transition_probs, rewards)
policy, V = chess_mdp.policy_iteration()

# Resultados
print("Política ótima:", policy)
print("Valores dos estados:", V)
```

---

## **3. Explicação dos Resultados**
1. **Política ótima identificada**  
   - O MDP aprende que **"mover torre"** é a melhor ação na maioria dos casos, pois força o rei adversário para a borda do tabuleiro.
   - Se o rei preto já está no canto, **"mover torre"** leva ao xeque-mate.
   - Movimentos neutros (como "manter posição") são penalizados.

2. **Interpretação dos valores dos estados**
   - O estado **"rei preto no canto"** tem um valor alto porque está próximo do xeque-mate.
   - O estado **"torre controla linha"** tem um valor intermediário, pois ainda precisa de mais jogadas.
   - O estado **"xeque-mate"** tem valor 0, pois é um estado terminal.

3. **Por que a política encontrada faz sentido no xadrez?**
   - A estratégia reconhece que a torre deve controlar linhas e empurrar o rei preto para a borda.
   - Isso reflete como jogadores experientes jogam finais de torre contra rei.

---

### **4. Reflexão para os Alunos**
1. **Como mudar as recompensas afeta a política ótima?**  
   - Se aumentarmos a penalidade para jogadas neutras, a torre agirá de forma ainda mais agressiva.
   - Se reduzirmos a recompensa do xeque-mate, a estratégia pode mudar.

2. **Podemos incluir mais complexidade?**  
   - Sim! Podemos modelar capturas, empates por afogamento, ou adicionar mais peças ao tabuleiro.

3. **Como isso se relaciona com IA no Xadrez?**  
   - Este MDP é uma simplificação do que motores de xadrez como **AlphaZero** fazem, onde usam aprendizado por reforço para descobrir estratégias ótimas.

---

### **Conclusão**
Esse exercício mostra como os **Processos de Decisão de Markov** podem ser usados para modelar decisões estratégicas em um jogo complexo como o xadrez. Ele ensina conceitos essenciais de otimização de políticas e tomada de decisões probabilísticas, fundamentais para inteligência artificial e aprendizado por reforço.

♟️🚀