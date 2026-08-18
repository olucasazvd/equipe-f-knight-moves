---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section {
    font-size: 26px;
  }
  section.title {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  section.title h1 {
    font-size: 56px;
    margin-bottom: 0;
  }
  section.title h3 {
    font-weight: normal;
    color: #555;
  }
  code {
    background: #f4f4f4;
  }
  blockquote {
    border-left: 6px solid #888;
    padding-left: 1em;
    color: #444;
    font-size: 22px;
  }
---

<!-- _class: title -->

# Knight Moves

### Marco 1 — Modelagem

**Lucas Azevedo**
**Laura Saraiva**

---

## Marco 1 — Modelagem

> - enunciado; entrada; saída; restrições;
> - vértices; arestas; tipo do grafo;
> - instância pequena; resultado esperado;
> - hipótese inicial de solução.

---

## Enunciado

Peter está fazendo uma pesquisa sobre o **Problema do Cavalo Viajante (TKP)**, no qual se deve encontrar o menor percurso fechado de movimentos de cavalo que visite cada casa de um conjunto de *n* casas de um tabuleiro de xadrez exatamente uma vez.

Ele acredita que a parte mais difícil é determinar o menor número de movimentos de cavalo entre duas casas dadas — feito isso, encontrar o percurso seria fácil.

É claro que é o contrário. Portanto, o objetivo é escrever um programa que resolva a parte "difícil": dadas duas casas **a** e **b**, determinar o número de movimentos de cavalo em uma rota de menor distância entre elas.

---

## Entrada e Saída

**Entrada**

Duas casas, cada uma composta pelo par coluna e linha, onde a coluna é uma letra entre `a`–`h` e a linha um número entre `1`–`8`.

```
e2 e4
```

**Saída**

Um valor inteiro definindo o mínimo de movimentos necessários para ir da casa de origem até a casa de destino.

```
2
```

---

## Restrições

- Tabuleiro fixo (8x8) → |V| = 64
- Grafo simples (sem loops, sem arestas paralelas) e conexo (existe caminho entre quaisquer dois vértices, já que o grafo de movimentos do cavalo em um tabuleiro 8×8 é conexo)
- Grau máximo Δ(G) = 8; grau mínimo δ(G) = 2 (casas de canto)

---

## Vértices e Arestas

**Vértices**
Cada uma das 64 casas do tabuleiro, identificadas por `(col, lin)`.

**Arestas**
Os movimentos válidos entre duas casas. Cada casa tem, no máximo, 8 vizinhos distintos.

---

## Tipo de Grafo

- **Simples** — sem loops, sem arestas paralelas.
- **Não direcionado** — o movimento do cavalo é reversível: se u → v é válido, v → u também é.
- **Não ponderado** — todas as arestas têm peso implícito igual a 1 (cada movimento conta como uma unidade de distância).

**Lista de Adjacência**

Representação do grafo: cada casa aponta para as casas alcançáveis por um movimento de cavalo.

```md
e4: d6, f6, c5, g5, c3, g3, d2, f2
d6: e4, f5
f6: e4, d5
```

---

## Instância Pequena (exemplo)

**Entrada:**
```
e2 e4
```

**Saída esperada:**
```
2
```

Um caminho mínimo possível: **e2 → d4 → e4** (2 movimentos / 2 arestas).

---

## Hipótese Inicial de Solução

Como o grafo é simples, não ponderado, e todas as arestas têm o mesmo "custo" (1 movimento), o problema se reduz a calcular a **distância** (número mínimo de arestas) entre dois vértices em um grafo não ponderado.

---

<!-- _class: title -->

# Obrigado!

**Lucas Azevedo**
**Laura Saraiva**