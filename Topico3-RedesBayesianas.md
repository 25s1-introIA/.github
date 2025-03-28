# Redes Bayesianas

## Introdução
As **Redes Bayesianas** são modelos probabilísticos que representam conhecimento incerto por meio de um **grafo acíclico dirigido (DAG)**, onde:
- **Nós** representam **variáveis aleatórias** (exemplo: "Chover", "Trânsito", "Atraso").
- **Arestas** representam **dependências condicionais** entre as variáveis.
- Cada nó possui uma **Distribuição de Probabilidade Condicional (DPC)**, que define a probabilidade da variável dado seus pais.

Esses modelos são amplamente utilizados em **inteligência artificial, diagnóstico médico, aprendizado de máquina** e **tomada de decisão sob incerteza**.

---
## Exemplo de Rede Bayesiana
Considere a seguinte situação:

- Se **Chover**, a probabilidade de **Trânsito** aumenta.
- Se houver **Trânsito**, há maior chance de **Atraso**.
- Se **Chover**, pode influenciar diretamente o **Atraso** (independentemente do trânsito).

Isso pode ser representado na seguinte estrutura:

```
  Chover  →  Trânsito  →  Atraso
     ↓
   Atraso
```

Essa estrutura indica que:
- "Atraso" depende tanto de "Trânsito" quanto de "Chover".
- "Trânsito" depende de "Chover".

Cada nó terá uma **Tabela de Probabilidades Condicionais (DPC)** que define essas relações.

---
## Implementação Prática em Python (Google Colab)
Vamos usar a biblioteca `pgmpy` para criar e inferir probabilidades em uma Rede Bayesiana.

### Instalação da Biblioteca
```python
!pip install pgmpy
```

### Criando a Rede Bayesiana
```python
from pgmpy.models import BayesianNetwork
from pgmpy.inference import VariableElimination
from pgmpy.factors.discrete import TabularCPD

# Definir a estrutura do grafo
modelo = BayesianNetwork([('Chover', 'Trânsito'), ('Chover', 'Atraso'), ('Trânsito', 'Atraso')])

# Definir as Tabelas de Probabilidades Condicionais (DPCs)
cpd_chover = TabularCPD(variable='Chover', variable_card=2, values=[[0.7], [0.3]])
cpd_transito = TabularCPD(variable='Trânsito', variable_card=2,
                           values=[[0.9, 0.4], [0.1, 0.6]],
                           evidence=['Chover'], evidence_card=[2])
cpd_atraso = TabularCPD(variable='Atraso', variable_card=2,
                         values=[[0.9, 0.6, 0.7, 0.1], [0.1, 0.4, 0.3, 0.9]],
                         evidence=['Trânsito', 'Chover'], evidence_card=[2, 2])

# Adicionar as DPCs ao modelo
modelo.add_cpds(cpd_chover, cpd_transito, cpd_atraso)

# Verificar se o modelo é válido
print("Modelo é válido?", modelo.check_model())
```

### Inferência na Rede Bayesiana
Podemos agora responder perguntas como: **Qual a probabilidade de atraso se estiver chovendo?**

```python
# Criando o objeto de inferência
infer = VariableElimination(modelo)

# Consultando a probabilidade de atraso dado que está chovendo
prob_atraso_dado_chuva = infer.query(variables=['Atraso'], evidence={'Chover': 1})
print(prob_atraso_dado_chuva)
```

---
## Exercícios Práticos

### 1. Expanda a Rede
Adicione um novo nó "Acidente" que dependa de "Trânsito" e afete "Atraso".

### 2. Alteração das Probabilidades
Modifique as tabelas de probabilidades condicionais para testar diferentes cenários.

### 3. Faça Novas Consultas
Experimente outras inferências, como:
```python
infer.query(variables=['Trânsito'], evidence={'Chover': 1})
```

---
## Conclusão
As Redes Bayesianas são ferramentas poderosas para modelar conhecimento incerto e tomar decisões baseadas em probabilidades. Usando `pgmpy`, podemos facilmente definir, visualizar e realizar inferências nesses modelos.

**Desafio final**: Modele um problema do seu interesse, como diagnóstico médico ou previsão de falhas em sistemas!

---
**Próximos Passos**
- Investigue redes bayesianas dinâmicas para modelar processos ao longo do tempo.
- Explore algoritmos de aprendizado para ajustar as probabilidades a partir de dados reais.
- Integre a rede bayesiana com um chatbot ou sistema de recomendação.


[Retornar](./Topico3-ReprConhecimento.md)