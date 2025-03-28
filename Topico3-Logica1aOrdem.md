**Lógica Proposicional e de Primeira Ordem na Representação do Conhecimento**

### **1. Introdução**
A lógica é uma ferramenta essencial para a representação do conhecimento em inteligência artificial e computação. A **Lógica Proposicional** e a **Lógica de Primeira Ordem** são utilizadas para modelar informações de forma estruturada, permitindo inferências e tomadas de decisão automáticas.

---

### **2. Representação do Conhecimento com Lógica Proposicional**
Na Lógica Proposicional, o conhecimento é representado por proposições (sentenças que podem ser verdadeiras ou falsas) e combinadas por conectivos lógicos.

#### **2.1 Exemplos de Representação**
- **Regra de Negociação:**
  - Se um cliente é fiel e fez mais de 10 compras, então ele tem direito a desconto.
  - \[ ClienteFiel \land Compras>10 \rightarrow Desconto \]

- **Clima:**
  - Se está chovendo, então a rua está molhada.
  - \[ Chuva \rightarrow RuaMolhada \]

#### **2.2 Implementação em Python**
Podemos usar a biblioteca `sympy` para manipular expressões lógicas.

```python
from sympy import symbols, And, Or, Not, Implies

# Definição de proposições
Chuva = symbols('Chuva')
RuaMolhada = symbols('RuaMolhada')
regra = Implies(Chuva, RuaMolhada)

# Verificando a regra
print("Regra:", regra)
```

---

### **3. Representação do Conhecimento com Lógica de Primeira Ordem**
A Lógica de Primeira Ordem permite descrever objetos, relações e quantificadores.

#### **3.1 Exemplo de Representação**
- **Todo aluno matriculado em um curso tem acesso ao material didático.**
  - $\forall x (Aluno(x) \rightarrow AcessoMaterial(x))$

- **Se um funcionário é gerente, então ele tem permissão para aprovar solicitações.**
  - $\forall x (Gerente(x) \rightarrow PermissaoAprovar(x))$

#### **3.2 Implementação em Python com `pyDatalog`**
```python
from pyDatalog import pyDatalog

pyDatalog.create_terms('Aluno, AcessoMaterial, x')
AcessoMaterial[x] = Aluno[x]

# Declarando alunos
+Aluno('Maria')
+Aluno('Joao')

# Consultando
print(AcessoMaterial['Maria'])  # Retorna True
print(AcessoMaterial['Pedro'])  # Retorna False
```

---

### **4. Exercícios Práticos**
#### **4.1 Verificação de Lógica Proposicional**
Implemente uma função em Python que avalie se a proposição "Se um aluno estudou, então ele passou" é verdadeira para um conjunto de dados.

```python
def verificar_estudo_passagem(estudou, passou):
    return not estudou or passou

print(verificar_estudo_passagem(True, True))  # True
print(verificar_estudo_passagem(True, False))  # False
```

#### **4.2 Consultas em Lógica de Primeira Ordem**
Utilizando `pyDatalog`, implemente um sistema que modele a hierarquia de cargos em uma empresa e permita verificar se um gerente tem permissão para aprovar projetos.

---

### **5. Conclusão**
A Lógica Proposicional e a Lógica de Primeira Ordem são ferramentas fundamentais na representação do conhecimento, permitindo modelagem precisa para sistemas de inteligência artificial, verificação de regras de negócio e inferência automática. O uso de Python possibilita implementações práticas e experimentação de conceitos de forma eficiente.


[Retornar](./Topico3-ReprConhecimento.md)