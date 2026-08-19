# Marco 2 — Representação Computacional

**Problema:** [beecrowd 1100 — Knight Moves](https://www.beecrowd.com.br/judge/pt/problems/view/1100)
**Linguagem planejada:** Python

## 1. Representação do Grafo

Usaremos a **Representação Implícita**, realizando a geração das conexões sob demanda durante a execução.

Como o tabuleiro é fixo (`8 × 8 = 64` vértices), criar uma matriz de adjacência `64 × 64` gastaria memória desnecessariamente com valores `0`, já que o grafo é esparso.

Além disso, como as regras de movimentação do cavalo são fixas e puramente matemáticas, não é necessário armazenar toda a estrutura de adjacência na memória antes de executar o algoritmo. Os vizinhos válidos podem ser calculados diretamente a partir da posição atual do cavalo.

---

## 2. Entrada e Construção do Grafo

### Mapeamento de Entrada

A notação do xadrez será convertida para um sistema de coordenadas **0-indexado `(X, Y)`**:

* **Coluna (`a` a `h`)** → Índice `X` de `0` a `7`.
* **Linha (`1` a `8`)** → Índice `Y` de `0` a `7`.

**Exemplo:**

`a1 → (0, 0)`

`h8 → (7, 7)`

### Geração de Arestas

A partir de uma posição `(x, y)`, aplicamos os **8 deslocamentos possíveis do cavalo**:

```text
(±1, ±2)
(±2, ±1)
```

Uma aresta para uma nova posição `(x', y')` só existe se a casa estiver dentro dos limites do tabuleiro:

```text
0 ≤ x' < 8
0 ≤ y' < 8
```

Assim, durante a execução, são gerados apenas os movimentos válidos para a posição atual.

---

## 3. Medidas Estruturais (Unidade I)

O tabuleiro é modelado como um **grafo não direcionado e não ponderado**.

| Medida          |       Valor |
| --------------- | ----------: |
| Ordem `\|V\|`   | 64 vértices |
| Tamanho `\|E\|` | 168 arestas |
| Grau mínimo `δ` |           2 |
| Grau máximo `Δ` |           8 |
| Grau médio      |        5,25 |
| Densidade       |     ≈ 8,33% |

### Cálculos

**Grau médio:**

```text
2 × 168 / 64 = 5,25
```

**Densidade:**

```text
D = (2 × 168) / (64 × 63)
D ≈ 0,0833
```

Ou seja, aproximadamente **8,33%** das possíveis conexões estão presentes.

A baixa densidade confirma matematicamente que o grafo é **esparso**, justificando a utilização da representação implícita em vez de uma matriz de adjacência.

---

## 4. Validação da Representação com Instância Pequena

### Origem e Destino

* **Origem:** `a1 → (0, 0)`
* **Destino:** `b2 → (1, 1)`

Aplicando as 8 regras de deslocamento do cavalo a partir da origem `(0, 0)`:

```text
(±1, ±2)
(±2, ±1)
```

Seis das opções geram coordenadas negativas e, portanto, são descartadas pelo filtro de borda.

Restam apenas **2 vizinhos válidos**:

* `(1, 2)` → `b3`
* `(2, 1)` → `c2`

Portanto, o grau obtido para a casa `a1` é:

```text
grau(a1) = 2
```

Esse resultado coincide exatamente com o **grau mínimo teórico dos cantos do tabuleiro**.

Além disso, a casa `b2 → (1, 1)` não aparece entre os vizinhos diretos de `a1`. Isso confirma que não existe uma aresta direta entre essas duas posições e que, portanto, a menor distância entre elas é maior que `1`.

Dessa forma, a instância pequena valida tanto a **representação implícita** quanto a **regra de geração das arestas** utilizada no modelo.
