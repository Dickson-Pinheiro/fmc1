---
layout: page
title: "8. Operacoes nos Naturais"
nav_order: 8
---
# 8. Numeros Naturais: Operacoes

## Resumo

### Por que precisamos definir adicao e multiplicacao?

Voce sabe somar desde crianca. Entao por que a matematica se da ao trabalho de "definir" o que e 2 + 3?

O ponto e que, com os Axiomas de Peano, comecamos do ZERO — literalmente. Tudo o que temos e:

```
- O numero 0
- A funcao sucessor S(n), que nos da o "proximo" numero
- Os axiomas que garantem que isso funciona (topico 7)
```

A partir disso, **nao temos soma nem multiplicacao**. Elas nao existem ate que as definamos. E mais: depois de defini-las, propriedades que parecem "obvias" (como a + b = b + a) precisam ser **provadas** — porque elas nao fazem parte da definicao.

Isso parece exagerado, mas e a base de como a matematica funciona: comece com o minimo de suposicoes e construa tudo a partir delas.

---

### Relembrando: o que temos ate agora

Antes de definir as operacoes, vale lembrar o que ja esta disponivel:

```
Numeros naturais: 0, S(0), S(S(0)), S(S(S(0))), ...
                  0,  1,     2,       3, ...

Nomes convenientes:
  1 = S(0)
  2 = S(1) = S(S(0))
  3 = S(2) = S(S(S(0)))
  4 = S(3) = S(S(S(S(0))))
  ...
```

A unica "operacao" que temos e S (dar o proximo). Adicao e multiplicacao serao construidas **a partir de S**.

---

### Adicao: definicao recursiva

A ideia intuitiva: somar m + n e "aplicar o sucessor n vezes, comecando de m".

```
m + 0:     nao aplico nenhum sucessor → o resultado e m
m + 1:     aplico S uma vez → S(m)
m + 2:     aplico S duas vezes → S(S(m))
m + 3:     aplico S tres vezes → S(S(S(m)))
```

Isso se formaliza em duas regras:

```
(A1)  m + 0 = m                    (caso base: somar 0 nao faz nada)
(A2)  m + S(n) = S(m + n)          (passo recursivo: somar o "proximo" e
                                     o mesmo que dar mais um S no resultado)
```

**Leia A2 assim:** "para somar m com o sucessor de n, primeiro some m com n e depois aplique S".

A definicao e **recursiva no segundo argumento**: ela "descasca" o segundo numero ate chegar a 0, onde o caso base resolve.

---

### Exemplo passo a passo: calcular 2 + 2

Vamos seguir as regras ao pe da letra, sem pular nenhum passo:

```
2 + 2
= 2 + S(1)           Reescrevemos 2 como S(1)
= S(2 + 1)           Aplicamos A2: m + S(n) = S(m + n), com m=2 e n=1
                      (Descascamos um S do segundo argumento)

Agora precisamos calcular 2 + 1:
  2 + 1
  = 2 + S(0)         Reescrevemos 1 como S(0)
  = S(2 + 0)         Aplicamos A2 de novo, com m=2 e n=0
                      (Descascamos mais um S)

  Agora precisamos calcular 2 + 0:
    2 + 0 = 2        Caso base! Aplicamos A1.

  Voltando: 2 + 1 = S(2 + 0) = S(2) = 3

Voltando: 2 + 2 = S(2 + 1) = S(3) = 4  ✓
```

**Observe o padrao:** cada aplicacao de A2 "descasca" um S(…) do segundo argumento. Quando o segundo argumento chega a 0, A1 encerra a recursao. Depois, os S(…) se "acumulam" ao redor do resultado.

---

### Exemplo passo a passo: calcular 3 + 1

```
3 + 1
= 3 + S(0)           Reescrevemos 1 como S(0)
= S(3 + 0)           Aplicamos A2
= S(3)               Aplicamos A1
= 4                  ✓
```

---

### Exemplo passo a passo: calcular 1 + 2

```
1 + 2
= 1 + S(1)           Reescrevemos 2 como S(1)
= S(1 + 1)           Aplicamos A2

  1 + 1
  = 1 + S(0)         Reescrevemos 1 como S(0)
  = S(1 + 0)         Aplicamos A2
  = S(1)             Aplicamos A1
  = 2

= S(2) = 3           ✓
```

---

### A armadilha: por que 0 + n = n NAO e obvio?

Esse e um ponto que confunde todo mundo e que aparece em provas. Veja:

```
A definicao A1 diz:  m + 0 = m     (o 0 esta no SEGUNDO argumento)

Isso nos da de graca:
  5 + 0 = 5  ✓
  100 + 0 = 100  ✓
  n + 0 = n  ✓   (para qualquer n — e literal na definicao)
```

Mas e **0 + n = n**? Aqui o 0 esta no PRIMEIRO argumento. A definicao nao diz nada sobre isso! Veja:

```
0 + 3 = ?
= 0 + S(2)    →  A2  →  S(0 + 2)
= S(0 + S(1)) →  A2  →  S(S(0 + 1))
= S(S(0 + S(0))) → A2 → S(S(S(0 + 0)))
= S(S(S(0)))      → A1 → S(S(S(0))) = 3  ✓
```

Funcionou para 0 + 3. Mas para provar que funciona **para todo n**, precisamos de inducao.

#### Prova: 0 + n = n para todo n ∈ ℕ

```
Caso base (n = 0):
  0 + 0 = 0.  (Por A1, com m = 0.)  ✓

H.I.: Suponha que 0 + k = k para algum k ≥ 0.

Passo indutivo (provar 0 + S(k) = S(k)):
  0 + S(k)
  = S(0 + k)       ← por A2
  = S(k)            ← pela H.I. (substituimos 0 + k por k)  ✓

Pelo principio de inducao, 0 + n = n para todo n ∈ ℕ. □
```

**A licao:** as definicoes recursivas fixam UM dos argumentos na recursao (aqui, o segundo). Propriedades envolvendo o OUTRO argumento quase sempre exigem prova por inducao.

---

### Lema auxiliar importante: S(n) = n + 1

Outro fato que "parece obvio" mas precisa de prova. A definicao diz m + S(n) = S(m + n), nao que S(n) = n + 1 diretamente.

#### Prova: S(n) = n + 1 para todo n ∈ ℕ

Aqui, "n + 1" significa n + S(0) pelas definicoes.

```
n + 1
= n + S(0)          Reescrevemos 1 como S(0)
= S(n + 0)          Por A2
= S(n)              Por A1  ✓
```

Esse nao precisou nem de inducao — saiu direto das definicoes! Mas e importante registrar: **S(n) e a mesma coisa que n + 1**.

---

### Lema auxiliar: S(m) + n = S(m + n)

Esse lema e necessario para provar a comutatividade. Ele diz que "somar a partir do sucessor de m da o mesmo que somar a partir de m e depois aplicar S".

Note que A2 nos da m + S(n) = S(m + n) — o S esta no **segundo** argumento. Esse lema coloca o S no **primeiro** argumento.

#### Prova por inducao em n:

```
Caso base (n = 0):
  S(m) + 0 = S(m)         ← por A1
  S(m + 0) = S(m)         ← por A1
  Logo S(m) + 0 = S(m + 0).  ✓

H.I.: Suponha que S(m) + k = S(m + k).

Passo indutivo (provar S(m) + S(k) = S(m + S(k))):
  S(m) + S(k)
  = S(S(m) + k)            ← por A2
  = S(S(m + k))            ← pela H.I.

  S(m + S(k))
  = S(S(m + k))            ← por A2 (aplicado a m + S(k))

  Ambos os lados dao S(S(m + k)).  ✓

Pelo principio de inducao, S(m) + n = S(m + n) para todo n. □
```

---

### Provando a comutatividade da adicao: a + b = b + a

Essa e a primeira propriedade "grande" — e a prova usa os dois lemas anteriores.

#### Prova por inducao em b:

```
Caso base (b = 0):
  a + 0 = a            ← por A1
  0 + a = a            ← pelo lema "0 + n = n"
  Logo a + 0 = 0 + a.  ✓

H.I.: Suponha que a + k = k + a.

Passo indutivo (provar a + S(k) = S(k) + a):
  a + S(k)
  = S(a + k)           ← por A2
  = S(k + a)           ← pela H.I. (trocamos a + k por k + a)

  S(k) + a
  = S(k + a)           ← pelo lema "S(m) + n = S(m + n)"

  Ambos os lados dao S(k + a).  ✓

Pelo principio de inducao, a + b = b + a para todo a, b ∈ ℕ. □
```

**Observe a estrutura:** cada passo usa um resultado anterior. A matematica se constroi como uma torre de blocos:

```
Definicoes A1, A2
    ↓
Lema: 0 + n = n
    ↓
Lema: S(n) = n + 1
    ↓
Lema: S(m) + n = S(m + n)
    ↓
Teorema: a + b = b + a
```

Nada e "obvio" neste contexto — tudo e construido.

---

### Associatividade da adicao: (a + b) + c = a + (b + c)

#### Prova por inducao em c:

```
Caso base (c = 0):
  (a + b) + 0 = a + b          ← por A1
  a + (b + 0) = a + b          ← por A1 (aplicado a b + 0 = b)
  Iguais.  ✓

H.I.: Suponha que (a + b) + k = a + (b + k).

Passo indutivo (provar (a + b) + S(k) = a + (b + S(k))):
  (a + b) + S(k)
  = S((a + b) + k)             ← por A2
  = S(a + (b + k))             ← pela H.I.

  a + (b + S(k))
  = a + S(b + k)               ← por A2 (aplicado a b + S(k))
  = S(a + (b + k))             ← por A2 (aplicado a a + S(b+k))

  Ambos os lados dao S(a + (b + k)).  ✓

Pelo principio de inducao, (a + b) + c = a + (b + c) para todo a, b, c ∈ ℕ. □
```

**Dica para provas:** a associatividade e a comutatividade quase sempre usam inducao no argumento "mais externo" ou no ultimo argumento. Teste c ou b primeiro.

---

### Multiplicacao: definicao recursiva

A ideia intuitiva: multiplicar m · n e "somar m consigo mesmo n vezes".

```
m · 0:     somo m zero vezes → resultado e 0
m · 1:     somo m uma vez → m
m · 2:     somo m duas vezes → m + m
m · 3:     somo m tres vezes → m + m + m
```

Formalmente:

```
(M1)  m · 0 = 0                    (caso base: multiplicar por 0 da 0)
(M2)  m · S(n) = m · n + m         (passo recursivo: multiplicar pelo proximo
                                     e somar mais uma copia de m)
```

**Leia M2 assim:** "m vezes o sucessor de n" e o mesmo que "m vezes n, mais m". Ou seja, adicionamos mais uma "parcela" de m.

Note que M2 usa a ADICAO, que ja foi definida. A multiplicacao e construida **em cima** da adicao.

---

### Exemplo passo a passo: calcular 2 · 3

```
2 · 3
= 2 · S(2)                   Reescrevemos 3 como S(2)
= 2 · 2 + 2                  Aplicamos M2: m·S(n) = m·n + m

  Agora precisamos calcular 2 · 2:
  2 · 2
  = 2 · S(1)                 Reescrevemos 2 como S(1)
  = 2 · 1 + 2                Aplicamos M2

    Agora precisamos calcular 2 · 1:
    2 · 1
    = 2 · S(0)               Reescrevemos 1 como S(0)
    = 2 · 0 + 2              Aplicamos M2

      Agora precisamos calcular 2 · 0:
      2 · 0 = 0              Caso base! Aplicamos M1.

    Voltando: 2 · 1 = 0 + 2 = 2     (pela definicao de adicao)

  Voltando: 2 · 2 = 2 + 2 = 4       (pela definicao de adicao)

Voltando: 2 · 3 = 4 + 2 = 6         ✓
```

**Observe:** cada aplicacao de M2 "descasca" um S(…) do segundo argumento e gera uma soma com m. Quando chega em 0, M1 para a recursao. Depois, somamos tudo.

---

### Exemplo passo a passo: calcular 2 · 2

Detalhando mais devagar (util para exercicios):

```
2 · 2
= 2 · S(1)          [2 = S(1)]
= 2 · 1 + 2         [M2]
= (2 · S(0)) + 2    [1 = S(0)]
= (2 · 0 + 2) + 2   [M2]
= (0 + 2) + 2       [M1: 2 · 0 = 0]
= 2 + 2             [0 + n = n, ja provado por inducao!]
= 4                  [ja calculamos acima]  ✓
```

**Note:** no passo "0 + 2 = 2", estamos usando o lema que provamos por inducao! Sem ele, teriamos que expandir 0 + 2 usando A1 e A2.

---

### A armadilha da multiplicacao: 0 · n = 0

Assim como na adicao, a definicao fixa o segundo argumento:

```
M1 diz:  m · 0 = 0     (o 0 esta no SEGUNDO argumento)

Isso nos da de graca:
  5 · 0 = 0  ✓
  n · 0 = 0  ✓
```

Mas **0 · n = 0** tem o 0 no PRIMEIRO argumento. Precisamos de inducao.

#### Prova: 0 · n = 0 para todo n ∈ ℕ

```
Caso base (n = 0):
  0 · 0 = 0.  (Por M1.)  ✓

H.I.: Suponha que 0 · k = 0.

Passo indutivo (provar 0 · S(k) = 0):
  0 · S(k)
  = 0 · k + 0          ← por M2
  = 0 + 0              ← pela H.I. (0 · k = 0)
  = 0                   ← por A1  ✓

Pelo principio de inducao, 0 · n = 0 para todo n ∈ ℕ. □
```

---

### Propriedades da multiplicacao (provadas por inducao)

Assim como na adicao, todas as propriedades "obvias" precisam ser demonstradas:

| Propriedade | Enunciado | Ideia da prova |
|---|---|---|
| Absorcao | 0 · n = 0 | Inducao em n (provada acima) |
| Identidade | 1 · n = n | Inducao em n |
| Distributividade | a · (b + c) = a·b + a·c | Inducao em c |
| Associatividade | (a · b) · c = a · (b · c) | Inducao em c |
| Comutatividade | a · b = b · a | Inducao em b (precisa de lemas) |

A torre de dependencias para a multiplicacao:

```
Definicoes M1, M2 + toda a teoria da adicao
    ↓
Lema: 0 · n = 0
    ↓
Lema: 1 · n = n
    ↓
Lema: S(m) · n = m · n + n       (analogo ao lema S(m) + n da adicao)
    ↓
Distributividade: a · (b + c) = a·b + a·c
    ↓
Comutatividade: a · b = b · a
    ↓
Associatividade: (a · b) · c = a · (b · c)
```

---

### Prova da distributividade: a · (b + c) = a · b + a · c

Essa prova e fundamental — a comutatividade e a associatividade da multiplicacao dependem dela.

#### Prova por inducao em c:

```
Caso base (c = 0):
  a · (b + 0) = a · b           ← por A1 (b + 0 = b)
  a · b + a · 0 = a · b + 0 = a · b   ← por M1 e A1
  Iguais.  ✓

H.I.: Suponha que a · (b + k) = a · b + a · k.

Passo indutivo (provar a · (b + S(k)) = a · b + a · S(k)):

  Lado esquerdo:
    a · (b + S(k))
    = a · S(b + k)              ← por A2 (b + S(k) = S(b + k))
    = a · (b + k) + a           ← por M2
    = (a · b + a · k) + a       ← pela H.I.

  Lado direito:
    a · b + a · S(k)
    = a · b + (a · k + a)       ← por M2 (a · S(k) = a · k + a)
    = (a · b + a · k) + a       ← pela associatividade da adicao

  Ambos os lados dao (a · b + a · k) + a.  ✓

Pelo principio de inducao, a · (b + c) = a · b + a · c para todo a, b, c ∈ ℕ. □
```

**Observe:** no passo indutivo, usamos a associatividade da adicao (que ja foi provada antes). Cada prova nova pode usar todos os resultados anteriores.

---

### Ordem nos naturais

Com a adicao definida, podemos definir a ordem:

```
m ≤ n   ⟺   ∃k ∈ ℕ tal que m + k = n
m < n   ⟺   m ≤ n  ∧  m ≠ n
```

**Leia assim:** "m e menor ou igual a n" significa que existe um numero natural k que, somado a m, da n. Ou seja, n esta "k passos a frente" de m.

**Exemplos:**
```
3 ≤ 5?  Existe k ∈ ℕ com 3 + k = 5?  Sim: k = 2. Logo 3 ≤ 5.  ✓
5 ≤ 3?  Existe k ∈ ℕ com 5 + k = 3?  Nao (somar natural a 5 da ≥ 5). Logo 5 ≤ 3 e falso.  ✗
0 ≤ n?  Existe k ∈ ℕ com 0 + k = n?  Sim: k = n (pois 0 + n = n). Logo 0 ≤ n para todo n.  ✓
```

**Propriedades importantes da ordem (provadas por inducao):**

| Propriedade | Enunciado |
|---|---|
| Reflexiva | n ≤ n (pois n + 0 = n) |
| Antissimetrica | se m ≤ n e n ≤ m, entao m = n |
| Transitiva | se a ≤ b e b ≤ c, entao a ≤ c |
| Totalidade | para todo m, n: m ≤ n ou n ≤ m |
| Compativel com + | se a ≤ b, entao a + c ≤ b + c |
| Compativel com · | se a ≤ b, entao a · c ≤ b · c |

---

### Cancelamento na adicao: a + c = b + c ⟹ a = b

Outra propriedade que parece obvia mas exige prova.

#### Prova por inducao em c:

```
Caso base (c = 0):
  a + 0 = b + 0  ⟹  a = b.  (Por A1.)  ✓

H.I.: Suponha que a + k = b + k ⟹ a = b.

Passo indutivo (provar que a + S(k) = b + S(k) ⟹ a = b):
  Se a + S(k) = b + S(k), entao:
  S(a + k) = S(b + k)          ← por A2 (aplicado dos dois lados)
  a + k = b + k                ← pois S e injetora (Axioma de Peano!)
  a = b                        ← pela H.I.  ✓

Pelo principio de inducao, a + c = b + c ⟹ a = b para todo c ∈ ℕ. □
```

**Note:** usamos o axioma de Peano "S e injetora" (S(x) = S(y) ⟹ x = y) diretamente na prova. Os axiomas de Peano nao sao apenas fundamento teorico — eles aparecem como ferramentas nas demonstracoes.

---

### Visao geral: a hierarquia de construcao

Tudo se encaixa como uma torre. Cada nivel so usa os anteriores:

```
NIVEL 0: Axiomas de Peano (0, S, injetividade, 0 ≠ S(n), inducao)
    ↓
NIVEL 1: Definicao da adicao (A1, A2)
    ↓
NIVEL 2: Propriedades da adicao
         (0+n=n, comutatividade, associatividade, cancelamento)
    ↓
NIVEL 3: Definicao da multiplicacao (M1, M2)
    ↓
NIVEL 4: Propriedades da multiplicacao
         (0·n=0, distributividade, comutatividade, associatividade)
    ↓
NIVEL 5: Definicao da ordem (≤, <)
    ↓
NIVEL 6: Propriedades da ordem
         (reflexiva, transitiva, compatibilidade com + e ·)
```

**Na prova da disciplina:** o mais comum e pedir para voce calcular expressoes usando A1/A2/M1/M2, ou provar alguma propriedade por inducao. Saber "em que nivel" cada resultado esta ajuda a saber o que voce pode usar em cada prova.

---

### Erros comuns

**1. Confundir m + 0 = m com 0 + m = m**

```
m + 0 = m  ← DEFINICAO (A1), vale de graca
0 + m = m  ← TEOREMA, exige prova por inducao

O mesmo vale para multiplicacao: m · 0 = 0 vs. 0 · m = 0.
```

**2. Usar comutatividade antes de prova-la**

```
ERRADO (ao provar 0 + n = n):
  "0 + n = n + 0 = n."

Voce usou a + b = b + a, mas esse e o TEOREMA que voce
ainda nao provou! A comutatividade nao pode ser usada ate
que seja demonstrada.
```

**3. Pular passos nas computacoes**

```
ERRADO:  2 · 3 = 6.  (De onde veio isso?)

CERTO:   2 · 3 = 2 · S(2) = 2 · 2 + 2 = ... = 6.
         (Cada igualdade justificada por A1, A2, M1 ou M2.)
```

**4. Esquecer que a multiplicacao DEPENDE da adicao**

Na definicao M2, aparece "+ m". Isso significa que para computar uma multiplicacao, voce eventualmente precisa computar adicoes. As duas operacoes nao sao independentes.

---

## Pontos-chave para a prova
- Saber as definicoes recursivas: A1, A2 (adicao) e M1, M2 (multiplicacao)
- Saber "computar" passo a passo usando APENAS essas regras
- Entender que comutatividade e associatividade sao **provadas**, nao assumidas
- 0 + n = n e 0 · n = 0 **exigem** prova por inducao (a definicao fixa o SEGUNDO argumento)
- As provas seguem uma hierarquia: cada resultado usa apenas os anteriores
- Os Axiomas de Peano (especialmente S injetora) aparecem como ferramentas nas demonstracoes

## Exercicios de fixacao

**Computacoes:**
1. Calcule 3 + 2 usando apenas A1 e A2. Mostre cada passo.
2. Calcule 1 + 3 usando apenas A1 e A2.
3. Calcule 3 · 2 usando M1, M2, A1 e A2.
4. Calcule 2 · 2 usando M1, M2, A1 e A2. (Detalhe cada soma intermediaria.)

**Provas por inducao:**
5. Prove que S(n) = n + 1 para todo n (dica: basta usar A1 e A2, sem inducao).
6. Prove que 0 + n = n para todo n ∈ ℕ.
7. Prove que 0 · n = 0 para todo n ∈ ℕ.
8. Prove que 1 · n = n para todo n ∈ ℕ. (Dica: use M1, M2 e o lema 0 + n = n.)
9. Prove a associatividade: (a + b) + c = a + (b + c) para todo a, b, c ∈ ℕ.

**Conceitual:**
10. Por que 0 · n = 0 precisa de prova, mas n · 0 = 0 nao?
11. Na prova de comutatividade de +, quais lemas sao usados?

> **Respostas selecionadas:**
>
> 1- 3+2 = 3+S(1) = S(3+1) = S(3+S(0)) = S(S(3+0)) = S(S(3)) = S(4) = 5. □
>
> 2- 1+3 = 1+S(2) = S(1+2) = S(1+S(1)) = S(S(1+1)) = S(S(1+S(0))) = S(S(S(1+0))) = S(S(S(1))) = S(S(2)) = S(3) = 4. □
>
> 3- 3·2 = 3·S(1) = 3·1 + 3 = (3·S(0)) + 3 = (3·0 + 3) + 3 = (0+3)+3 = 3+3
>    = 3+S(2) = S(3+2) = S(3+S(1)) = S(S(3+1)) = S(S(3+S(0))) = S(S(S(3+0))) = S(S(S(3))) = S(S(4)) = S(5) = 6. □
>
> 5- n+1 = n+S(0) = S(n+0) = S(n). Logo S(n) = n+1. (Nao precisa de inducao.) □
>
> 8- Base: 1·0 = 0 (por M1). E 0 = 0. ✓.
>    Passo: 1·S(k) = 1·k + 1 (por M2) = k + 1 (pela H.I.) = S(k) (pois n+1 = S(n)). ✓. □
>
> 10- n·0 = 0 e a definicao M1 — e literal. 0·n tem 0 no primeiro argumento,
>     que nao e o argumento da recursao. A definicao so "descasca" o segundo
>     argumento, entao 0·n precisa de inducao para "percorrer" todos os valores de n. □
>
> 11- Sao usados: (1) o lema 0+n = n (no caso base) e (2) o lema S(m)+n = S(m+n) (no passo indutivo).

## Referencias
- **Terence Tao**, Analysis I, Cap. 2 (adicao) e Cap. 3 (multiplicacao) — tratamento completo
- **Elon Lages Lima**, Curso de Analise Vol.1, Cap. 1
- **UFPR** - Apostila Numeros Naturais — https://docs.ufpr.br/~fernando.avila/Sem2-2023/CMM011/Apostila/N.pdf
- **UChicago** - Peano Arithmetic — http://cmsc-16100.cs.uchicago.edu/2018-autumn/Notes/arithmetic.php
- **Keith Devlin** - "How Multiplication Is Really Defined in Peano Arithmetic"
- **Wikipedia** - Peano Axioms (secao Arithmetic) — https://en.wikipedia.org/wiki/Peano_axioms
