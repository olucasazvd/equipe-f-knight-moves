> #### Marco 1 - Modelagem
> 
> - enunciado; entrada; saída; restrições;
> - vértices; arestas; tipo do grafo;
> - instância pequena; resultado esperado;
> - hipótese inicial de solução.

#### Knight Moves

###### English
Peter is doing a research on the Traveling Knight Problem (TKP) where you have to find the shortest closed tour of knight moves that visits each square of a given set of n squares on a chessboard exactly once. He thinks that the most difficult part of the problem is determining the smallest number of knight moves between two given squares and that, once you have accomplished this, finding the tour would be easy.

Of course you know that it is vice versa. So you must offer him a program that solves the "difficult" part.

Your job is to write a program that takes two squares a and b as input and then determines the number of knight moves on a shortest route from a to b.

###### Português
Peter está fazendo uma pesquisa sobre o Problema do Cavalo Viajante (TKP), no qual você deve encontrar o menor percurso fechado de movimentos de cavalo que visite cada casa de um determinado conjunto de n casas de um tabuleiro de xadrez exatamente uma vez. Ele acredita que a parte mais difícil do problema é determinar o menor número de movimentos de cavalo entre duas casas dadas e que, uma vez que isso tenha sido feito, encontrar o percurso seria fácil.

É claro que você sabe que é o contrário. Portanto, você deve oferecer a ele um programa que resolva a parte “difícil”.

Sua tarefa é escrever um programa que receba como entrada duas casas a e b e, então, determine o número de mov2imentos de cavalo em uma rota de menor distância de a até b.

#### Entrada
Duas casas, cada uma composta pelo par coluna e linha, onde a coluna é definida por uma letra entre `<a - h>` e a linha definda por um número entre `<1 - 8>`. (e.g: e2 e4)

#### Saída
Um valor inteiro, definindo o mínimo de movimentos necessários para ir da casa de origem até a casa de destino. (e.g: 2)

#### Restrições
- Tabuleiro fixo (8x8) → |V| = 64
- Grafo simples (sem loops, sem arestas paralelas) e conexo (existe caminho entre quaisquer dois vértices, já que o grafo de movimentos do cavalo em um tabuleiro 8×8 é conexo)
- Grau máximo Δ(G) = 8; grau mínimo δ(G) = 2 (casas de canto)

#### Vértices 
Cada uma das 64 casas do tabuleiro, identificadas por `(col, lin)`.

#### Arestas
Os movimentos válidos entre duas casas. Cada casa tem, no máximo, 8 vizinhos distintos.

#### Tipo de Grafo 
  - **Simples**: sem loops, sem arestas paralelas.
  - **Não direcionado**: o movimento do cavalo é reversível — se u → v é válido, v → u também é.
  - **Não ponderado**: todas as arestas têm peso implícito igual a 1 (cada movimento conta como uma unidade de distância).


#### Instância pequena (exemplo)
 
**Entrada:**
```
e2 e4
```
 
**Saída esperada:**
```
2
```
 
Um caminho mínimo possível: e2 → d4 → e4 (2 movimentos / 2 arestas).

#### Hipótese inicial de solução
 
Como o grafo é simples, não ponderado, e todas as arestas têm o mesmo "custo" (1 movimento), o problema se reduz a calcular a distância (número mínimo de arestas) entre dois vértices em um grafo não ponderado.