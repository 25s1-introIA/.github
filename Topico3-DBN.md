# **Redes Bayesianas Dinâmicas (DBN - Dynamic Bayesian Networks)**

As Redes Bayesianas Dinâmicas (DBN) são uma extensão das Redes Bayesianas para modelar dependências temporais. Elas são amplamente utilizadas para representar processos estocásticos, onde variáveis aleatórias evoluem ao longo do tempo, permitindo inferência sobre estados futuros e passados com base em observações.

---

## **1. Conceitos Fundamentais**

### **1.1 Definição Formal**
Uma DBN é definida por:
- **Nós de estado**: Representam variáveis ocultas que evoluem ao longo do tempo.
- **Nós de observação**: Representam variáveis observáveis influenciadas pelos estados.
- **Arestas direcionadas**: Definem relações probabilísticas entre variáveis em diferentes instantes de tempo.
- **Modelo de transição**: Define a evolução das variáveis ocultas ao longo do tempo.
- **Modelo de observação**: Relaciona variáveis ocultas a observações.

### **1.2 Propriedades**
- **Memória de Markov**: O estado atual depende apenas do estado anterior e não de todo o histórico.
- **Fatorização**: A DBN pode ser decomposta em sub-redes estáticas que se repetem ao longo do tempo.

---

## **2. Aplicações**

### **2.1 Sistemas de Navegação Autônoma**
As DBNs são usadas em robótica para estimar a posição e o estado de um robô ao longo do tempo, mesmo com sensores imprecisos.

#### **Exemplo Prático**
Um robô equipado com sensores de GPS e câmera pode usar uma DBN para estimar sua posição real, combinando medições ruidosas com um modelo probabilístico de movimento.

### **2.2 Previsão de Eventos**
As DBNs são utilizadas para prever eventos futuros com base em dados históricos, como previsão de falhas em máquinas ou tendências do mercado financeiro.

#### **Exemplo Prático**
Um sistema de manutenção preditiva pode usar uma DBN para estimar a probabilidade de falha de um equipamento com base em medições de vibração e temperatura ao longo do tempo.

---

## **3. Exercícios**

### **3.1 Exercício 1 - Implementação de uma DBN Básica**
Implemente uma DBN simples em Python que:
1. Defina estados ocultos e observáveis.
2. Simule uma sequência de observações geradas pelo modelo.
3. Complete a implementação para treinar a DBN com dados simulados.

#### Código inicial:
```python
import numpy as np
from pomegranate import BayesianNetwork

# Definição da estrutura da DBN
model = BayesianNetwork()

# TODO: Definir estados ocultos e observáveis
# TODO: Criar as relações entre os nós da rede
# TODO: Treinar a rede com dados simulados

print("Modelo configurado. Complete a implementação para treinar a DBN.")
```

### **3.2 Exercício 2 - Inferência na DBN**
Modifique o código acima para incluir um método que estime o estado mais provável para uma nova sequência de observações.

---

## **4. Respostas e Explicações**

### **4.1 Solução para Exercício 1**
O código abaixo adiciona a definição de estados e o treinamento da DBN com dados simulados.
```python
from pomegranate import DiscreteDistribution, ConditionalProbabilityTable, State

# Definição das distribuições de probabilidade
estado_anterior = DiscreteDistribution({'Normal': 0.7, 'Falha': 0.3})
transicao = ConditionalProbabilityTable([
    ['Normal', 'Normal', 0.8],
    ['Normal', 'Falha', 0.2],
    ['Falha', 'Normal', 0.4],
    ['Falha', 'Falha', 0.6]
], [estado_anterior])

observacao = ConditionalProbabilityTable([
    ['Normal', 'Leitura OK', 0.9],
    ['Normal', 'Leitura Ruim', 0.1],
    ['Falha', 'Leitura OK', 0.3],
    ['Falha', 'Leitura Ruim', 0.7]
], [transicao])

# Criação dos estados
s1 = State(estado_anterior, name='Estado Anterior')
s2 = State(transicao, name='Estado Atual')
s3 = State(observacao, name='Observação')

# Construção do modelo
model.add_states(s1, s2, s3)
model.add_edge(s1, s2)
model.add_edge(s2, s3)
model.bake()
print("DBN treinada com sucesso!")
```
Explicação:
- Criamos distribuições de probabilidade para estados e observações.
- Definimos as relações entre estados ao longo do tempo.
- Construímos a DBN e finalizamos seu treinamento.

### **4.2 Solução para Exercício 2**
A seguir, o código modificado para inferir o estado mais provável com base em observações.
```python
# Observação de entrada
test_seq = ['Leitura OK', 'Leitura Ruim', 'Leitura OK']

# Inferência
predictions = model.predict([[None] + test_seq])
print("Estados mais prováveis:", predictions)
```
Explicação:
- `model.predict(...)` retorna a sequência de estados ocultos mais provável para as observações fornecidas.
- O primeiro valor `None` indica que o estado inicial deve ser inferido.

---

As Redes Bayesianas Dinâmicas são ferramentas poderosas para modelagem probabilística de processos temporais. Seu uso permite resolver problemas complexos em previsão de eventos, diagnóstico de sistemas e navegação autônoma.





[Retornar](./Topico3-ReprConhecimento.md)