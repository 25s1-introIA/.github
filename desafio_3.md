
## **Desafio 3: Otimização da Rede de Energia Inteligente**  

**Cenário:**  
Uma cidade está implementando uma **rede de energia inteligente**, onde usinas geradoras devem distribuir eletricidade para diversas regiões da cidade. Cada estação possui uma **capacidade máxima** de energia e as regiões possuem **demandas variáveis**.  

**Objetivo:**  
Desenvolver um algoritmo baseado em **busca heurística** para otimizar a distribuição de energia, minimizando desperdícios e sobrecargas nas linhas de transmissão.  

### **Regras:**  
1. Cada **usina** tem um limite máximo de energia que pode fornecer.  
2. Cada **região** tem uma demanda específica de energia.  
3. O custo de transmissão entre uma usina e uma região depende da **distância euclidiana** entre elas.  
4. O algoritmo deve utilizar **A*** para encontrar a melhor distribuição de energia.  
5. O programa deve exibir a **lista de alocações** e indicar se alguma região ficou sem energia suficiente.  

### **Exemplo de Entrada:**  
```python
usinas = [
    {"id": "U1", "x": 0, "y": 0, "capacidade": 100},
    {"id": "U2", "x": 10, "y": 10, "capacidade": 150}
]

regioes = [
    {"id": "R1", "x": 3, "y": 3, "demanda": 50},
    {"id": "R2", "x": 8, "y": 9, "demanda": 70},
    {"id": "R3", "x": 12, "y": 14, "demanda": 80}
]
```

### **Saída esperada:**  
```plaintext
Distribuição de energia otimizada:
- U1 fornece 50 para R1
- U2 fornece 70 para R2
- U2 fornece 80 para R3
```

---
