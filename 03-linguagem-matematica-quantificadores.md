---
layout: page
title: "3. Quantificadores"
nav_order: 3
---
# 3. Linguagem Matematica: Conjuntos e Quantificadores

## Resumo

### Representacao de conjuntos

**Por extensao (listando elementos):**
- A = {1, 2, 3, 4, 5}
- B = {a, e, i, o, u}

**Por compreensao (descrevendo propriedade):**
- A = {x ∈ N : x ≤ 5} = {0, 1, 2, 3, 4, 5}
- B = {x ∈ Z : x² < 10} = {-3, -2, -1, 0, 1, 2, 3}

**Notacao de construcao (builder notation):**
- {expressao : condicao} ou {expressao | condicao}
- {2n : n ∈ N} = {0, 2, 4, 6, ...} (pares)
- {n² : n ∈ Z, 1 ≤ n ≤ 5} = {1, 4, 9, 16, 25}

### Conjuntos especiais
- ∅ ou {} — conjunto vazio
- N = {0, 1, 2, 3, ...} — naturais (convencao pode variar: alguns excluem 0)
- Z = {..., -2, -1, 0, 1, 2, ...} — inteiros
- Q — racionais
- R — reais

### Operacoes com conjuntos
- **Uniao:** A ∪ B = {x : x ∈ A ou x ∈ B}
- **Intersecao:** A ∩ B = {x : x ∈ A e x ∈ B}
- **Diferenca:** A \ B = {x : x ∈ A e x ∉ B}
- **Complemento:** Aᶜ = {x ∈ U : x ∉ A} (relativo ao universo U)
- **Produto cartesiano:** A × B = {(a, b) : a ∈ A e b ∈ B}

### Quantificadores

**Quantificador universal — ∀ ("para todo"):**
- ∀x ∈ A, P(x) significa: "para todo x pertencente a A, P(x) e verdadeira"
- E verdadeiro quando P(x) vale para TODOS os elementos do dominio
- Para refutar: basta UM contra-exemplo

**Quantificador existencial — ∃ ("existe"):**
- ∃x ∈ A, P(x) significa: "existe pelo menos um x em A tal que P(x) e verdadeira"
- E verdadeiro quando P(x) vale para PELO MENOS UM elemento
- Para refutar: mostrar que NENHUM elemento satisfaz

**Quantificador existencial unico — ∃! ("existe um unico"):**
- ∃!x ∈ A, P(x) significa: "existe exatamente um x em A tal que P(x)"

### Negacao de quantificadores (De Morgan generalizado)
Essa e uma das regras mais importantes:
- **¬(∀x, P(x)) ≡ ∃x, ¬P(x)**
  "Nem todo x satisfaz P" = "existe algum x que nao satisfaz P"
- **¬(∃x, P(x)) ≡ ∀x, ¬P(x)**
  "Nao existe x que satisfaz P" = "todo x nao satisfaz P"

**Exemplo:**
- "Nem todo aluno passou" ≡ "Existe algum aluno que nao passou"
- "Nao existe numero par primo maior que 2" ≡ "Todo numero par maior que 2 nao e primo"

### Quantificadores aninhados
A **ordem importa** quando os quantificadores sao diferentes:
- ∀x ∃y, P(x, y): "para cada x, existe algum y tal que..." (y pode depender de x)
- ∃y ∀x, P(x, y): "existe um y que funciona para todo x" (y e fixo)

**Exemplo com P(x,y) = "x + y = 0", dominio Z:**
- ∀x ∃y, x + y = 0 → **V** (para cada x, basta tomar y = -x)
- ∃y ∀x, x + y = 0 → **F** (nenhum y unico serve para todo x)

### Traduzindo linguagem natural para simbolos
| Portugues | Simbolos |
|---|---|
| "Todo natural e nao-negativo" | ∀n ∈ N, n ≥ 0 |
| "Existe um primo par" | ∃p ∈ {primos}, p e par |
| "Para todo epsilon > 0, existe delta > 0 tal que..." | ∀ε > 0, ∃δ > 0, ... |
| "Nenhum quadrado perfeito e negativo" | ∀n ∈ Z, n² ≥ 0 |

## Pontos-chave para a prova
- Saber negar proposicoes quantificadas (trocar ∀ por ∃ e negar o predicado)
- Entender que a ordem dos quantificadores importa
- Traduzir entre linguagem natural e simbolica (ida e volta)
- Notacao de conjuntos por compreensao

## Exercicio de fixacao
1. Negue formalmente: ∀x ∈ R, ∃y ∈ R, x + y > 0
2. Traduza para simbolos: "Para todo numero inteiro n, se n² e par entao n e par"
3. Verdadeiro ou falso? ∃x ∈ R, ∀y ∈ R, xy = y

> Respostas: 1- ∃x ∈ R, ∀y ∈ R, x + y ≤ 0. 2- ∀n ∈ Z, (n² par → n par). 3- V (x = 1).

## Referencias
- **Book of Proof** (Hammack), Cap. 1 (conjuntos) e Cap. 2 (logica/quantificadores) — https://www.people.vcu.edu/~rhammack/BookOfProof/
- **How to Prove It** (Velleman), Cap. 2 — excelente para quantificadores
- **Rosen**, Secoes 1.4-1.5 (predicados e quantificadores) e 2.1-2.2 (conjuntos)
- **MIT OCW 6.042J** — Predicate Logic — https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/
- **TrevTutor** - Quantifiers playlist (YouTube, EN)
- **Khan Academy** (PT) — https://pt.khanacademy.org/
