# **Desafio: Estratégia Ótima em Xadrez usando MDP**

### **Descrição**
Neste desafio, você implementará um modelo simplificado do jogo de xadrez usando Processos de Decisão de Markov (MDP). O objetivo é encontrar a melhor estratégia para um agente (jogador de xadrez) tomar decisões com base em um conjunto de estados e ações possíveis.

### **Objetivo**
- Modelar um MDP para um cenário simplificado do jogo de xadrez.
- Implementar um pseudo-código que avalia as melhores jogadas usando MDP.
- Os alunos devem completar e interpretar os resultados.

---

## **1. Modelagem do Problema**
Definição dos componentes do MDP:

- **Estados ($S$)**: Representações abstratas do tabuleiro, por exemplo, "rei sob ataque", "peão pode ser promovido", "mate em 2 movimentos".
- **Ações ($A$)**: Movimentos possíveis, como "mover peão", "capturar peça", "rocar".
- **Transições ($T(s, a, s’)$)**: Probabilidade de transição de um estado para outro ao executar uma ação.
- **Recompensa ($R(s, a, s’)$)**: Recompensa associada a uma jogada. Exemplo: Capturar uma peça adversária pode ter recompensa +5, enquanto perder uma peça pode ser -5.
- **Política Ótima ($\pi(s)$)**: Estratégia que maximiza a recompensa esperada a longo prazo.

---

## **2. Pseudo-Código**
```python
class ChessMDP:
    def __init__(self, states, actions, transition_probs, rewards):
        self.states = states  # Lista de estados possíveis
        self.actions = actions  # Lista de ações possíveis
        self.transition_probs = transition_probs  # Probabilidades de transição P(s' | s, a)
        self.rewards = rewards  # Recompensas R(s, a, s')

    def policy_evaluation(self, policy, gamma=0.9, theta=0.01):
        """Avaliação de política: calcula o valor esperado de cada estado."""
        V = {s: 0 for s in self.states}
        while True:
            delta = 0
            for s in self.states:
                v = V[s]
                V[s] = sum(
                    self.transition_probs[s][a][s_prime] * 
                    (self.rewards[s][a] + gamma * V[s_prime]) 
                    for a in self.actions for s_prime in self.states
                )
                delta = max(delta, abs(v - V[s]))
            if delta < theta:
                break
        return V

    def policy_iteration(self):
        """Iteração de política para encontrar a estratégia ótima."""
        policy = {s: self.actions[0] for s in self.states}
        while True:
            V = self.policy_evaluation(policy)
            stable = True
            for s in self.states:
                old_action = policy[s]
                policy[s] = max(self.actions, key=lambda a: sum(
                    self.transition_probs[s][a][s_prime] * 
                    (self.rewards[s][a] + V[s_prime])
                    for s_prime in self.states
                ))
                if old_action != policy[s]:
                    stable = False
            if stable:
                break
        return policy, V

# TODO: Implementar um conjunto de estados e transições baseados em um cenário de xadrez.
# Execute a função policy_iteration e explique os resultados.
```

---

## **3. Tarefa para os Alunos**
1. **Completar a Definição dos Estados e Ações**  
   - Escolha um cenário específico do jogo (exemplo: final de jogo com poucas peças).  
   - Defina estados relevantes (exemplo: "rei em xeque", "torre protegida", "dama ameaçada").  
   - Defina ações viáveis para cada estado (exemplo: "mover rei", "capturar peça adversária").  

2. **Implementar a Matriz de Transição e Recompensas**  
   - Estabeleça regras de transição entre estados com base nas ações.  
   - Defina valores de recompensa para cada ação tomada.  

3. **Rodar a Iteração de Política**  
   - Execute `policy_iteration()` para encontrar a melhor estratégia.  

4. **Explicar os Resultados**  
   - Qual é a melhor ação em cada estado?  
   - Como a política muda ao longo das iterações?  
   - A estratégia encontrada faz sentido para um jogador de xadrez?  

---



[Retornar](./Topico3-ReprConhecimento.md)