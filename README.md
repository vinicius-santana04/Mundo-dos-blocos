# Planejamento no Mundo dos Blocos de Tamanho Variável

Este projeto explora a aplicação de diferentes metodologias de Inteligência Artificial para resolver o problema de planejamento do "mundo dos blocos", estendendo-o para incluir blocos de tamanhos heterogêneos e restrições espaciais.

O objetivo é demonstrar como o planejamento, um campo da IA que se concentra em encontrar sequências de ações para alcançar um objetivo, pode ser abordado usando o conceito de **Planejamento como Verificação de Modelo** (*Planning as Model Checking*).

---

### 1. O Modelo Clássico (STRIPS)

O problema clássico do mundo dos blocos serve como um exemplo canônico no estudo do planejamento automatizado. O modelo, tipicamente baseado em STRIPS (Stanford Research Institute Problem Solver), é altamente abstrato. O estado do mundo é representado por predicados lógicos como `on(Block, Object)` e `clear(Object)`. O operador de ação `move(Block, From, To)` define as transições de estado.

No entanto, este modelo é insuficiente para o nosso problema, pois não considera as dimensões físicas dos blocos ou as restrições espaciais.

---

### 2. O Modelo Estendido em Lógica de Primeira Ordem (Prolog)

Para superar as limitações do modelo clássico, foi desenvolvido um modelo estendido em Prolog que incorpora atributos físicos e restrições espaciais. O estado do mundo é descrito de forma mais rica, incluindo informações estáticas como a largura dos blocos (`size/2`) e a posição exata na grade da mesa (`pos/2`). Os operadores de planejamento são redefinidos para impor leis físicas, como a regra de estabilidade que impede que um bloco largo seja colocado sobre um mais estreito.

---

### 3. Planejamento como Verificação de Modelo (NuSMV)

O problema de encontrar um plano é reformulado como um problema de encontrar um caminho em um grafo de estados. Usando um verificador de modelos como o NuSMV, o problema de planejamento é traduzido em uma propriedade lógica a ser verificada. Se a propriedade `!EF (Goal)` (não existe um caminho para o objetivo) for falsa, o verificador gera um contra-exemplo. Este contra-exemplo é, na verdade, o plano de ações que leva ao estado final desejado.

---

### Equipe

* Vinícius Santana (vinicius.santana@icomp.ufam.edu.br)

---

Este projeto está hospedado em nosso repositório no GitHub.
