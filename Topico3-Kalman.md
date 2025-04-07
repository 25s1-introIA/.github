
**Processos de Kalman**

Os Processos de Kalman são utilizados para filtrar ruído em sistemas dinâmicos e prever estados futuros. Eles são amplamente aplicados em rastreamento de objetos, controle de veículos autônomos e fusão de sensores, permitindo estimativas precisas mesmo na presença de incerteza.

---

## **1. Conceitos Fundamentais**

### **1.1 Definição Formal**
O Filtro de Kalman é um estimador recursivo baseado em dois principais passos:
- **Predição**: Estima o estado futuro do sistema com base no modelo de transição.
- **Atualização**: Ajusta a estimativa com base em novas medições, ponderando a incerteza da predição e da medição.

O modelo matemático é definido por:
- **Estado $x_k$**: Representa a variável oculta do sistema no instante $k$.
- **Matriz de transição $F_k$**: Define a relação entre o estado atual e o próximo.
- **Controle $u_k$ e matriz $B_k$**: (Opcional) Considera ações externas que afetam o sistema.
- **Medição $z_k$**: Valor observado influenciado pelo estado real.
- **Matriz de observação $H_k$**: Relaciona o estado verdadeiro com as medições.
- **Ruídos de processo $Q_k$ e de medição $R_k$**: Modelam incertezas nos estados e medições.

### **1.2 Propriedades**
- **É ótimo para sistemas lineares e gaussianos**.
- **Atualiza o estado em tempo real com eficiência computacional**.
- **Combina medições ruidosas para obter estimativas mais precisas**.

---

## **2. Aplicações**

### **2.1 Rastreamento de Objetos**
O filtro de Kalman é utilizado para rastrear a posição de objetos em movimento, mesmo quando as medições são imprecisas devido a ruídos.

#### **Exemplo Prático**
Um sistema de radar pode usar o filtro de Kalman para estimar a posição e velocidade de uma aeronave, corrigindo imprecisões nas medições do sensor.

### **2.2 Controle de Veículos Autônomos**
Veículos autônomos utilizam o filtro de Kalman para estimar sua posição real ao integrar dados de GPS, sensores inerciais e câmeras.

#### **Exemplo Prático**
Um carro autônomo pode corrigir sua posição utilizando o filtro de Kalman para combinar leituras de GPS e odometria, garantindo uma navegação mais precisa.

---

## **3. Exercícios**

### **3.1 Exercício 1 - Implementação de um Filtro de Kalman Simples**
Implemente um Filtro de Kalman em Python para estimar a posição de um objeto em um espaço unidimensional.
1. Defina os estados, medições e ruídos.
2. Complete a atualização recursiva do filtro.
3. Teste com medições simuladas.

#### Código inicial:
```python
import numpy as np

class KalmanFilter:
    def __init__(self, x0, P0, F, H, Q, R):
        self.x = x0  # Estado inicial
        self.P = P0  # Covariância inicial
        self.F = F  # Matriz de transição
        self.H = H  # Matriz de observação
        self.Q = Q  # Ruído do processo
        self.R = R  # Ruído da medição
    
    def predict(self):
        self.x = self.F @ self.x  # Predição do estado
        self.P = self.F @ self.P @ self.F.T + self.Q  # Predição da covariância
    
    def update(self, z):
        y = z - self.H @ self.x  # Inovação
        S = self.H @ self.P @ self.H.T + self.R  # Covariância da inovação
        K = self.P @ self.H.T @ np.linalg.inv(S)  # Ganho de Kalman
        self.x = self.x + K @ y  # Atualização do estado
        self.P = (np.eye(len(self.P)) - K @ self.H) @ self.P  # Atualização da covariância
    
# TODO: Completar o código para gerar medições ruidosas e testar o filtro
print("Filtro de Kalman configurado. Complete a implementação para testar com dados simulados.")
```

### **3.2 Exercício 2 - Aplicação ao Rastreamento de um Objeto**
Expanda a implementação acima para estimar tanto a posição quanto a velocidade de um objeto.

---

## **4. Respostas e Explicações**

### **4.1 Solução para Exercício 1**
O código abaixo adiciona a geração de medições ruidosas e a aplicação do Filtro de Kalman.
```python
# Definição de parâmetros
x0 = np.array([[0]])  # Estado inicial (posição)
P0 = np.array([[1]])  # Incerteza inicial
F = np.array([[1]])  # Modelo de transição (posição constante)
H = np.array([[1]])  # Medição direta da posição
Q = np.array([[0.01]])  # Ruído do processo
R = np.array([[0.1]])  # Ruído da medição

kf = KalmanFilter(x0, P0, F, H, Q, R)

# Simulação de medições ruidosas
true_positions = np.linspace(0, 10, 20)
measurements = true_positions + np.random.normal(0, np.sqrt(R[0,0]), size=len(true_positions))

estimates = []
for z in measurements:
    kf.predict()
    kf.update(np.array([[z]]))
    estimates.append(kf.x[0,0])

print("Posições estimadas:", estimates)
```
Explicação:
- O objeto se move em um eixo 1D.
- O filtro de Kalman corrige as medições ruidosas para obter estimativas mais precisas.

### **4.2 Solução para Exercício 2**
Agora, expandimos o filtro para estimar também a velocidade do objeto.
```python
# Estado inicial (posição e velocidade)
x0 = np.array([[0], [0]])
P0 = np.eye(2) * 1  # Incerteza inicial
F = np.array([[1, 1], [0, 1]])  # Modelo de movimento uniforme
H = np.array([[1, 0]])  # Medição apenas da posição
Q = np.eye(2) * 0.01  # Ruído do processo
R = np.array([[0.1]])  # Ruído da medição

kf = KalmanFilter(x0, P0, F, H, Q, R)

# Simulação
true_positions = np.linspace(0, 10, 20)
true_velocities = np.full_like(true_positions, 0.5)  # Velocidade constante
measurements = true_positions + np.random.normal(0, np.sqrt(R[0,0]), size=len(true_positions))

estimates = []
for z in measurements:
    kf.predict()
    kf.update(np.array([[z]]))
    estimates.append(kf.x.flatten())

print("Posição e velocidade estimadas:", estimates)
```
Explicação:
- Agora o estado inclui posição e velocidade.
- A matriz de transição considera movimento uniforme.
- O filtro de Kalman permite estimar ambos os valores ao longo do tempo.

---

Os Processos de Kalman são essenciais para aplicações onde medições ruidosas devem ser filtradas e previsões devem ser feitas com precisão, sendo cruciais para rastreamento e controle em sistemas dinâmicos.





[Retornar](./Topico3-ReprConhecimento.md)