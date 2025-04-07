
# 🎓 **Atividade Prática: Ontologia para Manutenção Preditiva com Python**


## Proposta: Criação e uso de uma ontologia para manutenção preditiva em ambientes industriais

### Objetivo
Desenvolver uma ontologia para padronizar e integrar informações relacionadas à manutenção preditiva de máquinas e equipamentos industriais, com foco em detecção precoce de falhas, gestão do ciclo de vida dos ativos e automação de diagnósticos.

### Justificativa
Em ambientes industriais, os dados sobre funcionamento de máquinas vêm de diversas fontes (sensores, históricos de manutenção, manuais, relatórios técnicos). Muitas vezes, esses dados são armazenados de forma isolada e sem semântica clara. Uma ontologia permite unificar e estruturar esse conhecimento, possibilitando:

- Diagnóstico automático baseado em sintomas e histórico.

- Integração entre sistemas de monitoramento, ERP e equipes de manutenção.

- Suporte à tomada de decisão (ex: priorização de ordens de serviço).

- Facilitação de treinamentos e transferência de conhecimento técnico.

### Exemplos de uso
 - Mapeamento de falhas conhecidas e suas causas prováveis.

- Relacionamento entre condições operacionais (temperatura, vibração, pressão) e padrões de desgaste.

- Associação de peças e componentes com planos de manutenção e fornecedores.

- Integração semântica com gêmeos digitais da planta industrial.

---

### 🧩 Atividade em Etapas

#### **Etapa 1 – Introdução Conceitual**
**Tarefa:** Estudar os conceitos de ontologia, RDF, OWL, triplas e raciocínio semântico.  
**Material de apoio:** Slides, artigos e tutoriais indicados pelo professor.

---

#### **Etapa 2 – Criação da Ontologia Base**
**Tarefa:** Usar Python para criar uma ontologia com as seguintes classes:

- Equipamento  
- Sensor  
- Componente  
- Falha  
- Manutencao  
- Procedimento  
- Responsavel  
- Alerta  

**Propriedades sugeridas:**
- `possuiComponente`, `mede`, `detectaFalha`, `generaAlerta`, `executaProcedimento`, `associadoA`


---

#### **Etapa 3 – Modelagem de Casos de Uso**
**Tarefa:** Criar instâncias representando um caso real ou fictício de manutenção preditiva.

**Exemplo sugerido (pode ser adaptado):**
- Motor com rolamento
- Sensor de vibração detecta falha
- Técnico realiza troca


---

#### **Etapa 4 – Desafios Semânticos** *(aluno escolhe ao menos dois)*
**Desafios sugeridos:**
1. Adicionar propriedades de dados (`frequenciaDeLeitura`, `dataFalha`, etc.)
2. Criar novos tipos de falha e causas
3. Simular alertas de sensores em tempo real



**Entregável:** Código Python (`.pynb`) que gera e salva a ontologia em `.owl`

