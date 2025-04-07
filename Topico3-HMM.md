**Modelos Ocultos de Markov (HMM - Hidden Markov Models)**

Os Modelos Ocultos de Markov (HMM) são uma classe de modelos probabilísticos amplamente utilizados para modelar sistemas dinâmicos nos quais os estados latentes influenciam as observações. Esses modelos são particularmente úteis em situações onde as variáveis de interesse não são diretamente observáveis, mas podem ser inferidas a partir de observações ruidosas ao longo do tempo.

---

## **1. Conceitos Fundamentais**

### **1.1 Definição Formal**
Um HMM é definido por:
- **Conjunto de estados ocultos**: $S = \{s_1, s_2, ..., s_N\}$.
- **Conjunto de observações**: $O = \{o_1, o_2, ..., o_T\}$.
- **Matriz de transição de estados**: $A = [a_{ij}]$, onde $a_{ij} = P(s_j | s_i)$ representa a probabilidade de transição do estado $s_i$ para o estado $s_j$.
- **Distribuição de emissão**: $B = [b_j(o)]$, que define a probabilidade de observar $o$ estando no estado $s_j$.
- **Distribuição de probabilidades iniciais**: $\pi = [\pi_i]$, onde $\pi_i$ é a probabilidade inicial do sistema começar no estado $s_i$.

### **1.2 Propriedades**
- **Processo de Markov**: A probabilidade de um estado futuro depende apenas do estado atual e não do histórico completo.
- **Independência condicional**: As observações dependem exclusivamente do estado oculto correspondente.

---

## **2. Aplicações**

### **2.1 Reconhecimento de Fala**
Os HMMs são amplamente utilizados no reconhecimento de fala, modelando sequências de fonemas. Cada palavra ou fonema pode ser representado como uma sequência de estados ocultos que emitem observações baseadas nas características acústicas do sinal de voz.

#### **Exemplo Prático**
Imagine um sistema de reconhecimento de palavras que tenta identificar se um usuário disse "gato" ou "pato". O HMM pode ter estados ocultos que representam diferentes fonemas, e as observações são as características extraídas do sinal de áudio (como frequência e intensidade). A transição entre estados define a probabilidade de um fonema seguir outro, enquanto a distribuição de emissão relaciona cada estado a possíveis sinais acústicos.

### **2.2 Análise de Sequências Biológicas**
Na bioinformática, os HMMs são utilizados para modelar sequências de DNA ou proteínas, ajudando a prever estruturas genéticas, domínios de proteínas e identificar genes em cadeias de DNA.

#### **Exemplo Prático**
Considere um modelo oculto de Markov aplicado à predição de regiões codificantes em um gene. Os estados ocultos representam se uma região do DNA pertence a um exon (região codificante) ou intron (não codificante). As observações são as sequências de nucleotídeos (A, C, G, T), e as transições entre estados ajudam a identificar padrões genéticos comuns.

---

## **3. Exercícios**

### **3.1 Exercício 1 - Implementação de um HMM Básico**
Implemente um HMM simples em Python que:
1. Defina estados ocultos e observáveis.
2. Simule uma sequência de observações geradas pelo modelo.
3. Complete a implementação para treinar o modelo a partir de uma sequência de observações.

#### Código inicial:
```python
import numpy as np
from hmmlearn import hmm

# Definição do modelo HMM
model = hmm.MultinomialHMM(n_components=2)
model.startprob_ = np.array([0.6, 0.4])
model.transmat_ = np.array([[0.7, 0.3], [0.4, 0.6]])
model.emissionprob_ = np.array([[0.5, 0.5], [0.2, 0.8]])

# Simular uma sequência de observações
test_seq = np.array([[0, 1, 0, 1, 1]]).T

# TODO: Ajuste o modelo com base em um conjunto de treinamento
# model.fit(...)

print("Modelo configurado. Complete a implementação para treinar o modelo.")
```

### **3.2 Exercício 2 - Estimativa da Sequência de Estados**
Modifique o código acima para incluir a estimativa da sequência de estados mais provável para uma sequência de observações utilizando o algoritmo de Viterbi.

---

## **4. Respostas e Explicações**

### **4.1 Solução para Exercício 1**
O código abaixo adiciona a funcionalidade de treinar o modelo com dados simulados.
```python
# Gerar dados de treino
X, Z = model.sample(100)  # Gerando 100 amostras

# Treinamento do modelo com as amostras geradas
model.fit(X)
print("Modelo treinado com sucesso!")
```
Explicação:
- `model.sample(100)`: Gera 100 amostras de sequências observáveis e seus estados ocultos.
- `model.fit(X)`: Ajusta o modelo aos dados de treinamento gerados.

### **4.2 Solução para Exercício 2**
A seguir, o código modificado para estimar a sequência de estados ocultos mais provável usando o algoritmo de Viterbi:
```python
# Estimativa da sequência de estados ocultos
logprob, state_sequence = model.decode(test_seq, algorithm="viterbi")
print("Sequência mais provável de estados:", state_sequence)
```
Explicação:
- `model.decode(test_seq, algorithm="viterbi")`: Retorna a sequência de estados ocultos mais provável para a sequência de observações fornecida.
- A variável `state_sequence` contém a estimativa da sequência oculta correspondente às observações.






[Retornar](./Topico3-ReprConhecimento.md)