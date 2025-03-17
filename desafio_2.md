
### **Desafio: O Labirinto Inteligente**  

**Objetivo:**  
Implemente o algoritmo A* para encontrar o caminho mais curto em um labirinto 2D de um ponto inicial até um destino.  

**Regras:**  
1. O labirinto é representado por uma matriz $N \times M$, onde:  
   - `0` representa uma célula vazia (onde se pode caminhar).  
   - `1` representa uma parede (bloqueio).  
   - `S` representa o ponto de início.  
   - `D` representa o destino.  

2. O movimento é permitido apenas nas direções **cima, baixo, esquerda e direita** (não são permitidos movimentos diagonais).  

3. O algoritmo deve encontrar o caminho mais curto usando o **algoritmo A*** com a heurística de **distância de Manhattan**.  

4. Se não houver caminho possível, a função deve retornar uma indicação disso.  

---

### **Exemplo de Entrada:**  
```python
labirinto = [
    ['S',  0 ,  1 ,  0 ,  0 ],
    [ 0 ,  1 ,  0 ,  1 ,  0 ],
    [ 0 ,  1 ,  0 ,  1 , 'D'],
    [ 0 ,  0 ,  0 ,  1 ,  0 ]
]
```

### **Exemplo de Saída:**  
```plaintext
Caminho encontrado: [(0,0), (1,0), (2,0), (3,0), (3,1), (3,2), (2,2), (1,2), (0,3), (0,4), (1,4), (2,4)]
```

**Dicas:**  
- Use uma **fila de prioridade** para armazenar os nós a serem explorados.  
- A **função heurística** pode ser a distância de Manhattan:  
  $$
  h(n) = |x_{atual} - x_{destino}| + |y_{atual} - y_{destino}|
  $$
- O custo real do caminho pode ser armazenado em um dicionário para cada nó.  
- O caminho final pode ser reconstruído armazenando os **nós pais** de cada posição explorada.  


[Resposta (sem implementação)](./r_desafio_2.md)