---
layout: page
title: "9. Principio da Boa Ordem"
nav_order: 9
---
# 9. Principio da Boa Ordem

## Resumo

### Enunciado
**Principio da Boa Ordem (PBO):** Todo subconjunto nao-vazio de N possui um elemento minimo.

Formalmente: Se A ⊆ N e A ≠ ∅, entao existe a₀ ∈ A tal que a₀ ≤ a para todo a ∈ A.

### O que significa "boa ordem"
Um conjunto e **bem ordenado** se toda parte nao-vazia dele tem um menor elemento. N com a ordem usual e bem ordenado. Nem todo conjunto numerico e:

| Conjunto | Bem ordenado? | Por que? |
|---|---|---|
| N = {0, 1, 2, ...} | Sim | Todo subconjunto nao-vazio tem minimo |
| Z = {..., -2, -1, 0, 1, ...} | Nao | Z nao tem minimo; {n ∈ Z : n < 0} tambem nao |
| Q⁺ = {q ∈ Q : q > 0} | Nao | {1, 1/2, 1/3, 1/4, ...} nao tem minimo |
| {3, 7, 15, 42} | Sim | Finito, minimo = 3 |

### Equivalencia fundamental
Os tres principios seguintes sao **logicamente equivalentes** (cada um pode ser derivado dos outros):

```
Principio de Inducao (fraca) ⟺ Principio de Inducao Forte ⟺ Principio da Boa Ordem
```

Isso significa que se voce aceita qualquer um como axioma, os outros dois se tornam teoremas.

### PBO → Inducao (esboço da prova)
Suponha que PBO vale e que:
- P(0) e verdadeiro
- P(k) → P(k+1) para todo k

Queremos mostrar que P(n) vale para todo n ∈ N.

*Prova:* Suponha por absurdo que existe n tal que P(n) e falso.
Seja A = {n ∈ N : P(n) e falso}. Entao A ≠ ∅.
Pelo PBO, A tem um elemento minimo n₀.
Como P(0) e verdadeiro, 0 ∉ A, logo n₀ ≥ 1, ou seja, n₀ = k+1 para algum k ≥ 0.
Como n₀ e o minimo de A, k ∉ A, logo P(k) e verdadeiro.
Pelo passo indutivo, P(k+1) = P(n₀) e verdadeiro.
Mas n₀ ∈ A significa P(n₀) e falso. **Contradicao.** □

### Inducao → PBO (esboço da prova)
Suponha que inducao vale. Seja A ⊆ N, A ≠ ∅. Queremos mostrar que A tem minimo.

*Prova:* Seja P(n) = "se n ∈ A, entao A tem um elemento ≤ n".
De forma equivalente, provaremos por inducao forte:
Q(n) = "se {0, 1, ..., n} ∩ A ≠ ∅, entao A tem minimo em {0, ..., n}".

Base: Q(0): se 0 ∈ A, entao 0 e o minimo de A. ✓
Passo: Se Q(k) vale e k+1 ∈ A, entao ou algum j ≤ k esta em A (e Q(k) da o minimo) ou k+1 e o minimo. ✓

Como A ≠ ∅, existe algum n com n ∈ A, e Q(n) garante que A tem minimo. □

### Aplicacoes do PBO

**1. Divisao euclidiana**
Para provar que dados a, b ∈ Z com b > 0, existem unicos q, r com a = bq + r e 0 ≤ r < b:
- Considere o conjunto A = {a - bq : q ∈ Z, a - bq ≥ 0}
- A ≠ ∅ (escolha q suficientemente negativo)
- Pelo PBO, A tem um minimo r = a - bq₀
- Mostre que r < b (por absurdo: se r ≥ b, entao r - b ∈ A e r - b < r, contradizendo a minimalidade)

**2. Tecnica do "criminoso minimo"**
Para provar ∀n ∈ N, P(n):
- Suponha que existe n com ¬P(n)
- Pelo PBO, existe o MENOR n₀ com ¬P(n₀) — o "criminoso minimo"
- Derive uma contradicao usando a minimalidade de n₀

**Exemplo:** Provar que todo n ≥ 2 tem fator primo.
Suponha que nao. Seja n₀ o menor inteiro ≥ 2 sem fator primo.
n₀ nao e primo (senao ele proprio seria fator primo de si mesmo).
Entao n₀ = a·b com 2 ≤ a, b < n₀.
Como a < n₀, e n₀ e o menor sem fator primo, a tem fator primo p.
p | a e a | n₀, logo p | n₀. **Contradicao.** □

## Pontos-chave para a prova
- Saber enunciar o PBO
- Entender por que Z e Q nao sao bem ordenados
- A equivalencia PBO ⟺ Inducao e central
- A tecnica do "criminoso minimo" e muito poderosa
- O PBO e usado na prova da divisao euclidiana

## Exercicio de fixacao
1. O conjunto {n ∈ N : n² > 10} tem minimo? Qual?
2. Por que {1/n : n ∈ N, n ≥ 1} nao contradiz o PBO?
3. Use o PBO para provar que nao existe natural entre 0 e 1.
4. Prove usando a tecnica do criminoso minimo: todo n ≥ 1 satisfaz 1 + 2 + ... + n = n(n+1)/2.

> Respostas: 1- Sim, minimo = 4 (pois 4²=16>10, 3²=9<10). 2- Esse conjunto esta em Q, nao em N. O PBO so vale para subconjuntos de N. 3- Suponha que existe n ∈ N com 0 < n < 1. Pelo PBO, seja n₀ o menor tal. Entao n₀² < n₀ < 1, e n₀² ∈ N (se n₀ ∈ N)... (depende da definicao de ordem usada).

## Referencias
- **MIT 6.042J** Textbook, Cap. 2 (Well-Ordering Principle) — https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/resources/mit6_042js15_textbook/
- **Elon Lages Lima**, Curso de Analise Vol.1, Cap. 1
- **UFS** - Aula 19: Principio da Boa Ordem — https://cesad.ufs.br/ORBI/public/uploadCatalago/15253016022012Fundamentos_de_Matematica_aula_19.pdf
- **IME-USP** - MAT0120 Aula 1 — https://www.ime.usp.br/~iusenko/ensino_2021_1/MAT0120/aulas/Aula1.pdf
- **Mathematics LibreTexts** — https://math.libretexts.org/Courses/Monroe_Community_College/MTH_220_Discrete_Math/3:_Proof_Techniques/3.7:_The_Well-Ordering_Principle
- **ProofWiki** — https://proofwiki.org/wiki/Well-Ordering_Principle
- **Book of Proof** (Hammack) — https://www.people.vcu.edu/~rhammack/BookOfProof/
