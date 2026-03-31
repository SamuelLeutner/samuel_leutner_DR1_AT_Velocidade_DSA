# Lista de Exercícios AT - Estruturas de Dados e Algoritmos

Este repositório contém a resolução integral do Assessment Test, com foco em instrumentação, medição de custo assintótico (Big O) e engenharia de estruturas dinâmicas. O projeto está modularizado para separar estruturas genéricas, algoritmos e domínios de aplicação.

1. **Busca em Estruturas Lineares e Impacto de Organização**
Implemente buscas clássicas e conecte o desempenho prático à organização em memória dos dados.
* Implemente `linear_search` e `binary_search` com contagem explícita de comparações.
* Crie cenários de teste variando escalas de dados e padrões (ordenado, reverso, aleatório).
* Projete uma estratégia de falha rápida (pre-condition check) para a busca binária.
* Reescreva a busca linear sobre uma lista encadeada mínima e compare os custos práticos.

2. **Ordenações Quadráticas com Instrumentação e Diagnóstico**
Implemente ordenações baseadas em comparações e quantifique os seus gargalos.
* Desenvolva `bubble_sort`, `selection_sort` e `insertion_sort` contabilizando cópias e trocas.
* Avalie os algoritmos em 4 distribuições de entrada, incluindo o caso "quase ordenado".
* Identifique e justifique qual algoritmo se beneficia da entrada parcialmente ordenada.
* Integre os dados em uma Árvore Binária de Busca (BST) e valide os invariantes via travessia in-order.

3. **Otimização Orientada a Big O com Requisitos de Desempenho**
Refatore implementações ingênuas reduzindo as suas complexidades de tempo e espaço.
* Reescreva uma deduplicação ingênua O(N²) para uma abordagem O(N) mantendo a ordem relativa.
* Implemente a extração dos *k-ésimos* menores elementos via ordenação total e via `QuickSelect`.
* Construa uma variante de seleção de elementos suportada por travessia controlada em BST.
* Apresente evidências que justifiquem as melhorias e demonstrem os piores casos teóricos.

4. **Hashtable com Colisões e Encadeamento por Lista**
Construa um dicionário do zero com tratamento robusto para falhas de hashing.
* Implemente uma `HashTableChained` suportando `put`, `get`, `delete` e `__len__`.
* Utilize listas encadeadas independentes em cada *bucket* para a resolução de colisões.
* Desenvolva o gatilho de *rehash* (redimensionamento automático) baseado no fator de carga.
* Provoque um cenário adversarial e documente a degradação assintótica sofrida pela estrutura.

5. **Pilha e Fila com Invariantes e Integração com Árvore de Expressão**
Projete filas e pilhas rigorosas e aplique-as na manipulação de expressões sintáticas.
* Implemente classes `Stack` e `Queue` baseadas em arrays de capacidade fixa (com *wraparound*).
* Levante exceções customizadas para as operações de *overflow* e *underflow*.
* Construa uma árvore de expressão a partir de uma string em notação pós-fixa usando a Pilha.
* Trate entradas matemáticas inválidas de forma antecipada, prevenindo a corrupção da árvore.

6. **Simulador de Eventos com Múltiplas Filas e Índice em Árvore**
Orquestre fluxos assíncronos integrando filas transacionais a um índice de busca estruturado.
* Construa um simulador com quatro filas distintas (A, B, C e D) controladas por logs temporais.
* Trate instabilidades na fila de atendimento garantindo a resiliência contínua da simulação.
* Indexe as transações e clientes concluídos através de uma Árvore Binária de Busca (BST).
* Discuta o isolamento entre o custo das operações transacionais e das consultas posteriores.

7. **Recursão para Navegação e Representação em Árvore de Diretórios**
Modele recursividade segura sobre árvores hierárquicas genéricas de profundidade variável.
* Desenvolva uma estrutura de dados de diretórios em memória com nós polimórficos.
* Escreva um método `walk(root)` para a extração do mapeamento de caminhos em pré-ordem.
* Integre uma política de deleção atômica e em cascata para pastas com filhos.
* Gerencie o rastreamento do diretório atual aplicando uma lista encadeada como *Path Stack*.

8. **Programação Dinâmica e Memoization com Hashtable**
Quebre a complexidade exponencial aplicando *caching* estruturado sobre problemas sobrepostos.
* Implemente a otimização de troco (moedas) via recursão pura e evidencie o custo O(C^A).
* Injete a estrutura `HashTableChained` construída no Ex 4 como motor de *memoization*.
* Molde e imprima uma árvore de subproblemas registrando as transições e podas do algoritmo.
* Demonstre de forma quantitativa a redução vertiginosa no volume das chamadas à pilha recursiva.

9. **QuickSort e QuickSelect: Variante em Lista Encadeada**
Adapte os mecanismos de partição ao paradigma estrito e sem índice das listas vinculadas.
* Desenvolva um `quicksort_hibrido` que delegue partições curtas ao algoritmo de Insertion Sort.
* Implemente a extração posicional `quickselect` isolando os custos inerentes à busca.
* Reescreva a função `partition` central para que ela opere unicamente via ponteiros (`next`).
* Prove a manutenção da estabilidade do algoritmo sob o regime limitado da *Singly Linked List*.

10. **Lista Encadeada com Operações Completas e Análise de Eficiência**
Forneça uma suíte completa de APIs para manipulação arbitrária de elementos em uma LSE.
* Crie os métodos transacionais da estrutura: `insert`, `search`, `delete` estáticos e orientados por índice.
* Blinde a implementação injetando validações estritas de tamanho e tratamento aos erros locais.
* Tome uma decisão projetual clara quanto ao rastreamento da cauda (`tail`) e suas ramificações.
* Conduza experimentos empíricos que ilustrem as deficiências de acesso do Big O linear prático.

11. **Lista Duplamente Encadeada e Deque com Especificação Rigorosa**
Expanda o escopo dos nós duplos implementando um Deque operando confiavelmente em tempo O(1).
* Construa os mecanismos de transição em `DoublyLinkedList` sincronizando os campos `prev` e `next`.
* Empacote a LDE exposta através dos protocolos rigorosos das portas de um `Deque`.
* Escreva baterias agressivas de testes unificando estresses mecânicos em ambas as direções (esq/dir).
* Confirme após cada mutação que o fluxo estrutural de contagem e os ponteiros se encontram intactos.

1.  **Motor de Indexação e Consulta com Estruturas Combinadas**
Construa um buscador textual agregando e provando o valor das estruturas abstratas desenvolvidas.
* Processe documentos textuais e componha um índice invertido consumindo a sua `HashTableChained`.
* Integre vocabulários e listas nativas orquestrando consultas sob a regência da `SinglyLinkedList`.
* Recupere desvios gramaticais de usuários instanciando uma matriz de *Edit Distance* amparada por Programação Dinâmica.
* Ranqueie e entregue os acertos por relevância através do `quicksort_hibrido`.
