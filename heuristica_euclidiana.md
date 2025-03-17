A **heurística Euclidiana** é usada para estimar a distância entre dois pontos em um espaço onde os movimentos podem ser feitos em **qualquer direção**, incluindo diagonais. Ela calcula a **distância em linha reta** entre os pontos, como se estivesse medindo com uma régua.

### **Fórmula:**  
A distância Euclidiana entre dois pontos \((x_1, y_1)\) e \((x_2, y_2)\) é dada por:

$
h(n) = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}
$

Essa é a famosa fórmula do **Teorema de Pitágoras**, onde estamos calculando a hipotenusa do triângulo formado pela diferença nas coordenadas.

---

### **Por que usar a heurística Euclidiana?**  
- Funciona bem quando **movimentos diagonais são permitidos** (exemplo: jogos de tabuleiro, robôs móveis, mapas de navegação).  
- Garante uma estimativa mais realista da distância quando comparada à heurística de Manhattan.  

---

### **Exemplo prático:**  
Imagine um personagem tentando ir do ponto **A** (1,2) para o ponto **B** (4,6) em um espaço onde ele pode se mover livremente em qualquer direção.  

A distância Euclidiana seria:

$
h(n) = \sqrt{(4 - 1)^2 + (6 - 2)^2}
$

$
h(n) = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5
$

Isso significa que, se pudesse se mover em linha reta, ele percorreria exatamente **5 unidades**.

---

### **Comparação com Manhattan:**  
Se usássemos a **heurística de Manhattan** para esse mesmo exemplo:

$
h(n) = |4 - 1| + |6 - 2| = 3 + 4 = 7
$

A heurística de Manhattan superestima o custo se o personagem puder se mover na diagonal, enquanto a Euclidiana dá um valor mais próximo do real.

---

### **Quando escolher Manhattan vs. Euclidiana?**  
- **Manhattan** → Quando **só pode andar em linhas retas** (exemplo: labirintos com paredes verticais e horizontais).  
- **Euclidiana** → Quando pode **andar em qualquer direção, incluindo diagonais**.  

