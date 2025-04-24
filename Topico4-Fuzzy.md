
# Lógica Fuzzy  
### Engenharia de Software - 5º Período

---

## Nesta aula  
- Introdução à Lógica Fuzzy  
- O que é?  
- Aplicações  
- Vantagens & Desvantagens  
- Arquitetura  
- Prática  
- Atividade  

---

## O que é Lógica Fuzzy?  
- Método de raciocínio que se assemelha ao raciocínio humano.  
- Imita a tomada de decisão humana considerando possibilidades intermediárias entre SIM e NÃO.  
- Lida com informações imprecisas ou incertas.  
- Representa imprecisão e incerteza na tomada de decisões.

---

## Além do Verdadeiro (V) e Falso (F)  
- O conceito binário é restritivo.  
- Existem "tons de cinza" entre verdadeiro e falso.  
- A lógica fuzzy permite variáveis com qualquer número real entre 0 e 1.  

---

## Aplicações  
- Controle de altitude de espaçonaves e satélites.  
- Controle de velocidade e tráfego em veículos.  
- Sistemas de apoio à decisão em grandes empresas.  
- Controle de pH, secagem e destilação química na indústria.
- Processamento de linguagem natural.  
- Aplicações em Inteligência Artificial.  
- Sistemas especialistas.  
- Combinada com Redes Neurais para decisões mais rápidas.  
- Dados agregados são transformados em verdades parciais (conjuntos fuzzy).

---

## Vantagens  
- Funciona com entradas imprecisas, distorcidas ou ruidosas.  
- Fácil construção e compreensão.  
- Baseada na teoria dos conjuntos.  
- Eficiente para problemas complexos.  
- Algoritmos exigem pouca memória.  

---

## Desvantagens  
- Múltiplas abordagens levam à ambiguidade.  
- Falta de sistematização para resolver problemas.  
- Difícil provar características matemáticas.  
- Precisão pode ser comprometida.  

---

## Arquitetura  

### Regras  
- Conjunto de regras SE-ENTÃO fornecidas por especialistas.  
- Desenvolvimentos recentes reduzem número de regras.  

### Fuzzificação  
- Converte entradas nítidas (sensores) em conjuntos fuzzy.  
- Ex.: temperatura, pressão, rpm.  

### Motor de Inferência  
- Verifica correspondência das entradas com as regras.  
- Combina regras disparadas para gerar ações de controle.  

### Defuzzificação  
- Converte conjuntos fuzzy em valores crisp.  
- Vários métodos disponíveis para minimizar erros.

---

## Crisp vs Fuzzy  

### Funções de Pertencimento  
Tipos de fuzzificadores:  
- Singleton  
- Gaussiano  
- Trapezoidal ou Triangular  

---

## Exemplos  
- União  
- Intersecção  
- Diferença  


---

## Conclusão  
- Extremamente flexível  
- Aplicações em muitos domínios  
- Simples de implementar  

---

## Demonstração dos conceitos

🔗 [https://tinyurl.com/fuzzycolab](./colabs/Fuzzy.ipynb)