
## **Desafio 4: Escalonamento Inteligente de Tarefas em um Supercomputador**  

**Cenário:**  
Um centro de pesquisa precisa executar **N tarefas** em um supercomputador. Cada tarefa tem um **tempo de execução estimado** e precisa ser alocada a um dos **M processadores** disponíveis. O objetivo é minimizar o **tempo total de execução** e garantir um balanceamento eficiente da carga de trabalho.  

**Objetivo:**  
Desenvolver um algoritmo de **busca heurística** que distribua as tarefas entre os processadores de forma otimizada, minimizando o tempo total de execução.  

### **Regras:**  
1. Cada tarefa tem um **tempo estimado** de execução.  
2. Cada processador pode executar apenas **uma tarefa por vez**, mas novas tarefas podem começar assim que ele terminar uma.  
3. O objetivo é minimizar o **makespan** (tempo total de execução).  
4. O algoritmo deve utilizar **A*** para encontrar uma alocação eficiente.  
5. O programa deve exibir a **distribuição das tarefas** e o tempo final de conclusão.  

### **Exemplo de Entrada:**  
```python
tarefas = [
    {"id": "T1", "tempo": 10},
    {"id": "T2", "tempo": 20},
    {"id": "T3", "tempo": 15},
    {"id": "T4", "tempo": 30}
]

processadores = [
    {"id": "P1"},
    {"id": "P2"}
]
```

### **Saída esperada:**  
```plaintext
Distribuição de tarefas otimizada:
- P1 executa T1 (0s - 10s), T3 (10s - 25s)
- P2 executa T2 (0s - 20s), T4 (20s - 50s)
Tempo total de execução: 50s
```

