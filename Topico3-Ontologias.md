# Ontologias

## Introdução
As **ontologias** são representações formais do conhecimento em um domínio específico. Elas permitem organizar informações de maneira estruturada, facilitando **a inferência automática** de novos conhecimentos. Ontologias são amplamente utilizadas em **inteligência artificial, web semântica, sistemas especialistas** e **bancos de dados semânticos**.

---
## Conceitos Fundamentais
### Componentes de uma Ontologia
1. **Conceitos (Classes)**: Representam entidades ou categorias no domínio (exemplo: "Animal", "Pessoa").
2. **Relações (Propriedades)**: Definem conexões entre os conceitos (exemplo: "temFilho", "éAmigoDe").
3. **Instâncias (Indivíduos)**: Objetos específicos dentro dos conceitos (exemplo: "Rex" como uma instância de "Cachorro").
4. **Axiomas**: Regras lógicas que governam as relações (exemplo: "Todo Mamífero é um Animal").

### Exemplo de Ontologia
Considere uma ontologia para um domínio de animais:
- "Cachorro" e "Gato" são subclasses de "Mamífero".
- "Mamífero" é uma subclasse de "Animal".
- "Rex" é um indivíduo da classe "Cachorro".
- "Rex temDono João".

Isso pode ser representado graficamente ou em linguagens como **OWL (Web Ontology Language)**.

---

**Taxonomias** são uma forma de representação do conhecimento, mas com uma estrutura mais simples do que **Ontologias**.

### **Diferença entre Taxonomias e Ontologias**
| Característica  | Taxonomia | Ontologia |
|---------------|----------|-----------|
| **Definição** | Hierarquia de categorias organizadas de forma estrita. | Representação formal do conhecimento com conceitos, relações e regras lógicas. |
| **Estrutura** | Árvore (pai-filho) com relações **é um**. | Grafo mais rico com diferentes tipos de relações. |
| **Semântica** | Apenas classificação e organização. | Permite inferência automática e raciocínio lógico. |
| **Exemplo** | \"Mamífero\" é uma subcategoria de \"Animal\". | \"Mamífero\" é um \"Animal\", mas também tem propriedades como \"tem sangue quente\" e \"dá leite\". |

### **Relação entre Taxonomias e Ontologias**
- **Toda ontologia contém uma taxonomia**, pois define classes e sub-classes em uma estrutura hierárquica.
- A **taxonomia** é um subconjunto da ontologia, mas sem a capacidade de inferência automática.
- Enquanto **taxonomias** organizam informações, **ontologias** adicionam regras e relações complexas para permitir raciocínio automatizado.

### **Resumo**
- Se você precisa **apenas classificar informações** → **Taxonomia**.
- Se você precisa **modelar conhecimento e inferir novas informações** → **Ontologia**.
---


Aqui está um exemplo prático em Python que ilustra a diferença entre **taxonomias** e **ontologias**.  

### **1. Taxonomia (Hierarquia Simples)**
Vamos criar uma **taxonomia** usando uma estrutura de árvore simples.

```python
class NodoTaxonomia:
    def __init__(self, nome):
        self.nome = nome
        self.subcategorias = []

    def adicionar_subcategoria(self, subcategoria):
        self.subcategorias.append(subcategoria)

    def exibir_taxonomia(self, nivel=0):
        print(" " * nivel * 2 + "- " + self.nome)
        for sub in self.subcategorias:
            sub.exibir_taxonomia(nivel + 1)

# Criando a taxonomia
animal = NodoTaxonomia("Animal")
mamifero = NodoTaxonomia("Mamífero")
reptil = NodoTaxonomia("Réptil")

cachorro = NodoTaxonomia("Cachorro")
gato = NodoTaxonomia("Gato")

mamifero.adicionar_subcategoria(cachorro)
mamifero.adicionar_subcategoria(gato)

animal.adicionar_subcategoria(mamifero)
animal.adicionar_subcategoria(reptil)

# Exibindo a taxonomia
print("Taxonomia de Animais:")
animal.exibir_taxonomia()
```

#### **Saída esperada:**
```
Taxonomia de Animais:
- Animal
  - Mamífero
    - Cachorro
    - Gato
  - Réptil
```
✅ **Observação**: Aqui temos apenas uma relação **hierárquica (é um)**, sem propriedades adicionais ou inferência.

---

### **2. Ontologia (Com Inferência)**
Agora, vamos criar uma **ontologia** usando `owlready2`, onde podemos adicionar **propriedades e regras**.

```python
from owlready2 import *

# Criando uma nova ontologia
onto = get_ontology("http://exemplo.org/animais.owl")

with onto:
    class Animal(Thing): pass
    class Mamifero(Animal): pass
    class Reptil(Animal): pass
    class Cachorro(Mamifero): pass
    class Gato(Mamifero): pass

    # Propriedades adicionais
    class temSom(ObjectProperty):
        domain = [Animal]
        range = [Thing]

    class temCaracteristica(DataProperty, FunctionalProperty):
        domain = [Animal]
        range = [str]

# Criando instâncias
rex = Cachorro("Rex")
rex.temCaracteristica.append("Latido")

gato_felix = Gato("Felix")
gato_felix.temCaracteristica.append("Mia")

# Exibindo informações da ontologia
print("\nOntologia de Animais:")
for animal in onto.Animal.instances():
    print(f"- {animal} ({animal.__class__.__name__})")
    for caracteristica in animal.temCaracteristica:
        print(f"  ↳ Característica: {caracteristica}")

# Salvando a ontologia
onto.save(file="animais.owl", format="rdfxml")
```

#### **Saída esperada:**
```
Ontologia de Animais:
- Rex (Cachorro)
  ↳ Característica: Latido
- Felix (Gato)
  ↳ Característica: Mia
```
✅ **Diferenciais da Ontologia:**
- Permite definir **propriedades adicionais** (`temCaracteristica`).
- Permite criar **regras e inferências** (por exemplo, um motor de inferência pode concluir que um **Mamífero sempre tem sangue quente**).

---

### **Resumo**
| | Taxonomia | Ontologia |
|------|------------|------------|
| **Estrutura** | Simples (hierárquica) | Complexa (relações e regras) |
| **Uso** | Organização de categorias | Representação formal do conhecimento |
| **Inferência** | ❌ Não suporta | ✅ Suporta |
| **Exemplo** | Relação \"Cachorro é um Mamífero\" | \"Cachorro late\" e \"Mamíferos têm sangue quente\" |

🚀 **Quer um desafio?** Tente adicionar à ontologia um novo conceito como **Ave**, com a propriedade `temAsas`

## Implementação Prática em Python (Google Colab)
Aqui está um **novo exemplo** de ontologia, agora modelando uma **rede de transporte urbano**, onde temos **estações de metrô**, **linhas de transporte** e suas conexões.  

---

### **Criando uma Ontologia de Transporte Urbano**
```python
from owlready2 import *

# Criando uma nova ontologia
onto = get_ontology("http://exemplo.org/transporte.owl")

with onto:
    # Definição de classes
    class Estacao(Thing): pass
    class Linha(Thing): pass
    
    # Propriedade para definir quais estações pertencem a uma linha
    class pertenceALinha(ObjectProperty):
        domain = [Estacao]
        range = [Linha]

    # Propriedade para representar conexão entre estações
    class conectadoCom(ObjectProperty):
        domain = [Estacao]
        range = [Estacao]
        symmetric = True  # A conexão é bidirecional

# Criando instâncias de linhas
linha_azul = Linha("LinhaAzul")
linha_vermelha = Linha("LinhaVermelha")

# Criando estações
estacao_1 = Estacao("EstacaoCentral")
estacao_2 = Estacao("EstacaoSul")
estacao_3 = Estacao("EstacaoLeste")

# Associando estações às linhas
estacao_1.pertenceALinha.append(linha_azul)
estacao_2.pertenceALinha.append(linha_azul)
estacao_3.pertenceALinha.append(linha_vermelha)

# Criando conexões entre estações
estacao_1.conectadoCom.append(estacao_2)
estacao_1.conectadoCom.append(estacao_3)

# Salvando a ontologia
onto.save(file="transporte.owl", format="rdfxml")
print("Ontologia de transporte criada e salva com sucesso!")
```

---

### **Consultando a Ontologia**
```python
# Carregando a ontologia salva
onto = get_ontology("transporte.owl").load()

# Verificando estações e suas conexões
print("\nEstações e suas conexões:")
for estacao in onto.Estacao.instances():
    print(f"- {estacao} pertence à {estacao.pertenceALinha[0]}")
    for conexao in estacao.conectadoCom:
        print(f"  ↳ Conectado com {conexao}")
```

---

### **Saída esperada**
```
Ontologia de transporte criada e salva com sucesso!

Estações e suas conexões:
- EstacaoCentral pertence à LinhaAzul
  ↳ Conectado com EstacaoSul
  ↳ Conectado com EstacaoLeste
- EstacaoSul pertence à LinhaAzul
- EstacaoLeste pertence à LinhaVermelha
```

---

### **Diferenciais desse exemplo**
✅ **Relacionamento entre conceitos**: As estações pertencem a uma linha e podem estar conectadas.  
✅ **Propriedades Semânticas**: `conectadoCom` é **symmetric**, ou seja, se a Estação A está conectada à Estação B, então B está conectada a A automaticamente.  
✅ **Expansível**: Você pode adicionar mais estações, conexões e até atributos como **tempo de deslocamento**.  

🚀 **Desafio:** Adicione uma propriedade `tempoDeViagem` para definir o tempo (em minutos) entre duas estações conectadas! Se precisar de ajuda, me avise! 😃



---
## Exercícios Práticos

### 1. Expanda a Ontologia
Adicione novos conceitos como **Pássaros** e relacione-os a "Animal".

### 2. Novas Propriedades
Crie a relação **temCor** para os animais e associe cores a instâncias.

### 3. Inferência Automática
Investigue como usar um **reasoner** para inferir novas informações automaticamente.

---
## Conclusão
Ontologias são fundamentais para representar conhecimento de forma estruturada e inferível por máquinas. Com `owlready2`, podemos definir ontologias, adicionar instâncias e executar inferências.

**Desafio final**: Modele uma ontologia para um domínio de sua escolha, como "Saúde" ou "Cidades Inteligentes"!

---
**Próximos Passos**
- Explore linguagens como **OWL e RDF** para modelagem semântica avançada.
- Use **motores de inferência** como HermiT para inferência lógica automática.
- Integre ontologias com **chatbots** ou sistemas de recomendação.

[Retornar](./Topico3-ReprConhecimento.md)