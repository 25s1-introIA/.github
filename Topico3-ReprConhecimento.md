# **Representação do Conhecimento em Inteligência Artificial** 

## 1a aula

A representação do conhecimento é um dos pilares fundamentais da Inteligência Artificial (IA), pois influencia diretamente a capacidade de uma máquina em processar informações e tomar decisões. O conhecimento pode ser representado de diversas formas, cada uma com suas vantagens e desvantagens, dependendo do tipo de problema a ser resolvido.

### Principais Formas de Representação do Conhecimento

1. [**Lógica Proposicional e de Primeira Ordem**](./Topico3-Logica1aOrdem.md): Utilizada para representar fatos e regras do mundo de maneira formal, permitindo inferências rigorosas por meio de sistemas de dedução.
   - Exemplo de representação: "Se chove, então o solo fica molhado" (Chove → SoloMolhado).
   
2. [**Redes Semânticas**](./Topico3-RedesSemanticas.md): Modelam relações entre conceitos por meio de grafos, onde nós representam conceitos e arestas representam relações entre eles.

3. [**Frames e Scripts**](./Topico3-Frames.md): Estruturas que organizam informações sobre conceitos e eventos de maneira hierárquica.

4. [**Redes Bayesianas**](./Topico3-RedesBayesianas.md): Modelam conhecimento incerto e probabilístico através de um grafo acíclico dirigido, onde cada nó representa uma variável aleatória e as arestas representam dependências condicionais.

5. [**Ontologias**](./Topico3-Ontologias.md): Representação formal do conhecimento em domínios específicos, permitindo a inferência automática de novas informações.

---
# Desafio

[Clique aqui](./Topico3-Desafio6.md)


---

## 2a aula

# **Raciocínio Probabilístico Temporal**

O raciocínio probabilístico temporal é uma abordagem fundamental para modelar sistemas dinâmicos que evoluem ao longo do tempo sob incerteza. Ele é amplamente utilizado em aplicações como previsão de séries temporais, reconhecimento de padrões e controle de sistemas autônomos.

### Principais Modelos de Raciocínio Probabilístico Temporal

1. [**Modelos Ocultos de Markov (HMM - Hidden Markov Models)**](./Topico3-HMM.md):
   - Modelam sistemas dinâmicos onde estados latentes influenciam as observações.
   - Aplicados em reconhecimento de fala e análise de sequências biológicas.
   
2. [**Redes Bayesianas Dinâmicas (DBN - Dynamic Bayesian Networks)**](./Topico3-DBN.md):
   - Extensão das Redes Bayesianas para modelar dependências temporais.
   - Utilizadas em sistemas de navegação autônoma e previsão de eventos.

3. [**Processos de Decisão de Markov (MDP - Markov Decision Processes)**](./Topico3-MDP.md):
   - Modelam a interação entre agentes e ambientes dinâmicos para otimização de decisões.
   - Utilizados em robótica e inteligência artificial aplicada a jogos.

4. [**Processos de Kalman**](./Topico3-Kalman.md):
   - Utilizados para filtrar ruído em sistemas dinâmicos e prever estados futuros.
   - Aplicados em rastreamento de objetos e controle de veículos autônomos.

---

**Exercícios Práticos**

1. **Exercício sobre Redes Bayesianas**
   - Considere um problema de diagnóstico médico com as seguintes variáveis:
     - "Doença" (D) pode ser verdadeira (T) ou falsa (F).
     - "Teste Positivo" (T+) depende de D.
     - "Sintoma" (S) também depende de D.
   - Construa uma Rede Bayesiana com essas variáveis e calcule P(D=T | T+=T, S=T).

2. **Modelagem com HMM**
   - Implemente um modelo oculto de Markov para detectar padrões de atividade de um usuário com base em sensores de um smartphone.

3. **Decisão com MDP**
   - Modele um problema de navegação de um robô autônomo em um labirinto usando um Processo de Decisão de Markov.



[Retornar](./Topico3-ReprConhecimento.md)