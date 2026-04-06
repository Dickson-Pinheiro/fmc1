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
Comutatividade: a + b = b + a
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

### Cancelamento na adicao: a + c = b + c ⟹ a = b

Essa propriedade parece obvia, mas exige prova — e e uma das mais usadas em demonstracoes posteriores (inclusive no cancelamento da multiplicacao).

**A intuicao:** se dois numeros, somados ao mesmo valor, dao o mesmo resultado, entao eles sao iguais.

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

### Resumo: a hierarquia completa das propriedades da adicao

```
Definicoes A1, A2
    ↓
Lema: 0 + n = n
    ↓
Lema: S(n) = n + 1
    ↓
Lema: S(m) + n = S(m + n)
    ↓
Comutatividade: a + b = b + a
    ↓
Associatividade: (a + b) + c = a + (b + c)
    ↓
Cancelamento: a + c = b + c ⟹ a = b
```

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

Assim como na adicao, todas as propriedades "obvias" precisam ser demonstradas. A ordem importa: cada prova pode usar apenas os resultados anteriores.

| # | Propriedade | Enunciado | Ideia da prova |
|---|---|---|---|
| 1 | Absorcao | 0 · a = 0 | Inducao em a (provada acima) |
| 2 | Lema do sucessor | S(a) · b = (a · b) + b | Inducao em b |
| 3 | Comutatividade | a · b = b · a | Inducao em b (usa props. 1 e 2) |
| 4 | Distributividade | a · (b + c) = a·b + a·c | Inducao em c |
| 5 | Associatividade | (a · b) · c = a · (b · c) | Inducao em c (usa prop. 4) |

A torre de dependencias para a multiplicacao:

```
Definicoes M1, M2 + toda a teoria da adicao
    ↓
Propriedade 1: 0 · a = 0              (lema — inducao em a)
    ↓
Propriedade 2: S(a) · b = (a·b) + b   (lema — inducao em b)
    ↓
Propriedade 3: a · b = b · a           (comutatividade — usa props. 1 e 2)
    ↓
Propriedade 4: a·(b+c) = a·b + a·c    (distributividade — independe de 3)
    ↓
Propriedade 5: (a·b)·c = a·(b·c)      (associatividade — usa prop. 4)
```

**Por que essa ordem?** Props 1 e 2 sao lemas preparatorios (analogos aos da adicao). A comutatividade (3) depende deles. A distributividade (4) e independente da comutatividade — usa apenas as definicoes e propriedades da adicao. A associatividade (5) depende da distributividade (4). Como 3 e 4 sao independentes, podem vir em qualquer ordem entre si, mas essa sequencia e mais natural: primeiro fechamos a comutatividade (completando o paralelo com a adicao), depois introduzimos a distributividade (propriedade nova que mistura · e +), e por fim a associatividade.

---

### Propriedade 1: 0 · a = 0 (absorcao)

Essa propriedade ja foi provada acima, mas vale relembrar por que ela e necessaria.

A definicao M1 diz que **m · 0 = 0** — o zero esta no SEGUNDO argumento. Isso nos da n · 0 = 0 de graca. Mas **0 · a = 0** tem o zero no PRIMEIRO argumento, que nao e o argumento da recursao. Por isso, precisamos de inducao.

A prova completa esta na secao anterior. O resultado e:

```
0 · a = 0   para todo a ∈ ℕ.  □
```

---

### Propriedade 2 (Lema do sucessor): S(a) · b = (a · b) + b

Esse lema e o analogo multiplicativo do lema S(m) + n = S(m + n) que usamos na comutatividade da adicao.

**A intuicao:** multiplicar S(a) por b e o mesmo que "b vezes o proximo de a". Ou seja, sao b parcelas de S(a), que e b parcelas de a MAIS b parcelas de 1 (que e b). Formalmente: S(a) · b = (a · b) + b.

**Por que precisamos disso?** A definicao M2 diz m · S(n) = m · n + m — o S(…) esta no **segundo** argumento. Esse lema move o S(…) para o **primeiro** argumento. Sem ele, nao conseguimos provar a comutatividade.

#### Prova por inducao em b:

```
Caso base (b = 0):
  Lado esquerdo:
    S(a) · 0 = 0                   ← por M1

  Lado direito:
    (a · 0) + 0
    = 0 + 0                        ← por M1 (a · 0 = 0)
    = 0                             ← por A1

  Ambos os lados dao 0.  ✓

H.I.: Suponha que S(a) · k = (a · k) + k.

Passo indutivo (provar S(a) · S(k) = (a · S(k)) + S(k)):

  Lado esquerdo:
    S(a) · S(k)
    = S(a) · k + S(a)              ← por M2
    = ((a · k) + k) + S(a)         ← pela H.I.

  Lado direito:
    (a · S(k)) + S(k)
    = (a · k + a) + S(k)           ← por M2 (a · S(k) = a · k + a)

  Precisamos mostrar que ((a·k) + k) + S(a) = (a·k + a) + S(k).

  Simplificando o lado esquerdo:
    ((a · k) + k) + S(a)
    = S(((a · k) + k) + a)         ← por A2
    = S((a · k) + (k + a))         ← pela associatividade da adicao

  Simplificando o lado direito:
    (a · k + a) + S(k)
    = S((a · k + a) + k)           ← por A2
    = S(a · k + (a + k))           ← pela associatividade da adicao

  Agora, pela comutatividade da ADICAO (ja provada):
    k + a = a + k

  Logo:
    S((a · k) + (k + a)) = S(a · k + (a + k))  ✓

Pelo principio de inducao, S(a) · b = (a · b) + b para todo a, b ∈ ℕ. □
```

**Observe:** essa prova usa a comutatividade e associatividade da ADICAO (que ja foram provadas). As propriedades da adicao sao ferramentas para provar as propriedades da multiplicacao.

---

### Propriedade 3 (Comutatividade): a · b = b · a

Assim como na adicao, a comutatividade da multiplicacao **nao e parte da definicao** — precisa ser provada. A prova segue a mesma estrutura da comutatividade da adicao: usa dois lemas (propriedades 1 e 2) como ingredientes.

**Comparacao com a adicao — o padrao e o mesmo:**

```
Adicao:                              Multiplicacao:
  Lema: 0 + n = n                      Prop 1: 0 · a = 0
  Lema: S(m) + n = S(m + n)            Prop 2: S(a) · b = (a · b) + b
  Teorema: a + b = b + a               Prop 3: a · b = b · a
```

#### Prova por inducao em b:

```
Caso base (b = 0):
  Lado esquerdo:
    a · 0 = 0                      ← por M1

  Lado direito:
    0 · a = 0                      ← pela Propriedade 1

  Ambos os lados dao 0.  ✓

H.I.: Suponha que a · k = k · a.

Passo indutivo (provar a · S(k) = S(k) · a):

  Lado esquerdo:
    a · S(k)
    = a · k + a                    ← por M2
    = k · a + a                    ← pela H.I. (trocamos a · k por k · a)

  Lado direito:
    S(k) · a
    = (k · a) + a                  ← pela Propriedade 2 (S(k)·a = k·a + a)

  Ambos os lados dao (k · a) + a.  ✓

Pelo principio de inducao, a · b = b · a para todo a, b ∈ ℕ. □
```

**A estrutura e elegante:** o caso base usa a Propriedade 1 (0 · a = 0) e o passo indutivo usa a Propriedade 2 (S(a) · b = (a · b) + b). Sem esses dois lemas, a prova nao fecha.

---

### Propriedade 4 (Distributividade): a · (b + c) = a · b + a · c

Essa propriedade e a primeira que mistura as duas operacoes (multiplicacao e adicao). Ela e fundamental porque a associatividade da multiplicacao (propriedade 5) depende dela.

**A intuicao:** se voce tem a parcelas de (b + c), e o mesmo que a parcelas de b mais a parcelas de c.

**Note:** essa prova NAO usa a comutatividade da multiplicacao (propriedade 3). Ela e independente — usa apenas as definicoes e propriedades da adicao. Por isso, as propriedades 3 e 4 podem vir em qualquer ordem.

#### Prova por inducao em c:

```
Caso base (c = 0):
  Lado esquerdo:
    a · (b + 0) = a · b            ← por A1 (b + 0 = b)

  Lado direito:
    a · b + a · 0
    = a · b + 0                    ← por M1 (a · 0 = 0)
    = a · b                        ← por A1

  Iguais.  ✓

H.I.: Suponha que a · (b + k) = a · b + a · k.

Passo indutivo (provar a · (b + S(k)) = a · b + a · S(k)):

  Lado esquerdo:
    a · (b + S(k))
    = a · S(b + k)                 ← por A2 (b + S(k) = S(b + k))
    = a · (b + k) + a              ← por M2
    = (a · b + a · k) + a          ← pela H.I.

  Lado direito:
    a · b + a · S(k)
    = a · b + (a · k + a)          ← por M2 (a · S(k) = a · k + a)
    = (a · b + a · k) + a          ← pela associatividade da adicao

  Ambos os lados dao (a · b + a · k) + a.  ✓

Pelo principio de inducao, a · (b + c) = a · b + a · c para todo a, b, c ∈ ℕ. □
```

**Observe:** no passo indutivo, usamos a associatividade da adicao (que ja foi provada). Cada prova nova pode usar todos os resultados anteriores.

---

### Propriedade 5 (Associatividade): (a · b) · c = a · (b · c)

Essa e a ultima propriedade da lista e a mais "pesada", porque depende de quase tudo que veio antes.

**A intuicao:** agrupar a multiplicacao de forma diferente nao muda o resultado. Mas como a multiplicacao foi definida recursivamente no segundo argumento, precisamos de inducao para provar isso.

**O que essa prova usa:**
- Definicoes M1, M2
- Distributividade (Propriedade 4): a · (b + c) = a · b + a · c

#### Prova por inducao em c:

```
Caso base (c = 0):
  Lado esquerdo:
    (a · b) · 0 = 0                ← por M1

  Lado direito:
    a · (b · 0)
    = a · 0                        ← por M1 (b · 0 = 0)
    = 0                             ← por M1

  Ambos os lados dao 0.  ✓

H.I.: Suponha que (a · b) · k = a · (b · k).

Passo indutivo (provar (a · b) · S(k) = a · (b · S(k))):

  Lado esquerdo:
    (a · b) · S(k)
    = (a · b) · k + (a · b)       ← por M2
    = a · (b · k) + (a · b)       ← pela H.I.

  Lado direito:
    a · (b · S(k))
    = a · (b · k + b)             ← por M2 (b · S(k) = b · k + b)
    = a · (b · k) + a · b         ← pela Distributividade (Prop. 4)

  Ambos os lados dao a · (b · k) + (a · b).  ✓

Pelo principio de inducao, (a · b) · c = a · (b · c) para todo a, b, c ∈ ℕ. □
```

**Observe como a distributividade foi essencial:** sem ela, nao conseguiriamos "abrir" a expressao a · (b · k + b) no lado direito. Esse e o motivo pelo qual a distributividade precisa ser provada ANTES da associatividade.

---

### Cancelamento na multiplicacao: a · c = b · c ∧ c ≠ 0 ⟹ a = b

Essa e a versao multiplicativa do cancelamento. Comparada com o cancelamento da adicao, ela e **mais delicada** por um motivo importante:

Precisamos exigir **c ≠ 0** (pois a · 0 = b · 0 = 0 para quaisquer a, b — nao podemos concluir nada).

**A exigencia c ≠ 0 e essencial.** Sem ela: 3 · 0 = 5 · 0 (ambos sao 0), mas 3 ≠ 5.

**Nota:** essa prova depende do cancelamento da adicao (a + c = b + c ⟹ a = b), que ja foi demonstrado na secao anterior.

---

#### Fato auxiliar: a · c + c ≠ 0 quando c ≠ 0

Antes da prova principal, precisamos de um fato simples: se c ≠ 0, entao a · c + c ≠ 0.

```
Prova:
  Se c ≠ 0, entao c = S(c') para algum c'.
  a · c + c = a · c + S(c') = S(a · c + c')     ← por A2
  E S(a · c + c') ≠ 0 pelo axioma de Peano (0 nao e sucessor de ninguem). □
```

Esse fato e usado no passo indutivo para garantir que b ≠ 0.

---

#### Prova por inducao em a

A ideia e fixar b e c (com c ≠ 0) e fazer inducao em a.

```
Caso base (a = 0):
  Temos 0 · c = b · c.
  0 · c = 0                           ← pela Propriedade 1
  Logo b · c = 0.

  Mas c ≠ 0. Se b tambem fosse ≠ 0, teriamos b = S(b') e:
    b · c = S(b') · c = b' · c + c    ← pela Propriedade 2
  E b' · c + c ≠ 0 pelo fato auxiliar acima. Contradicao.

  Logo b = 0. Portanto a = b = 0.  ✓

H.I.: Suponha que, para todo b, a · c = b · c ∧ c ≠ 0 ⟹ a = b.

Passo indutivo (provar que S(a) · c = b · c ∧ c ≠ 0 ⟹ S(a) = b):

  Temos S(a) · c = b · c.

  Primeiro, mostramos que b ≠ 0:
    S(a) · c = a · c + c               ← pela Propriedade 2
    E a · c + c ≠ 0 pelo fato auxiliar (pois c ≠ 0).
    Logo b · c ≠ 0, o que implica b ≠ 0 (pois se b = 0, teriamos b·c = 0).

  Como b ≠ 0, existe b' tal que b = S(b'). Entao:
    S(b') · c = b' · c + c             ← pela Propriedade 2

  Substituindo na hipotese S(a) · c = b · c:
    a · c + c = b' · c + c

  Pelo cancelamento da ADICAO (cancelamos c):
    a · c = b' · c

  Pela H.I.:
    a = b'

  Logo S(a) = S(b') = b.  ✓

Pelo principio de inducao, a · c = b · c ∧ c ≠ 0 ⟹ a = b
para todo a, b, c ∈ ℕ. □
```

**Observe a cadeia de dependencias desta prova:**

```
Cancelamento da multiplicacao
    usa → Propriedade 1 (0 · a = 0)           — no caso base
    usa → Propriedade 2 (S(a)·b = a·b + b)    — em ambos os passos
    usa → Cancelamento da adicao (a+c = b+c ⟹ a = b) — no passo indutivo
    usa → Axioma de Peano (0 ≠ S(n))          — no fato auxiliar
```

**Comparacao entre os dois cancelamentos:**

```
Cancelamento da adicao:               Cancelamento da multiplicacao:
  a + c = b + c ⟹ a = b               a · c = b · c ∧ c ≠ 0 ⟹ a = b
  Vale para TODO c                      Exige c ≠ 0
  Prova por inducao em c                Prova por inducao em a
  Usa: A2 + S injetora                  Usa: Props 1, 2 + cancel. adicao
```

---

### Resumo: a hierarquia completa das propriedades da multiplicacao

Cada seta (↓) significa "usa o resultado de cima na prova":

```
Definicoes M1, M2  +  Toda a teoria da adicao (A1, A2, comut., assoc.)
    ↓
Propriedade 1: 0 · a = 0              (inducao em a)
    ↓
Propriedade 2: S(a) · b = (a·b) + b   (inducao em b, usa comut. da adicao)
    ↓
Propriedade 3: a · b = b · a           (inducao em b, usa props. 1 e 2)
    ↓                                                    ↑ independentes ↓
Propriedade 4: a·(b+c) = a·b + a·c    (inducao em c, usa assoc. da adicao)
    ↓
Propriedade 5: (a·b)·c = a·(b·c)      (inducao em c, usa prop. 4)
    ↓
Cancelamento: a·c = b·c ∧ c≠0 ⟹ a=b  (inducao em a, usa props. 1, 2 + cancel. adicao)
```

**Props 3 e 4 sao independentes:** nenhuma usa a outra na prova. A ordem 1→2→3→4→5 segue a logica de primeiro completar o paralelo com a adicao (comutatividade), depois introduzir a distributividade (propriedade nova), e por fim a associatividade. O cancelamento vem por ultimo porque depende do cancelamento da adicao (secao anterior).

**Para a prova da disciplina:** se o professor pedir para provar a comutatividade da multiplicacao, voce DEVE mencionar que esta usando as Propriedades 1 e 2. Se pedir a associatividade, mencione a distributividade. Se pedir o cancelamento, mencione as Propriedades 1 e 2 e o cancelamento da adicao. Nao basta "usar" — precisa dizer que esta usando.

---

### Potenciacao: definicao recursiva

Assim como a multiplicacao foi construida a partir da adicao, a potenciacao e construida a partir da multiplicacao.

**A ideia intuitiva:** elevar a a potencia n e "multiplicar a por si mesmo n vezes".

```
a⁰:     multiplico a zero vezes → resultado e 1 (o elemento neutro da multiplicacao)
a¹:     multiplico a uma vez → a
a²:     multiplico a duas vezes → a · a
a³:     multiplico a tres vezes → a · a · a
```

Formalmente:

```
(P1)  a⁰ = 1                      (caso base: qualquer numero elevado a 0 da 1)
(P2)  a^S(n) = aⁿ · a             (passo recursivo: elevar ao proximo
                                    e multiplicar mais uma vez por a)
```

**Leia P2 assim:** "a elevado ao sucessor de n" e o mesmo que "a elevado a n, vezes a". Ou seja, adicionamos mais um "fator" de a.

**Note o padrao — cada operacao e construida sobre a anterior:**

```
Adicao:       m + 0 = m          m + S(n) = S(m + n)        (aplica S repetidamente)
Multiplicacao: m · 0 = 0          m · S(n) = m · n + m       (aplica + repetidamente)
Potenciacao:   a⁰ = 1            a^S(n) = aⁿ · a            (aplica · repetidamente)
```

Cada operacao tem um **caso base** (o elemento neutro) e um **passo recursivo** (que usa a operacao do nivel anterior).

---

### Exemplo passo a passo: calcular 2³

```
2³
= 2^S(2)                    Reescrevemos 3 como S(2)
= 2² · 2                    Aplicamos P2: a^S(n) = aⁿ · a

  Agora precisamos calcular 2²:
  2²
  = 2^S(1)                  Reescrevemos 2 como S(1)
  = 2¹ · 2                  Aplicamos P2

    Agora precisamos calcular 2¹:
    2¹
    = 2^S(0)                Reescrevemos 1 como S(0)
    = 2⁰ · 2               Aplicamos P2

      Agora precisamos calcular 2⁰:
      2⁰ = 1               Caso base! Aplicamos P1.

    Voltando: 2¹ = 1 · 2 = 2

  Voltando: 2² = 2 · 2 = 4

Voltando: 2³ = 4 · 2 = 8   ✓
```

**Observe:** o padrao e identico ao da adicao e multiplicacao. Cada aplicacao de P2 "descasca" um S(…) do expoente. Quando chega em 0, P1 encerra a recursao. Depois, multiplicamos tudo.

---

### Exemplo passo a passo: calcular 3²

```
3²
= 3^S(1)                    [2 = S(1)]
= 3¹ · 3                    [P2]
= (3^S(0)) · 3              [1 = S(0)]
= (3⁰ · 3) · 3              [P2]
= (1 · 3) · 3               [P1: 3⁰ = 1]
= 3 · 3                     [1 · n = n, ja provado]
= 9                          ✓
```

---

### A armadilha da potenciacao: 0ⁿ e 1ⁿ

Assim como nas operacoes anteriores, a definicao fixa a recursao no **expoente** (segundo argumento). Isso traz consequencias:

```
P1 diz:  a⁰ = 1     (o 0 esta no EXPOENTE)

Isso nos da de graca:
  5⁰ = 1  ✓
  100⁰ = 1  ✓
  a⁰ = 1  ✓  (para qualquer a — e literal na definicao)
```

Mas **0ⁿ** tem o 0 na **base**, nao no expoente. E preciso cuidado:

```
0⁰ = 1          ← por P1 (nesta definicao, 0⁰ = 1 por convencao)
0¹ = 0⁰ · 0 = 1 · 0 = 0
0² = 0¹ · 0 = 0 · 0 = 0
```

Para provar que **0^S(n) = 0** para todo n, precisamos de inducao.

#### Prova: 0^S(n) = 0 para todo n ∈ ℕ

```
Caso base (n = 0):
  0^S(0) = 0⁰ · 0             ← por P2
         = 1 · 0               ← por P1
         = 0                    ← por M1 (m · 0 = 0... mas cuidado!)

  Na verdade: 1 · 0 = 0 por M1.  ✓

H.I.: Suponha que 0^S(k) = 0.

Passo indutivo (provar 0^S(S(k)) = 0):
  0^S(S(k))
  = 0^S(k) · 0                ← por P2
  = 0 · 0                      ← pela H.I.
  = 0                           ← por M1  ✓

Pelo principio de inducao, 0^S(n) = 0 para todo n ∈ ℕ. □
```

**Resumindo:** 0⁰ = 1 (pela definicao P1), mas 0ⁿ = 0 para todo n ≥ 1.

Da mesma forma, **1ⁿ = 1** para todo n, e a prova e simples:

#### Prova: 1ⁿ = 1 para todo n ∈ ℕ

```
Caso base (n = 0):
  1⁰ = 1.  (Por P1.)  ✓

H.I.: Suponha que 1^k = 1.

Passo indutivo (provar 1^S(k) = 1):
  1^S(k)
  = 1^k · 1                   ← por P2
  = 1 · 1                      ← pela H.I.
  = 1                           ← pois m · 1 = m (com m = 1)  ✓

Pelo principio de inducao, 1ⁿ = 1 para todo n ∈ ℕ. □
```

---

### Propriedades da potenciacao

Assim como na adicao e na multiplicacao, as propriedades "obvias" precisam ser demonstradas. Cada prova usa inducao e os resultados anteriores.

---

#### Propriedade: aⁿ⁺ᵐ = aⁿ · aᵐ (expoente da soma)

**A intuicao:** a elevado a (n + m) e "multiplicar a por si mesmo n + m vezes", que e o mesmo que "n vezes" seguido de "m vezes".

#### Prova por inducao em m:

```
Caso base (m = 0):
  Lado esquerdo:
    a^(n + 0) = aⁿ              ← por A1 (n + 0 = n)

  Lado direito:
    aⁿ · a⁰ = aⁿ · 1 = aⁿ      ← por P1 e pela identidade m · 1 = m

  Iguais.  ✓

H.I.: Suponha que a^(n + k) = aⁿ · a^k.

Passo indutivo (provar a^(n + S(k)) = aⁿ · a^S(k)):

  Lado esquerdo:
    a^(n + S(k))
    = a^S(n + k)                 ← por A2 (n + S(k) = S(n + k))
    = a^(n + k) · a              ← por P2
    = (aⁿ · a^k) · a            ← pela H.I.

  Lado direito:
    aⁿ · a^S(k)
    = aⁿ · (a^k · a)            ← por P2
    = (aⁿ · a^k) · a            ← pela associatividade da multiplicacao

  Ambos os lados dao (aⁿ · a^k) · a.  ✓

Pelo principio de inducao, a^(n + m) = aⁿ · aᵐ para todo n, m ∈ ℕ. □
```

---

#### Propriedade: (aⁿ)ᵐ = aⁿ·ᵐ (expoente do expoente)

**A intuicao:** elevar aⁿ a potencia m e multiplicar o expoente n por m.

#### Prova por inducao em m:

```
Caso base (m = 0):
  Lado esquerdo:
    (aⁿ)⁰ = 1                   ← por P1

  Lado direito:
    a^(n · 0) = a⁰ = 1          ← por M1 e P1

  Iguais.  ✓

H.I.: Suponha que (aⁿ)^k = a^(n · k).

Passo indutivo (provar (aⁿ)^S(k) = a^(n · S(k))):

  Lado esquerdo:
    (aⁿ)^S(k)
    = (aⁿ)^k · aⁿ              ← por P2
    = a^(n · k) · aⁿ           ← pela H.I.

  Lado direito:
    a^(n · S(k))
    = a^(n · k + n)             ← por M2 (n · S(k) = n · k + n)
    = a^(n · k) · aⁿ           ← pela propriedade a^(p+q) = a^p · a^q

  Ambos os lados dao a^(n · k) · aⁿ.  ✓

Pelo principio de inducao, (aⁿ)ᵐ = aⁿ·ᵐ para todo n, m ∈ ℕ. □
```

---

#### Propriedade: (a · b)ⁿ = aⁿ · bⁿ (potencia do produto)

**A intuicao:** elevar um produto a potencia n e o mesmo que elevar cada fator a n.

#### Prova por inducao em n:

```
Caso base (n = 0):
  Lado esquerdo:
    (a · b)⁰ = 1                ← por P1

  Lado direito:
    a⁰ · b⁰ = 1 · 1 = 1       ← por P1

  Iguais.  ✓

H.I.: Suponha que (a · b)^k = a^k · b^k.

Passo indutivo (provar (a · b)^S(k) = a^S(k) · b^S(k)):

  Lado esquerdo:
    (a · b)^S(k)
    = (a · b)^k · (a · b)       ← por P2
    = (a^k · b^k) · (a · b)     ← pela H.I.

  Lado direito:
    a^S(k) · b^S(k)
    = (a^k · a) · (b^k · b)     ← por P2 (aplicado a cada fator)

  Precisamos mostrar que (a^k · b^k) · (a · b) = (a^k · a) · (b^k · b).

  Reorganizando o lado esquerdo usando associatividade e comutatividade
  da multiplicacao:
    (a^k · b^k) · (a · b)
    = a^k · (b^k · (a · b))     ← associatividade
    = a^k · (b^k · a · b)
    = a^k · (a · b^k · b)       ← comutatividade (b^k · a = a · b^k)
    = (a^k · a) · (b^k · b)     ← associatividade

  Ambos os lados dao (a^k · a) · (b^k · b).  ✓

Pelo principio de inducao, (a · b)ⁿ = aⁿ · bⁿ para todo n ∈ ℕ. □
```

---

### Resumo: a hierarquia da potenciacao

```
Definicoes P1, P2  +  Toda a teoria da adicao e multiplicacao
    ↓
0^S(n) = 0                      (inducao em n)
    ↓
1ⁿ = 1                          (inducao em n)
    ↓
a^(n+m) = aⁿ · aᵐ              (inducao em m, usa assoc. da multiplicacao)
    ↓
(aⁿ)ᵐ = a^(n·m)                (inducao em m, usa propriedade acima)
    ↓
(a·b)ⁿ = aⁿ · bⁿ               (inducao em n, usa comut. e assoc. da multiplicacao)
```

**O padrao se repete:** definicao recursiva → exemplos → armadilhas (0 na base) → propriedades por inducao. E a mesma estrutura da adicao e da multiplicacao, agora num nivel acima.

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
         Prop 1: 0·a=0, Prop 2: S(a)·b=(a·b)+b
         Prop 3: comutatividade, Prop 4: distributividade
         Prop 5: associatividade
    ↓
NIVEL 5: Definicao da potenciacao (P1, P2)
    ↓
NIVEL 6: Propriedades da potenciacao
         (0^S(n)=0, 1ⁿ=1, a^(n+m)=aⁿ·aᵐ, (aⁿ)ᵐ=a^(n·m), (a·b)ⁿ=aⁿ·bⁿ)
    ↓
NIVEL 7: Definicao da ordem (≤, <)
    ↓
NIVEL 8: Propriedades da ordem
         (reflexiva, transitiva, tricotomia, compatibilidade com + e ·)
    ↓
NIVEL 9: Cancelamento da multiplicacao
         (a·c = b·c ∧ c≠0 ⟹ a=b — usa niveis 2 e 4)
```

**Na prova da disciplina:** o mais comum e pedir para voce calcular expressoes usando A1/A2/M1/M2/P1/P2, ou provar alguma propriedade por inducao. Saber "em que nivel" cada resultado esta ajuda a saber o que voce pode usar em cada prova.

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
- As 5 propriedades da multiplicacao seguem uma ordem precisa de dependencia:
  - Prop 1 (0·a=0) e Prop 2 (S(a)·b=(a·b)+b) sao lemas preparatorios
  - Prop 3 (comutatividade) usa Props 1 e 2
  - Prop 4 (distributividade) e independente de Prop 3
  - Prop 5 (associatividade) usa Prop 4
- Os Axiomas de Peano (especialmente S injetora) aparecem como ferramentas nas demonstracoes

## Exercicios de fixacao

**Computacoes — Adicao:**
1. Calcule 3 + 2 usando apenas A1 e A2. Mostre cada passo.
2. Calcule 1 + 3 usando apenas A1 e A2.

**Computacoes — Multiplicacao:**
3. Calcule 3 · 2 usando M1, M2, A1 e A2.
4. Calcule 2 · 2 usando M1, M2, A1 e A2. (Detalhe cada soma intermediaria.)
5. Calcule 4 · 2 usando M1, M2, A1 e A2.
6. Calcule 1 · 3 usando M1, M2, A1 e A2. (Observe como a Prop 1 simplifica o calculo.)

**Computacoes — Potenciacao:**
7. Calcule 2⁴ usando P1, P2, M1, M2, A1 e A2.
8. Calcule 3² usando P1 e P2. (Voce pode usar resultados de multiplicacao ja calculados.)
9. Calcule 1³ usando P1 e P2. (Verifique que bate com 1ⁿ = 1.)
10. Calcule 2⁰ e 0² usando as definicoes. (Observe a diferenca entre base e expoente zero.)

**Provas por inducao — Adicao:**
11. Prove que S(n) = n + 1 para todo n (dica: basta usar A1 e A2, sem inducao).
12. Prove que 0 + n = n para todo n ∈ ℕ.
13. Prove a associatividade: (a + b) + c = a + (b + c) para todo a, b, c ∈ ℕ.

**Provas por inducao — Multiplicacao:**
14. Prove que 0 · n = 0 para todo n ∈ ℕ.
15. Prove que 1 · n = n para todo n ∈ ℕ. (Dica: use M1, M2 e o lema 0 + n = n.)
16. Prove que S(a) · b = (a · b) + b para todo a, b ∈ ℕ. (Dica: inducao em b.)
17. Prove a comutatividade: a · b = b · a para todo a, b ∈ ℕ. (Dica: use as provas 14 e 16.)
18. Prove a distributividade: a · (b + c) = a · b + a · c para todo a, b, c ∈ ℕ.

**Provas por inducao — Potenciacao:**
19. Prove que 1ⁿ = 1 para todo n ∈ ℕ.
20. Prove que 0^S(n) = 0 para todo n ∈ ℕ.
21. Prove que aⁿ⁺ᵐ = aⁿ · aᵐ para todo a, n, m ∈ ℕ. (Dica: inducao em m.)
22. Prove que (a · b)ⁿ = aⁿ · bⁿ para todo a, b, n ∈ ℕ. (Dica: inducao em n.)

**Conceitual:**
23. Por que 0 · n = 0 precisa de prova, mas n · 0 = 0 nao?
24. Na prova de comutatividade de +, quais lemas sao usados?
25. Na prova de comutatividade de ·, quais propriedades sao usadas?
26. Por que a definicao P1 diz que a⁰ = 1 e nao a⁰ = 0?
27. Por que a prova de (aⁿ)ᵐ = aⁿ·ᵐ depende da prova de aⁿ⁺ᵐ = aⁿ · aᵐ?

> **Respostas selecionadas:**
>
> 1- 3+2 = 3+S(1) = S(3+1) = S(3+S(0)) = S(S(3+0)) = S(S(3)) = S(4) = 5. □
>
> 2- 1+3 = 1+S(2) = S(1+2) = S(1+S(1)) = S(S(1+1)) = S(S(1+S(0))) = S(S(S(1+0))) = S(S(S(1))) = S(S(2)) = S(3) = 4. □
>
> 3- 3·2 = 3·S(1) = 3·1 + 3 = (3·S(0)) + 3 = (3·0 + 3) + 3 = (0+3)+3 = 3+3
>    = 3+S(2) = S(3+2) = S(3+S(1)) = S(S(3+1)) = S(S(3+S(0))) = S(S(S(3+0))) = S(S(S(3))) = S(S(4)) = S(5) = 6. □
>
> 6- 1·3 = 1·S(2) = 1·2 + 1. Agora 1·2 = 1·S(1) = 1·1 + 1. Agora 1·1 = 1·S(0) = 1·0 + 1 = 0 + 1 = 1.
>    Voltando: 1·2 = 1 + 1 = 2. Voltando: 1·3 = 2 + 1 = 3. □
>
> 7- 2⁴ = 2³ · 2 = (2² · 2) · 2 = ((2¹ · 2) · 2) · 2 = (((2⁰ · 2) · 2) · 2) · 2
>    = (((1 · 2) · 2) · 2) · 2 = ((2 · 2) · 2) · 2 = (4 · 2) · 2 = 8 · 2 = 16. □
>
> 10- 2⁰ = 1 (por P1). 0² = 0^S(1) = 0¹ · 0 = (0^S(0) · 0) = (0⁰ · 0) · 0 = (1 · 0) · 0 = 0 · 0 = 0.
>     Nota: o expoente zero sempre da 1 (por definicao), mas a base zero da 0 (para expoente ≥ 1). □
>
> 11- n+1 = n+S(0) = S(n+0) = S(n). Logo S(n) = n+1. (Nao precisa de inducao.) □
>
> 15- Base: 1·0 = 0 (por M1). E 0 = 0. ✓.
>     Passo: 1·S(k) = 1·k + 1 (por M2) = k + 1 (pela H.I.) = S(k) (pois n+1 = S(n)). ✓. □
>
> 23- n·0 = 0 e a definicao M1 — e literal. 0·n tem 0 no primeiro argumento,
>     que nao e o argumento da recursao. A definicao so "descasca" o segundo
>     argumento, entao 0·n precisa de inducao para "percorrer" todos os valores de n. □
>
> 24- Sao usados: (1) o lema 0+n = n (no caso base) e (2) o lema S(m)+n = S(m+n) (no passo indutivo).
>
> 25- Sao usadas: (1) Prop 1 (0·a = 0) no caso base e (2) Prop 2 (S(a)·b = (a·b)+b) no passo indutivo.
>
> 26- Porque 1 e o elemento neutro da multiplicacao (a · 1 = a). A potenciacao repete a multiplicacao,
>     entao zero repeticoes deve dar o neutro multiplicativo (1), nao o neutro aditivo (0).
>     Analogia: m + 0 = m (zero somas, neutro da adicao); m · 0 = 0 (zero parcelas); a⁰ = 1 (zero fatores). □
>
> 27- No passo indutivo de (aⁿ)ᵐ, aparece a expressao a^(n·k + n), que precisa ser reescrita como
>     a^(n·k) · aⁿ. Essa reescrita so e possivel com a propriedade a^(p+q) = a^p · a^q.
>     Sem ela, a prova nao fecha. □

## Referencias
- **Terence Tao**, Analysis I, Cap. 2 (adicao) e Cap. 3 (multiplicacao) — tratamento completo
- **Elon Lages Lima**, Curso de Analise Vol.1, Cap. 1
- **UFPR** - Apostila Numeros Naturais — https://docs.ufpr.br/~fernando.avila/Sem2-2023/CMM011/Apostila/N.pdf
- **UChicago** - Peano Arithmetic — http://cmsc-16100.cs.uchicago.edu/2018-autumn/Notes/arithmetic.php
- **Keith Devlin** - "How Multiplication Is Really Defined in Peano Arithmetic"
- **Wikipedia** - Peano Axioms (secao Arithmetic) — https://en.wikipedia.org/wiki/Peano_axioms
