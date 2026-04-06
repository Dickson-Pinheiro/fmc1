---
layout: page
title: "1. Proposicoes e Funcoes"
nav_order: 1
---
# 1. Objetos, Proposicoes, Variaveis e Funcoes Proposicionais

## Resumo

### Objetos
Objetos sao as entidades basicas sobre as quais a matematica fala. Podem ser numeros (1, 2, 3), conjuntos ({1, 2}), funcoes, pontos geometricos, etc. Tudo que pode ser sujeito de uma afirmacao matematica e um objeto.

### Proposicoes
Uma **proposicao** e uma sentenca declarativa que possui exatamente um valor logico: **verdadeiro (V)** ou **falso (F)**.

**Exemplos de proposicoes:**
- "7 e um numero primo" (V)
- "2 + 3 = 6" (F)
- "Todo numero par maior que 2 e soma de dois primos" (V ou F, ainda nao provado — Conjectura de Goldbach — mas possui valor logico definido)

**Nao sao proposicoes:**
- "Que horas sao?" (pergunta)
- "Feche a porta" (comando)
- "x > 5" (depende do valor de x — e uma funcao proposicional)

### Variaveis proposicionais
Sao simbolos (p, q, r, ...) usados para representar proposicoes. Funcionam como "placeholders":
- p = "Hoje e segunda-feira"
- q = "Esta chovendo"

Permitem manipular proposicoes de forma abstrata sem se preocupar com o conteudo especifico.

### Funcoes proposicionais (predicados)
Uma **funcao proposicional** e uma expressao que contem uma ou mais variaveis livres e se torna uma proposicao quando valores sao atribuidos a essas variaveis.

**Notacao:** P(x), Q(x, y), etc.

**Exemplo:**
- P(x) = "x e par"
  - P(4) = "4 e par" → V (proposicao)
  - P(7) = "7 e par" → F (proposicao)
  - P(x) sozinho nao e proposicao — e um predicado

**Dominio (universo de discurso):** o conjunto de valores possiveis para a variavel. Se o dominio de x e N (naturais), entao P(x) = "x e par" gera proposicoes para cada n em N.

### Relacao entre os conceitos
```
Objeto → pode ser argumento de um predicado
Predicado + objeto → proposicao
Proposicao → tem valor V ou F
Variavel proposicional → representa uma proposicao
```

## Pontos-chave para a prova
- Saber distinguir o que e e o que nao e proposicao
- Entender que uma funcao proposicional so vira proposicao ao substituir as variaveis ou ao quantificar (para todo, existe)
- Dominio/universo de discurso afeta o valor logico

## Exercicio de fixacao
Classifique como proposicao (P), funcao proposicional (FP) ou nenhum (N):
1. "5 + 3 = 8"
2. "x + 3 = 8"
3. "Estude mais!"
4. "n e divisivel por 3"
5. "O conjunto vazio e subconjunto de todo conjunto"

> Respostas: 1-P, 2-FP, 3-N, 4-FP, 5-P

## Referencias
- **Book of Proof** (Hammack), Cap. 1-2 — https://www.people.vcu.edu/~rhammack/BookOfProof/
- **How to Prove It** (Velleman), Cap. 1
- **Rosen**, Discrete Mathematics, Cap. 1 (Secoes 1.1-1.3)
- **Blauth Menezes**, Matematica Discreta para Computacao, Cap. 1-2
- **UNIVESP** - Matematica Discreta (YouTube, PT): buscar "UNIVESP Matematica Discreta"
- **Neso Academy** - Discrete Mathematics (YouTube, EN)
