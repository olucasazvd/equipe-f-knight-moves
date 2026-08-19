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

### Marco 2 — Representação Computacional

**Lucas Azevedo**
**Laura Saraiva**

---

## Marco 2 — Representação Computacional

> - matriz, lista de adjacência ou representação implícita;
> - leitura da entrada; construção do grafo;
> - medidas estruturais pertinentes da Unidade I;
> - validação da representação com a instância pequena.

---

## Representação do Grafo

**Escolha:** Representação Implícita (geração sob demanda).

- Tabuleiro com dimensão fixa $8 \times 8 \rightarrow |V| = 64$.
- Matriz de Adjacência $64 \times 64$ desperdiçaria memória com zeros (grafo esparso).
- Como as regras de movimentação em "L" são puramente matemáticas e invariantes, os vizinhos válidos são calculados em tempo de execução a partir da posição atual.

---

## Leitura da Entrada

Mapeamento da notação algébrica do xadrez para matriz de coordenadas $0$-indexadas $(X, Y)$:

- **Coluna:** `a`–`h` $\rightarrow X \in \{0, 1, \dots, 7\}$
- **Linha:** `1`–`8` $\rightarrow Y \in \{0, 1, \dots, 7\}$

Exemplos:
'a1'  ->  (0, 0)
'e4'  ->  (4, 3)
'h8'  ->  (7, 7)


---

## Construção do Grafo

A partir de um vértice $(x, y)$, testamos os 8 deltas de movimento do cavalo:

$$(\pm 1, \pm 2) \quad \text{e} \quad (\pm 2, \pm 1)$$

**Filtro de borda (validação de aresta):**
Uma aresta para $(x', y')$ só é construída se:

$$0 \le x' < 8 \quad \text{e} \quad 0 \le y' < 8$$

---

## Medidas Estruturais (Unidade I)

- **Ordem ($|V|$):** 64 vértices.
- **Tamanho ($|E|$):** 168 arestas.
- **Grau Mínimo ($\delta$):** 2 (casas dos 4 cantos: `a1`, `a8`, `h1`, `h8`).
- **Grau Máximo ($\Delta$):** 8 (16 casas centrais do tabuleiro).
- **Grau Médio ($\bar{d}$):** $5{,}25$ ($2 \cdot |E| / |V| = 336 / 64$).
- **Densidade ($D$):** $\approx 0{,}0833$ (8,33%).

*A baixa densidade confirma matematicamente que o grafo é esparso.*

---

## Validação da Representação

**Instância pequena:** `a1` $\rightarrow$ `b2` (Mapeado: `(0, 0)` $\rightarrow$ `(1, 1)`).

Aplicando a geração de vizinhos a partir da origem `(0, 0)`:
- 6 movimentações são descartadas pelo filtro de borda ($x' < 0$ ou $y' < 0$).
- **Vizinhos gerados:** `(1, 2)` (`b3`) e `(2, 1)` (`c2`).

**Conclusão:** O grau gerado para `a1` é 2 (valida $\delta = 2$). Como o destino `b2` não está entre os vizinhos diretos, o modelo confirma que a distância é $> 1$.

---

<!-- _class: title -->

# Obrigado!

**Lucas Azevedo**
**Laura Saraiva**
