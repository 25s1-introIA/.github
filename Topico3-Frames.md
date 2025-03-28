**Frames e Scripts: Representação do Conhecimento em IA**

### **1. Introdução**
A representação do conhecimento é essencial para sistemas de inteligência artificial, permitindo que agentes computacionais processem e infiram informações de forma estruturada. Duas abordagens fundamentais nesse contexto são **Frames** e **Scripts**, que organizam informações hierarquicamente para descrever conceitos e eventos.

---

### **2. Frames: Estruturas de Representação do Conhecimento**
Os **frames** foram introduzidos por Marvin Minsky em 1975 como uma estrutura para representar objetos, situações e conceitos de forma hierárquica. Um frame é uma estrutura de dados que agrupa atributos e valores associados a um conceito.

#### **2.1 Exemplo de Representação de um Frame**
Um carro pode ser representado por um frame contendo atributos como marca, modelo, cor e tipo de combustível:

```python
class Carro:
    def __init__(self, marca, modelo, cor, combustivel):
        self.marca = marca
        self.modelo = modelo
        self.cor = cor
        self.combustivel = combustivel
    
    def exibir_info(self):
        return f"{self.marca} {self.modelo}, Cor: {self.cor}, Combustível: {self.combustivel}"

# Exemplo de uso
meu_carro = Carro("Toyota", "Corolla", "Prata", "Gasolina")
print(meu_carro.exibir_info())
```

#### **2.2 Herança e Especialização em Frames**
Frames permitem a criação de estruturas hierárquicas, onde conceitos mais específicos herdam atributos de conceitos mais gerais:

```python
class CarroEletrico(Carro):
    def __init__(self, marca, modelo, cor, bateria):
        super().__init__(marca, modelo, cor, "Elétrico")
        self.bateria = bateria
    
    def exibir_info(self):
        return f"{self.marca} {self.modelo}, Cor: {self.cor}, Bateria: {self.bateria} kWh"

# Exemplo de uso
meu_tesla = CarroEletrico("Tesla", "Model S", "Branco", 100)
print(meu_tesla.exibir_info())
```

---

### **3. Scripts: Modelagem de Eventos**
Os **scripts** foram introduzidos por Roger Schank e representam sequências de eventos típicas em situações cotidianas. São usados para modelar como humanos esperam que certos eventos ocorram em um contexto específico.

#### **3.1 Exemplo de um Script: Restaurante**
Imagine o processo de ir a um restaurante. Ele segue uma sequência lógica de eventos:

1. Entrar no restaurante.
2. Pedir um cardápio.
3. Fazer o pedido.
4. Comer.
5. Pagar a conta.
6. Sair.

Podemos representar esse script em Python:

```python
def restaurante():
    print("1. Entrando no restaurante")
    print("2. Pegando o cardápio")
    print("3. Fazendo o pedido")
    print("4. Comendo a refeição")
    print("5. Pagando a conta")
    print("6. Saindo do restaurante")

# Executando o script
restaurante()
```

#### **3.2 Modelagem de Scripts com Classes**
Podemos usar classes para modelar eventos dinâmicos em um script mais flexível:

```python
class Restaurante:
    def __init__(self, cliente):
        self.cliente = cliente
        self.estado = "entrada"
    
    def proximo_passo(self):
        passos = ["entrada", "cardapio", "pedido", "comida", "pagamento", "saida"]
        if self.estado in passos:
            print(f"{self.cliente} está em: {self.estado}")
            self.estado = passos[passos.index(self.estado) + 1] if self.estado != "saida" else "finalizado"
        else:
            print("Processo concluído!")

# Simulando a interação
cliente1 = Restaurante("João")
while cliente1.estado != "finalizado":
    cliente1.proximo_passo()
```

---

### **4. Exercícios Práticos**

#### **4.1 Criando um Frame para Representar um Animal**
Crie uma classe chamada `Animal` que contenha atributos gerais como `nome`, `especie` e `som`. Depois, crie uma subclasse `Cachorro` que herde `Animal` e adicione um método `latir()`.

#### **4.2 Modelagem de um Script para Compra Online**
Crie uma função ou classe que modele o processo de compra online, incluindo os passos:
1. Escolher produto
2. Adicionar ao carrinho
3. Inserir dados de pagamento
4. Confirmar compra
5. Aguardar entrega

---

### **5. Conclusão**
Frames e Scripts são abordagens poderosas para organizar informações em sistemas de inteligência artificial. Enquanto **frames** estruturam conceitos e relações hierárquicas, **scripts** modelam sequências de eventos esperados. Ambas as técnicas são amplamente utilizadas em sistemas baseados em conhecimento, assistentes virtuais e aprendizado de máquina.

---

## Para Saber mais

- Guia de Inteligência Artificial TOTVS 2025: Este guia oferece uma visão abrangente sobre a aplicação de técnicas de IA, incluindo a modelagem de conhecimento por meio de frames e scripts. ​
TOTVS

- Frameworks de IA: Guia Completo para Iniciantes: Este artigo aborda diversas estruturas utilizadas no desenvolvimento de soluções de inteligência artificial, fornecendo insights sobre como modelar e implementar essas técnicas. ​
descomplicaia.com.br

- Inteligência Artificial IA: O GUIA COMPLETO (2025) - Udemy: Este curso online oferece uma introdução abrangente à inteligência artificial, abordando conceitos fundamentais e técnicas de modelagem, incluindo frames e scripts. 

- [Event Driven Architecture](https://www.redhat.com/pt-br/topics/integration/what-is-event-driven-architecture)


[Retornar](./Topico3-ReprConhecimento.md)