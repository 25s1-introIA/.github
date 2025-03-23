A **heurística de Manhattan** é usada no algoritmo A* para estimar a distância entre dois pontos em um grid (grade) onde só são permitidos movimentos horizontais e verticais (sem diagonais).  

### **Fórmula:**  
A distância de Manhattan entre dois pontos $(x_1, y_1)$ e $(x_2, y_2)$ é calculada como:  

$$
h(n) = |x_1 - x_2| + |y_1 - y_2|
$$

Ou seja, é a soma das diferenças absolutas das coordenadas **x** e **y**.

### **Por que é chamada de "Manhattan"?**  
O nome vem do sistema de ruas da cidade de **Manhattan, Nova York**, onde os quarteirões formam uma grade e os deslocamentos são feitos apenas na horizontal ou na vertical, como se estivesse seguindo ruas e avenidas.

### **Exemplo prático:**  
Imagine um tabuleiro onde você quer ir do ponto **A** (2,3) para o ponto **B** (5,6):

$$
h(n) = |5 - 2| + |6 - 3| = 3 + 3 = 6
$$

Isso significa que, no pior caso, serão necessários **6 movimentos** para chegar ao destino.

### **Por que usar a heurística de Manhattan no A*?**  
- É uma **estimativa admissível** (nunca superestima o custo real, garantindo um caminho ótimo).  
- Funciona bem para grids **onde os movimentos são restritos a quatro direções** (cima, baixo, esquerda, direita).  
- Simples de calcular e eficiente para busca de caminhos.  

Se o labirinto permitisse **movimentos diagonais**, usaríamos outra heurística, como a **distância Euclidiana**. 🚀