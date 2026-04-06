---
layout: page
title: "6. Inducao Matematica"
nav_order: 6
---
# 6. Inducao Matematica (Fraca e Forte)

## Resumo

### O que e inducao matematica?

Imagine uma fila infinita de dominos, numerados 1, 2, 3, 4, ...

Voce quer garantir que **todos** os dominos caem. Para isso, precisa de exatamente **duas** coisas:

```
1. EMPURRAR o primeiro domino (ele cai de fato).
2. GARANTIR que os dominos estao posicionados de modo que,
   se o domino k cair, ele derruba o domino k+1.
```

Se ambas as condicoes valem:
- O domino 1 cai (pela condicao 1).
- Como o 1 caiu, o 2 cai (pela condicao 2, com k=1).
- Como o 2 caiu, o 3 cai (pela condicao 2, com k=2).
- E assim por diante, **para sempre**.

Na matematica, os "dominos" sao afirmacoes P(1), P(2), P(3), ... que queremos provar verdadeiras. A inducao e a tecnica para provar que **P(n) vale para todo n ≥ n₀**.

---

### Por que AMBAS as condicoes sao necessarias?

Esse ponto e crucial. Veja o que acontece quando falta uma:

**Sem o caso base (nao empurrou o primeiro domino):**

```
"Afirmacao": Para todo n ≥ 1, n² = n.

Passo indutivo: Se k² = k (H.I.), entao (k+1)² = k² + 2k + 1 = k + 2k + 1 = (k+1) + 2k.
... Ops, isso nao funciona. Mas suponha que "funcionasse" — mesmo assim,
sem verificar o caso base, nao temos NENHUM domino caindo.
P(1): 1² = 1? Sim, ok. P(2): 4 = 2? NAO. A afirmacao e falsa.

Os dominos estao la, mas ninguem empurrou o primeiro.
```

**Sem o passo indutivo (dominos separados demais):**

```
"Afirmacao": Para todo n ≥ 1, n < 100.

Base: P(1): 1 < 100? Sim. ✓
Mas nao conseguimos provar que P(k) ⟹ P(k+1).
(Para k = 99: "se 99 < 100, entao 100 < 100" — FALSO.)

O primeiro domino cai, mas nao derruba o segundo.
```

**A licao:** caso base sem passo indutivo = dominos separados. Passo indutivo sem caso base = dominos posicionados mas ninguem empurrou o primeiro. Voce precisa dos DOIS.

---

### A estrutura formal

Para provar que P(n) vale para todo n ≥ n₀:

```
CASO BASE:
  Verificar que P(n₀) e verdadeira.
  (Calcular diretamente, sem truques.)

HIPOTESE DE INDUCAO (H.I.):
  Supor que P(k) e verdadeira para algum k ≥ n₀ arbitrario.
  (Esse e o "presente" que voce GANHA para usar no proximo passo.)

PASSO INDUTIVO:
  Mostrar que P(k+1) e verdadeira, USANDO a H.I.
  (Esse e o trabalho: construir a ponte de P(k) ate P(k+1).)

CONCLUSAO:
  Pelo principio de inducao, P(n) vale para todo n ≥ n₀. □
```

---

### "Mas isso nao e raciocinio circular?"

Essa e a duvida mais comum de quem esta aprendendo inducao. Parece que estamos "assumindo o que queremos provar". Mas **nao estamos**.

Veja a diferenca:

```
CIRCULAR (errado):
  "Quero provar P(n) para todo n.
   Assumo que P(n) vale para todo n.
   Logo, P(n) vale para todo n."

INDUCAO (correto):
  "Quero provar P(n) para todo n.
   Provo P(1) diretamente. ← nenhuma suposicao aqui
   Depois provo uma CONDICIONAL: se P(k), entao P(k+1).
   Junto as duas coisas: P(1) e verdade, logo P(2) e verdade,
   logo P(3) e verdade, ..."
```

O passo indutivo nao diz "P(k) e verdade". Ele diz "**SE** P(k) fosse verdade, **ENTAO** P(k+1) tambem seria". E uma condicional — exatamente como nas provas diretas do topico 4.

Outra forma de pensar: **a inducao prova que a verdade e contagiosa**. O caso base mostra que P(n₀) e verdadeira. O passo indutivo mostra que a verdade "contamina" o proximo caso. Juntos, garantem que todos os casos sao "infectados".

---

### A tecnica essencial: escreva P(k) e P(k+1) ANTES de comecar

Esse e o conselho mais importante deste material. Antes de fazer qualquer conta, escreva explicitamente:

```
P(k):   [a afirmacao com n substituido por k]     ← o que voce ASSUME
P(k+1): [a afirmacao com n substituido por k+1]   ← o que voce DEVE MOSTRAR
```

Depois, compare as duas. Pergunte: **"O que muda de P(k) para P(k+1)? Onde P(k) aparece dentro de P(k+1)?"**

Essa comparacao revela exatamente o que o passo indutivo precisa fazer.

Vamos ver isso na pratica com cada tipo de problema.

---

### Exemplo 1 — Somatorio (o tipo mais classico)

**Enunciado:** Prove que para todo n ≥ 1, 1 + 2 + 3 + ... + n = n(n+1)/2.

**Passo 0 — Escreva P(k) e P(k+1):**
```
P(k):    1 + 2 + ... + k     = k(k+1)/2
P(k+1):  1 + 2 + ... + k + (k+1) = (k+1)(k+2)/2
                         ^^^^^
                     esse termo e novo!
```

Observe: o lado esquerdo de P(k+1) e o lado esquerdo de P(k) **mais (k+1)**. Essa e a chave.

**Prova:**

```
Caso base (n = 1):
  Lado esquerdo: 1.
  Lado direito: 1·2/2 = 1.
  1 = 1. ✓

Hipotese de inducao:
  Suponha que para algum k ≥ 1:
  1 + 2 + ... + k = k(k+1)/2.          ← isso e P(k), nosso "presente"

Passo indutivo (provar P(k+1)):
  Queremos mostrar que 1 + 2 + ... + k + (k+1) = (k+1)(k+2)/2.

  1 + 2 + ... + k + (k+1)
  = [1 + 2 + ... + k] + (k+1)          ← separamos: P(k) + termo novo
  = k(k+1)/2 + (k+1)                   ← AQUI usamos a H.I.! (pela H.I.)
  = k(k+1)/2 + 2(k+1)/2               ← colocando no mesmo denominador
  = [k(k+1) + 2(k+1)] / 2
  = (k+1)(k + 2) / 2                   ← fatoramos (k+1)
  = (k+1)(k+2)/2                        ← isso e exatamente P(k+1)! ✓

Pelo principio de inducao, P(n) vale para todo n ≥ 1. □
```

**O que aconteceu?** O truque foi separar a soma ate k+1 em "soma ate k" + "(k+1)". A "soma ate k" e exatamente P(k), que podemos substituir pela H.I. Depois, foi so algebra.

**Padrao para somatorios:**
```
soma(k+1) = soma(k) + termo(k+1)
                |
                v
           usa H.I. aqui
```

---

### Exemplo 2 — Divisibilidade (exige introduzir variavel da H.I.)

**Enunciado:** Prove que para todo n ≥ 0, 3 | (n³ - n).

Esse tipo de problema tem um detalhe que confunde: quando dizemos "3 | (k³ - k)" pela H.I., isso significa que **existe um inteiro m** tal que k³ - k = 3m. Voce precisa **introduzir esse m** e usa-lo.

**Passo 0 — Escreva P(k) e P(k+1):**
```
P(k):    3 | (k³ - k)         ou seja, ∃m ∈ ℤ, k³ - k = 3m
P(k+1):  3 | ((k+1)³ - (k+1))
```

A estrategia: expandir (k+1)³ - (k+1) e isolar (k³ - k) dentro da expressao.

**Prova:**

```
Caso base (n = 0):
  0³ - 0 = 0 = 3·0. Logo 3 | 0. ✓

Hipotese de inducao:
  Suponha que para algum k ≥ 0:
  3 | (k³ - k), ou seja, k³ - k = 3m para algum m ∈ ℤ.   ← H.I.

Passo indutivo (provar P(k+1)):
  Queremos mostrar que 3 | ((k+1)³ - (k+1)).

  (k+1)³ - (k+1)
  = k³ + 3k² + 3k + 1 - k - 1          ← expandimos (k+1)³
  = k³ + 3k² + 3k - k
  = (k³ - k) + 3k² + 3k                 ← reagrupamos para isolar (k³ - k)
  = (k³ - k) + 3(k² + k)               ← fatoramos o 3

  Agora usamos a H.I.: k³ - k = 3m.     ← AQUI usamos a H.I.

  = 3m + 3(k² + k)
  = 3(m + k² + k)

  Como m + k² + k ∈ ℤ, temos 3 | ((k+1)³ - (k+1)). ✓

Pelo principio de inducao, 3 | (n³ - n) para todo n ≥ 0. □
```

**O que aconteceu?** Expandimos (k+1)³ - (k+1) e reorganizamos os termos para fazer (k³ - k) aparecer. Depois substituimos pela H.I. (que nos deu o "3m") e fatoramos.

**Padrao para divisibilidade:**
```
1. Expanda f(k+1).
2. Reagrupe para isolar f(k) dentro da expressao.
3. Substitua f(k) pelo valor da H.I. (f(k) = d·m).
4. Fatore d na expressao toda.
```

**Dica crucial:** o passo 2 e o mais importante. Se voce nao encontra f(k) dentro de f(k+1), tente rearranjar os termos. Quase sempre da certo.

---

### Exemplo 3 — Desigualdade (o tipo mais dificil — use rascunho!)

**Enunciado:** Prove que para todo n ≥ 1, 2ⁿ > n.

Desigualdades sao mais dificeis porque a H.I. nao substitui diretamente — ela da um **limitante** que voce precisa manipular. A dica e: faca rascunho antes.

**Passo 0 — Escreva P(k) e P(k+1):**
```
P(k):    2^k > k
P(k+1):  2^(k+1) > k + 1
```

**Rascunho (nao faz parte da prova, e so para pensar):**

Vamos com calma. Temos duas informacoes:
```
O que SABEMOS (H.I.):         2^k > k
O que QUEREMOS mostrar:       2^(k+1) > k + 1
```

Começo manipulando o lado esquerdo do que quero mostrar:
```
2^(k+1) = 2 · 2^k
```

Agora posso usar a H.I.! Como 2^k > k, e estou multiplicando por 2 (positivo):
```
2 · 2^k > 2 · k = 2k
```

Otimo! Ja sei que 2^(k+1) > 2k. Mas o que eu QUERIA era 2^(k+1) > k+1.
Sera que o que eu consegui (> 2k) ja e suficiente? Vamos ver com numeros:

```
Para k = 3:   consegui provar 2^(k+1) > 2k = 6.
              Eu queria provar   2^(k+1) > k+1 = 4.
              6 > 4? SIM! Entao ser maior que 6 GARANTE ser maior que 4.

Para k = 10:  consegui provar 2^(k+1) > 2k = 20.
              Eu queria provar   2^(k+1) > k+1 = 11.
              20 > 11? SIM!
```

O padrao: 2k e SEMPRE maior ou igual a k+1 (quando k ≥ 1)?
Vamos verificar: 2k ≥ k+1  ⟺  2k - k ≥ 1  ⟺  k ≥ 1. SIM! ✓

Entao a logica completa e uma CADEIA de desigualdades:
```
2^(k+1) = 2·2^k > 2k ≥ k+1
           ^^^^^^   ^^^^^^^^
           H.I.     pois k ≥ 1
```

Lendo da esquerda para a direita: 2^(k+1) e maior que 2k, que por sua vez
e maior ou igual a k+1. Portanto, 2^(k+1) > k+1. Isso e a **transitividade**:
se A > B e B ≥ C, entao A > C.

**Por que esse segundo passo e necessario?** Porque a H.I. nos levou ate
"2^(k+1) > 2k", mas nosso destino e "2^(k+1) > k+1". Sao afirmacoes
DIFERENTES — 2k e k+1 sao numeros diferentes! Precisamos de um "degrau"
que conecte 2k a k+1. Esse degrau e a verificacao de que 2k ≥ k+1.

**Prova (agora escrita de forma limpa):**

```
Caso base (n = 1):
  2¹ = 2 > 1 = 1. ✓

Hipotese de inducao:
  Suponha que para algum k ≥ 1: 2^k > k.         ← H.I.

Passo indutivo (provar P(k+1)):
  2^(k+1)
  = 2 · 2^k
  > 2 · k           ← pela H.I. (substituimos 2^k > k)
  = k + k
  ≥ k + 1           ← pois k ≥ 1

  Logo 2^(k+1) > k + 1. ✓

Pelo principio de inducao, 2ⁿ > n para todo n ≥ 1. □
```

**Padrao para desigualdades — a ideia da "escada":**

Em somatorios e divisibilidade, a H.I. substitui diretamente uma expressao
(ex: "troco k(k+1)/2 no lugar da soma" ou "troco 3m no lugar de k³-k").
O trabalho acaba ali.

Em desigualdades, a H.I. nao te leva direto ao destino. Ela te leva a um
**ponto intermediario**. Voce precisa entao mostrar que esse ponto intermediario
e suficiente para alcancar o destino. E como subir uma escada com dois degraus:

```
                          DESTINO: 2^(k+1) > k+1
                              ▲
                              │  Degrau 2: mostrar 2k ≥ k+1 (pois k ≥ 1)
                              │
                    PONTO INTERMEDIARIO: 2^(k+1) > 2k
                              ▲
                              │  Degrau 1: usar a H.I. (2^k > k, multiplica por 2)
                              │
                          INICIO: 2^(k+1) = 2 · 2^k
```

O template geral:
```
1. Reescreva a expressao de P(k+1) para fazer f(k) aparecer.
2. Aplique a H.I. como um limitante → voce chega ao PONTO INTERMEDIARIO.
3. Mostre que o ponto intermediario ≥ (ou >) o destino.
   Esse passo 3 e o "segundo degrau" — faca no rascunho!
```

**Dica:** no rascunho, trabalhe DE TRAS PARA FRENTE. Pergunte: "o que eu precisaria
que fosse verdade para a cadeia fechar?" Depois, na prova limpa, escreva para frente.

---

### Exemplo 4 — Desigualdade mais dificil (com argumento auxiliar)

**Enunciado:** Prove que para todo n ≥ 5, 2ⁿ > n².

**Passo 0:**
```
P(k):    2^k > k²
P(k+1):  2^(k+1) > (k+1)²
```

**Rascunho:**
```
2^(k+1) = 2 · 2^k > 2k²  (pela H.I.)

Preciso: 2k² ≥ (k+1)² = k² + 2k + 1
         k² ≥ 2k + 1
         k² - 2k - 1 ≥ 0

Para k ≥ 3: k² - 2k - 1 = k(k-2) - 1 ≥ 3·1 - 1 = 2 > 0. ✓
(E como k ≥ 5 > 3, estamos seguros.)
```

**Prova:**

```
Caso base (n = 5):
  2⁵ = 32 > 25 = 5². ✓

Hipotese de inducao:
  Suponha que para algum k ≥ 5: 2^k > k².

Passo indutivo:
  2^(k+1) = 2 · 2^k > 2k²   (pela H.I.)

  Afirmamos que 2k² ≥ (k+1)² para k ≥ 5.
  De fato: 2k² - (k+1)² = 2k² - k² - 2k - 1 = k² - 2k - 1 = (k-1)² - 2.
  Para k ≥ 5: (k-1)² - 2 ≥ 16 - 2 = 14 > 0. ✓

  Logo 2^(k+1) > 2k² ≥ (k+1)², ou seja, 2^(k+1) > (k+1)². ✓

Pelo principio de inducao, 2ⁿ > n² para todo n ≥ 5. □
```

**Observe:** o caso base comeca em n = 5, nao em n = 1. Isso porque a afirmacao e falsa para n = 2, 3, 4 (por exemplo, 2² = 4 e 2² = 4, entao 4 > 4 e falso). O n₀ pode ser qualquer valor!

---

### O metodo das duas colunas (para quando voce travar)

Se voce esta perdido, organize assim:

```
| O que eu SEI (H.I.)              | O que eu PRECISO MOSTRAR           |
|----------------------------------|-------------------------------------|
| 1+2+...+k = k(k+1)/2            | 1+2+...+k+(k+1) = (k+1)(k+2)/2    |
```

Agora a pergunta e: **como chego da coluna esquerda na coluna direita?**

Para somatorios: "some (k+1) dos dois lados de P(k)".
Para divisibilidade: "expanda f(k+1) e encontre f(k) dentro dela".
Para desigualdades: "multiplique ou some algo nos dois lados de P(k) e compare".

Essa tabela visual e extremamente util quando voce nao sabe por onde comecar.

---

### Onde exatamente voce usa a H.I.? (marque na prova!)

**Regra de ouro:** em toda prova por inducao, deve existir um momento em que voce escreve "pela H.I." ou "(pela hipotese de inducao)". Se voce terminou a prova e nao escreveu isso em lugar nenhum, **algo esta errado.**

Nos exemplos acima, marquei com `← AQUI usamos a H.I.` e `← pela H.I.`. Faca isso nas suas provas tambem. Alem de ajudar na correcao, ajuda VOCE a verificar que a prova esta completa.

```
ALERTA: se voce "provou" P(k+1) sem nunca mencionar P(k),
entao voce fez uma prova direta, nao uma prova por inducao.
Ou a prova esta errada, ou inducao era desnecessaria.
```

---

### Mais um exemplo — Somatorio de quadrados

**Enunciado:** Prove que para todo n ≥ 1, 1² + 2² + ... + n² = n(n+1)(2n+1)/6.

```
P(k):    1² + 2² + ... + k² = k(k+1)(2k+1)/6
P(k+1):  1² + 2² + ... + k² + (k+1)² = (k+1)(k+2)(2k+3)/6
```

**Prova:**

```
Caso base (n = 1):
  Esquerda: 1² = 1.
  Direita: 1·2·3/6 = 6/6 = 1.
  1 = 1. ✓

H.I.: Suponha 1² + 2² + ... + k² = k(k+1)(2k+1)/6.

Passo indutivo:
  1² + 2² + ... + k² + (k+1)²
  = k(k+1)(2k+1)/6 + (k+1)²            ← pela H.I.
  = (k+1) [k(2k+1)/6 + (k+1)]          ← fatoramos (k+1)
  = (k+1) [k(2k+1)/6 + 6(k+1)/6]
  = (k+1) [k(2k+1) + 6(k+1)] / 6
  = (k+1) [2k² + k + 6k + 6] / 6
  = (k+1) [2k² + 7k + 6] / 6
  = (k+1)(k+2)(2k+3) / 6                ← fatoramos o trinomio

  Isso e exatamente P(k+1). ✓

Pelo principio de inducao, vale para todo n ≥ 1. □
```

**Dica:** a fatoracao 2k² + 7k + 6 = (k+2)(2k+3) pode ser verificada: (k+2)(2k+3) = 2k² + 3k + 4k + 6 = 2k² + 7k + 6. ✓

---

### Inducao forte (completa)

#### A ideia central: por que a inducao fraca as vezes nao basta?

Na inducao fraca, para provar P(k+1) voce so pode usar P(k) — o caso **imediatamente anterior**. Isso funciona quando cada caso depende apenas do anterior (como somatorios).

Mas e quando, para provar P(k+1), voce precisa de um caso que **nao e o anterior**? Por exemplo:
- P(k+1) depende de P(k-2) (tres passos atras)
- P(k+1) depende de P(k-1) **e** P(k) (dois termos)
- P(k+1) depende de P(a) e P(b) onde a e b sao **imprevisiveis** (so sabemos que sao menores que k+1)

Nesses casos, a inducao fraca nao basta. Precisamos de algo mais generoso.

---

#### Analogia: escada vs. parede de escalada

```
INDUCAO FRACA = escada:
  Cada degrau so depende do degrau imediatamente abaixo.
  Do degrau k, voce sobe para o degrau k+1.

  [k+1]  ← voce quer chegar aqui
  [k]    ← voce so pode pisar AQUI
  [k-1]
  [k-2]
  ...

INDUCAO FORTE = parede de escalada:
  Para alcancar a posicao k+1, voce pode se apoiar em QUALQUER
  posicao abaixo — k, k-1, k-5, qualquer uma.

  [k+1]  ← voce quer chegar aqui
  [k]    ← pode usar
  [k-1]  ← pode usar
  [k-2]  ← pode usar
  ...    ← pode usar QUALQUER um desses
  [n₀]   ← pode usar
```

---

#### A estrutura formal

```
CASO BASE:
  Verificar P(n₀) (e possivelmente P(n₀+1), P(n₀+2), ...).

HIPOTESE DE INDUCAO (forte):
  Supor que P(j) vale para TODO j com n₀ ≤ j ≤ k.
  (Nao apenas P(k), mas TODOS os anteriores!)

PASSO INDUTIVO:
  Mostrar que P(k+1) e verdadeira, podendo usar qualquer P(j)
  com n₀ ≤ j ≤ k.

CONCLUSAO:
  Pelo principio de inducao forte, P(n) vale para todo n ≥ n₀. □
```

Compare com a inducao fraca:
```
Fraca:   assume P(k)                         → prova P(k+1)
Forte:   assume P(n₀), P(n₀+1), ..., P(k)   → prova P(k+1)
```

A unica diferenca e que a H.I. forte te da **mais informacao** para trabalhar. E como ganhar mais ferramentas na caixa — voce pode usar qualquer uma delas.

---

#### Exemplo 5 — O problema dos selos (o mais simples para comecar)

**Enunciado:** Prove que todo inteiro n ≥ 8 pode ser escrito como 3a + 5b, com a, b ∈ ℕ.

(Ou seja: com selos de 3 centavos e 5 centavos, voce consegue pagar qualquer valor ≥ 8.)

**Primeiro, vamos TENTAR com inducao fraca e ver por que nao funciona:**

```
Tentativa (inducao fraca):
  Base: P(8): 8 = 3 + 5 = 3·1 + 5·1. ✓

  H.I.: Suponha que k = 3a + 5b para algum k ≥ 8.

  Passo: Quero mostrar que k+1 = 3a' + 5b' para algum a', b'.
    k+1 = 3a + 5b + 1  (pela H.I.)

    ...e agora? Preciso "encaixar" esse +1 usando selos de 3 e 5.
    Mas nao existe selo de 1! Nao consigo simplesmente somar 1 a
    uma combinacao de 3s e 5s e obter outra combinacao de 3s e 5s.

    TRAVEI. Saber que P(k) vale nao me ajuda a provar P(k+1).
```

O problema e que "somar 1" nao combina com selos de 3 e 5. Mas "somar 3" sim! Se eu soubesse que P(k-2) vale (ou seja, k-2 = 3a + 5b), entao:

```
k + 1 = (k - 2) + 3 = 3a + 5b + 3 = 3(a+1) + 5b  ✓
```

Eu precisei "voltar 3 passos" (usar P(k-2) em vez de P(k)). Isso e inducao forte!

**Agora com inducao forte:**

```
Casos base:
  P(8):  8  = 3·1 + 5·1.  ✓
  P(9):  9  = 3·3 + 5·0.  ✓
  P(10): 10 = 3·0 + 5·2.  ✓

  (Precisamos de 3 casos base — ja explicaremos por que.)

H.I. (forte): Suponha que para todo j com 8 ≤ j ≤ k (com k ≥ 10):
  j = 3a + 5b para algum a, b ∈ ℕ.

Passo indutivo (provar para k+1, com k+1 ≥ 11):
  Como k+1 ≥ 11, temos (k+1) - 3 = k - 2 ≥ 8.

  Pela H.I. forte, k - 2 = 3a + 5b para algum a, b ∈ ℕ.     ← H.I. em k-2

  Entao: k + 1 = (k - 2) + 3 = 3a + 5b + 3 = 3(a + 1) + 5b.

  Como a+1 ∈ ℕ e b ∈ ℕ, k+1 pode ser escrito como 3a' + 5b'. ✓

Pelo principio de inducao forte, vale para todo n ≥ 8. □
```

**Por que 3 casos base?** Porque no passo indutivo, "voltamos 3 posicoes" (usamos P(k-2), e k+1 - (k-2) = 3). Para k+1 = 11, usamos P(8). Para k+1 = 10, usariamos P(7)... mas 7 < 8! Nao temos P(7). Entao P(10) precisa ser verificado diretamente. O mesmo para P(9) e P(8).

**Regra geral para numero de casos base:**
```
Se o passo indutivo "volta d posicoes" (usa P(k+1-d)),
voce precisa de d casos base.

Volta 1 posicao (usa P(k)):   1 caso base  (como inducao fraca)
Volta 2 posicoes (usa P(k-1)): 2 casos base
Volta 3 posicoes (usa P(k-2)): 3 casos base
...
```

---

#### Exemplo 6 — A barra de chocolate (por que precisamos de TODOS os anteriores)

**Enunciado:** Uma barra de chocolate tem n quadradinhos em formato retangular. Voce quebra a barra escolhendo um pedaco e partindo-o em dois ao longo de uma linha. Prove que sao necessarias exatamente n - 1 quebras para separar todos os n quadradinhos.

Esse exemplo mostra uma situacao diferente: voce nao sabe exatamente "quantos passos" vai voltar. A primeira quebra divide a barra em pedacos de tamanho **imprevisivel**.

**Por que inducao fraca nao funciona:**

```
Tentativa:
  H.I.: Uma barra de k quadradinhos precisa de k-1 quebras.
  Quero mostrar para k+1.

  Ao quebrar uma barra de k+1, obtenho dois pedacos de tamanhos a e b,
  com a + b = k+1.

  Mas a e b podem ser QUALQUER coisa entre 1 e k.
  Se a barra e 3×4 = 12 quadradinhos e eu quebro no meio,
  obtenho pedacos de 6 e 6. Preciso de P(6) e P(6).
  A inducao fraca so me deu P(11). TRAVEI.
```

**Com inducao forte:**

```
Caso base (n = 1):
  1 quadradinho, 0 quebras. 1 - 1 = 0. ✓

H.I. (forte): Suponha que para todo j com 1 ≤ j ≤ k,
  uma barra de j quadradinhos precisa de j - 1 quebras.

Passo indutivo (provar para k+1):
  Pegue uma barra de k+1 quadradinhos. Faca a primeira quebra.
  Voce obtem dois pedacos de tamanhos a e b, com a + b = k+1
  e 1 ≤ a, b ≤ k.

  Pela H.I. forte:
    o pedaco de tamanho a precisa de a - 1 quebras.     ← H.I. em a
    o pedaco de tamanho b precisa de b - 1 quebras.     ← H.I. em b

  Total de quebras = 1 (a primeira) + (a - 1) + (b - 1)
                   = 1 + a + b - 2
                   = a + b - 1
                   = (k+1) - 1 = k.  ✓

Pelo principio de inducao forte, sao necessarias n - 1 quebras. □
```

**O que torna esse exemplo especial?** Nao sabemos de antemao quais valores de j vamos precisar. A primeira quebra pode produzir pedacos de qualquer tamanho. Por isso precisamos da H.I. para **todos** os valores menores — nao da para prever qual vamos usar.

**Comparando os dois exemplos ate agora:**

```
Selos (exemplo 5):        voltamos EXATAMENTE 3 passos (sempre P(k-2))
Barra de chocolate (ex 6): voltamos um numero IMPREVISIVEL de passos

Ambos precisam de inducao forte, mas por motivos diferentes:
  - Selos: o "salto" e fixo mas maior que 1
  - Chocolate: o "salto" e variavel
```

---

#### Exemplo 7 — Todo inteiro ≥ 2 e produto de primos

Agora que a intuicao esta construida, podemos encarar esse exemplo classico.

**Enunciado:** Prove que todo inteiro n ≥ 2 pode ser escrito como produto de numeros primos.

**A ideia e a mesma da barra de chocolate:** se n nao e primo, ele se "quebra" em dois fatores menores. Precisamos da H.I. para esses fatores, que podem ser qualquer coisa entre 2 e n-1.

**Antes da prova formal, vejamos com numeros concretos:**

```
12 e produto de primos?
  12 nao e primo. Entao 12 = 4 × 3.
  3 e primo. ✓
  4 e primo? Nao. 4 = 2 × 2. Ambos primos. ✓
  Logo 12 = 2 × 2 × 3. ✓

Para demonstrar isso formalmente, precisamos saber que o resultado
vale para 4 E para 3 — nao basta saber que vale para 11.
Por isso, inducao forte.
```

**Prova:**

```
Caso base (n = 2):
  2 e primo, logo e produto de primos (ele mesmo). ✓

H.I. (forte): Suponha que para todo inteiro j com 2 ≤ j ≤ k,
  j pode ser escrito como produto de primos.

Passo indutivo (provar para k+1):
  Caso 1: k+1 e primo.
    Entao k+1 ja e um produto de primos (o produto com um unico fator). ✓

  Caso 2: k+1 nao e primo.
    Entao ∃a, b ∈ ℤ com k+1 = a · b, onde 2 ≤ a ≤ k e 2 ≤ b ≤ k.
    Como 2 ≤ a ≤ k, pela H.I. forte, a e produto de primos.    ← H.I. em a
    Como 2 ≤ b ≤ k, pela H.I. forte, b e produto de primos.    ← H.I. em b
    Logo k+1 = a · b tambem e produto de primos. ✓

Pelo principio de inducao forte, todo inteiro n ≥ 2 e produto de primos. □
```

**Por que apenas 1 caso base?** Diferente dos selos, aqui nao "voltamos um numero fixo de passos". Precisamos de P(a) e P(b) onde a, b ≥ 2. O menor valor possivel e 2, que e exatamente nosso caso base. Entao 1 basta.

---

#### Exemplo 8 — Todo inteiro ≥ 2 tem um divisor primo

**Enunciado:** Prove que ∀n ∈ ℤ, n ≥ 2 ⟹ n tem um divisor primo.

A estrutura e a mesma: se n nao e primo, ele tem um divisor menor, e podemos aplicar a H.I. a esse divisor.

**Prova:**

```
Caso base (n = 2):
  2 e primo e 2 | 2. Logo 2 tem um divisor primo (ele mesmo). ✓

H.I. (forte): Suponha que para todo inteiro j com 2 ≤ j ≤ k,
  j tem um divisor primo.

Passo indutivo (provar para k+1):
  Caso 1: k+1 e primo.
    Entao k+1 divide a si mesmo e e primo. ✓

  Caso 2: k+1 nao e primo.
    Entao ∃a com 2 ≤ a < k+1 tal que a | (k+1).
    Como 2 ≤ a ≤ k, pela H.I. forte, a tem um divisor primo p.
    Entao p | a e a | (k+1), logo p | (k+1).     ← transitividade
    Portanto k+1 tem um divisor primo. ✓

Pelo principio de inducao forte, todo n ≥ 2 tem um divisor primo. □
```

---

#### Exemplo 9 — Sequencia recursiva (dois termos anteriores)

**Enunciado:** Seja a sequencia definida por a₁ = 1, a₂ = 3, e aₙ = aₙ₋₁ + 2aₙ₋₂ para n ≥ 3. Prove que aₙ e impar para todo n ≥ 1.

**Por que inducao forte?** A definicao de aₙ usa aₙ₋₁ **e** aₙ₋₂ — dois termos anteriores. A inducao fraca so nos daria aₖ (um termo). Precisamos de dois.

**Por que 2 casos base?** A recorrencia "volta 2 posicoes" (usa aₖ₋₁). Para k+1 = 3 (o primeiro caso do passo indutivo), usamos a₂ e a₁. Ambos precisam estar verificados.

```
P(k):   aₖ e impar
P(k+1): aₖ₊₁ e impar
```

**Prova:**

```
Caso base 1 (n = 1): a₁ = 1, que e impar. ✓
Caso base 2 (n = 2): a₂ = 3, que e impar. ✓

H.I. (forte): Suponha que para todo j com 1 ≤ j ≤ k (com k ≥ 2),
aⱼ e impar.

Passo indutivo (provar para k+1, com k+1 ≥ 3):
  aₖ₊₁ = aₖ + 2aₖ₋₁.

  Pela H.I., aₖ e impar, logo aₖ = 2s + 1 para algum s ∈ ℤ.    ← H.I. em k
  Pela H.I., aₖ₋₁ e impar (pois k-1 ≥ 1).                       ← H.I. em k-1

  aₖ₊₁ = aₖ + 2aₖ₋₁
        = (2s + 1) + 2aₖ₋₁
        = 2(s + aₖ₋₁) + 1

  Como s + aₖ₋₁ ∈ ℤ, aₖ₊₁ e impar. ✓

Pelo principio de inducao forte, aₙ e impar para todo n ≥ 1. □
```

---

#### Resumo: quando usar inducao forte e quantos casos base

**Sinais de que voce precisa de inducao forte:**
```
1. O problema "quebra" k+1 em partes de tamanho imprevisivel
   (ex: fatoracao em primos, barra de chocolate)

2. O problema envolve recorrencia com 2+ termos anteriores
   (ex: Fibonacci, sequencias aₙ = f(aₙ₋₁, aₙ₋₂))

3. O passo indutivo precisa "voltar" mais de 1 posicao
   (ex: selos de 3 e 5, onde voltamos 3 posicoes)

4. Voce tentou inducao fraca e TRAVOU — nao conseguiu usar
   apenas P(k) para chegar em P(k+1)
```

**Quantos casos base?**
```
Se volta d posicoes fixas:    d casos base
Se volta para tamanho imprevisivel:  1 caso base (o menor valor do dominio)
Se a recorrencia usa r termos:  r casos base
```

---

### Comparacao: inducao fraca vs. forte

| Aspecto | Inducao fraca | Inducao forte |
|---|---|---|
| H.I. assume | Apenas P(k) | P(n₀), P(n₀+1), ..., P(k) — todos |
| Usa quando | P(k+1) depende so de P(k) | P(k+1) depende de P(j) para j < k |
| Casos base | Geralmente 1 | Depende de "quantos passos" o passo volta |
| Poder logico | Equivalentes (mesmo poder) | Equivalentes (mesmo poder) |
| Exemplos tipicos | Somas, divisibilidade simples | Fatoracao, sequencias recursivas, "selos" |

**Fato importante:** inducao fraca e forte sao **logicamente equivalentes** — tudo que se prova com uma, pode-se provar com a outra. Inducao forte nao e "mais poderosa" no sentido logico — ela apenas da uma hipotese mais generosa, o que as vezes torna a prova possivel de escrever.

**"Se forte e mais generosa, por que nao usar sempre?"** Voce pode! Nunca e errado usar inducao forte. Mas quando inducao fraca funciona, a prova tende a ser mais limpa e focada. Use forte quando a estrutura do problema exigir.

---

### Erros comuns em provas por inducao

**1. Esquecer o caso base**

Sem o caso base, o passo indutivo nao garante nada. O exemplo classico:

```
"Teorema" FALSO: Em qualquer grupo de n cavalos, todos tem a mesma cor.

Passo indutivo (n = k → n = k+1):
  Considere um grupo de k+1 cavalos. Tire o ultimo: sobram k cavalos.
  Pela H.I., esses k cavalos tem a mesma cor.
  Agora tire o primeiro: sobram k cavalos.
  Pela H.I., esses k cavalos tem a mesma cor.
  Como os dois grupos se sobrepoe, todos os k+1 cavalos tem a mesma cor.

O ERRO: para k = 1, os dois grupos de 1 cavalo NAO se sobrepoe.
O passo indutivo so funciona para k ≥ 2, mas o caso base com n = 2 FALHA.
```

**2. Nao usar a hipotese de inducao**

```
Se voce "provou" P(k+1) sem nunca mencionar P(k),
voce nao fez inducao — fez prova direta.
Ou a prova esta errada, ou inducao nao era necessaria.

REGRA: procure a frase "pela H.I." na sua prova.
Se nao esta la, revise.
```

**3. Usar P(k+1) na prova de P(k+1) (raciocinio circular)**

```
ERRADO:
  "Queremos mostrar 1+2+...+(k+1) = (k+1)(k+2)/2.
   Assumimos que 1+2+...+(k+1) = (k+1)(k+2)/2.  ← CIRCULAR!
   Entao ..."

CERTO:
  "Queremos mostrar 1+2+...+(k+1) = (k+1)(k+2)/2.
   Comecamos pelo lado esquerdo e transformamos ate chegar no direito."
```

**4. Comecar do resultado e chegar numa tautologia**

```
ERRADO:
  "Queremos (k+1)(k+2)/2.
   (k+1)(k+2)/2 = (k+1)(k+2)/2. Verdade!"

Voce comecou assumindo o que queria provar.
Comece SEMPRE pelo lado que voce pode manipular
(geralmente o lado esquerdo de P(k+1)).
```

**5. Nao verificar que a H.I. se aplica (em inducao forte)**

```
Ao usar P(j) para algum j, verifique que j ≥ n₀.
Se j < n₀, a H.I. nao cobre esse valor e a prova tem um buraco.
```

**6. Caso base errado**

```
Se o enunciado diz "para todo n ≥ 5", o caso base e n = 5, nao n = 1!
Se a recorrencia usa dois termos, voce pode precisar de DOIS casos base.
```

---

### Guia pratico: como fazer uma prova por inducao passo a passo

```
ANTES DE ESCREVER:
  □ Identifique P(n): qual e a propriedade que depende de n?
  □ Identifique n₀: a partir de qual valor vale?
  □ Escreva P(k) e P(k+1) explicitamente, lado a lado
  □ Compare: o que muda? Onde P(k) aparece dentro de P(k+1)?

AO ESCREVER:
  □ Caso base: calcule P(n₀) diretamente (mostre as contas!)
  □ H.I.: escreva "suponha que P(k) vale para algum k ≥ n₀"
  □ Passo indutivo: comece de P(k+1) e transforme ate usar P(k)
  □ Marque "pela H.I." no exato momento em que usar
  □ Conclua: "pelo principio de inducao, P(n) vale para todo n ≥ n₀"

DEPOIS DE ESCREVER:
  □ Verifique: usei a H.I.? Onde?
  □ Verifique: o caso base esta certo?
  □ Verifique: nao comecei assumindo P(k+1)?
```

---

### Exemplos com notacao formal e quantificadores

#### Exemplo 10 — Somatorio com notacao sigma

**Enunciado:** Prove que ∀n ∈ ℤ⁺, ∑ᵢ₌₁ⁿ i² = n(n+1)(2n+1)/6.

(Esse e o mesmo exemplo de antes, mas com a notacao formal que aparece em provas.)

```
P(k):    ∑ᵢ₌₁ᵏ i² = k(k+1)(2k+1)/6
P(k+1):  ∑ᵢ₌₁ᵏ⁺¹ i² = (k+1)(k+2)(2k+3)/6

Observe: ∑ᵢ₌₁ᵏ⁺¹ i² = [∑ᵢ₌₁ᵏ i²] + (k+1)²
                          ^^^^^^^^^^^^
                           isso e P(k)!
```

O resto da prova e identico ao Exemplo de somatorio de quadrados acima.

---

#### Exemplo 11 — Divisibilidade com congruencia

**Enunciado:** Prove que ∀n ∈ ℕ, 6 | (n³ + 5n).

**Passo 0:**
```
P(k):    6 | (k³ + 5k)         → k³ + 5k = 6m para algum m ∈ ℤ
P(k+1):  6 | ((k+1)³ + 5(k+1))
```

**Prova:**

```
Caso base (n = 0):
  0³ + 5·0 = 0 = 6·0. Logo 6 | 0. ✓

H.I.: Suponha k³ + 5k = 6m para algum m ∈ ℤ.

Passo indutivo:
  (k+1)³ + 5(k+1)
  = k³ + 3k² + 3k + 1 + 5k + 5
  = (k³ + 5k) + 3k² + 3k + 6
  = (k³ + 5k) + 3k(k+1) + 6

  Pela H.I., k³ + 5k = 6m.                          ← H.I.

  Agora, 3k(k+1): como k e k+1 sao consecutivos,
  um deles e par, logo k(k+1) e par, digamos k(k+1) = 2t.
  Entao 3k(k+1) = 6t.

  (k+1)³ + 5(k+1) = 6m + 6t + 6 = 6(m + t + 1).

  Como m + t + 1 ∈ ℤ, temos 6 | ((k+1)³ + 5(k+1)). ✓

Pelo principio de inducao, 6 | (n³ + 5n) para todo n ∈ ℕ. □
```

**Observe:** alem da H.I., usamos o fato auxiliar de que k(k+1) e sempre par. Em provas por inducao, voce pode (e deve!) usar fatos ja provados — a H.I. nao precisa fazer todo o trabalho sozinha.

---

#### Exemplo 12 — Inducao forte com quantificadores

**Enunciado:** Prove que ∀n ∈ ℤ, n ≥ 8 ⟹ ∃a, b ∈ ℕ tal que n = 3a + 5b.

(Todo inteiro ≥ 8 pode ser escrito como combinacao de moedas de 3 e 5.)

**Por que inducao forte?** Para escrever k+1 = 3a + 5b, podemos usar (k+1) - 3 = k-2, que pode estar bem abaixo de k. Precisamos da H.I. para k-2, nao apenas para k.

```
Casos base:
  n = 8:  8 = 3·1 + 5·1. ✓
  n = 9:  9 = 3·3 + 5·0. ✓
  n = 10: 10 = 3·0 + 5·2. ✓

  (Precisamos de 3 casos base porque o passo "volta 3" pode cair em 8, 9 ou 10.)

H.I. (forte): Suponha que para todo j com 8 ≤ j ≤ k (com k ≥ 10):
∃a, b ∈ ℕ tal que j = 3a + 5b.

Passo indutivo (k+1 ≥ 11):
  Como k+1 ≥ 11, temos (k+1) - 3 = k - 2 ≥ 8.
  Pela H.I. forte, k - 2 = 3a + 5b para alguns a, b ∈ ℕ.    ← H.I.
  Logo k + 1 = (k-2) + 3 = 3a + 5b + 3 = 3(a+1) + 5b.
  Como a+1 ∈ ℕ e b ∈ ℕ, k+1 = 3(a+1) + 5b. ✓

Pelo principio de inducao forte, vale para todo n ≥ 8. □
```

**Dica:** em problemas de "representacao" (escrever n como soma de termos fixos), a ideia e "voltar" um passo de tamanho fixo (aqui, 3) e usar a H.I. no valor menor.

---

## Pontos-chave para a prova
- Sempre explicitar: caso base, hipotese de inducao, passo indutivo
- **Escreva P(k) e P(k+1) explicitamente** antes de comecar o passo indutivo
- A hipotese de inducao deve ser **USADA** no passo indutivo — marque "pela H.I."
- Saber quando usar fraca vs. forte (P(k+1) depende so de P(k), ou de valores anteriores?)
- Caso base errado ou ausente invalida toda a prova
- Para desigualdades, faca rascunho antes
- Inducao fraca e forte sao logicamente equivalentes

## Exercicios de fixacao

**Somatorios:**
1. Prove: ∀n ≥ 1, 1 + 3 + 5 + ... + (2n-1) = n².
2. Prove: ∀n ≥ 1, ∑ᵢ₌₁ⁿ i·(i+1) = n(n+1)(n+2)/3.

**Divisibilidade:**
3. Prove: ∀n ≥ 0, 3 | (n³ - n).
4. Prove: ∀n ≥ 0, 6 | (n³ - n). (Dica: use o exercicio anterior ou adapte.)
5. Prove: ∀n ≥ 1, 4 | (5ⁿ - 1).

**Desigualdades:**
6. Prove: ∀n ≥ 1, 2ⁿ > n.
7. Prove: ∀n ≥ 4, 2ⁿ > n + 5. (Dica: caso base n = 4, argumento auxiliar.)

**Inducao forte:**
8. Prove: todo inteiro n ≥ 2 tem um divisor primo.
9. Seja aₙ definida por a₁ = 1, a₂ = 5, aₙ = 5aₙ₋₁ - 6aₙ₋₂ para n ≥ 3. Prove que aₙ = 3ⁿ - 2ⁿ.

**Com notacao formal:**
10. Prove: ∀n ∈ ℤ⁺, ∑ᵢ₌₁ⁿ (2i - 1) = n².
11. Prove: ∀n ∈ ℕ, n ≥ 1 ⟹ ∑ᵢ₌₀ⁿ 2ⁱ = 2ⁿ⁺¹ - 1.
12. Prove por inducao forte: ∀n ∈ ℤ, n ≥ 12 ⟹ ∃a, b ∈ ℕ tal que n = 4a + 5b.

> **Respostas selecionadas:**
>
> 1- Base: n=1, 2·1-1 = 1 = 1². ✓. Passo: 1+3+...+(2k-1)+(2(k+1)-1) = k² + (2k+1) (pela H.I.) = (k+1)². □
>
> 3- Base: n=0, 0³-0=0, 3|0. ✓. Passo: (k+1)³-(k+1) = k³+3k²+3k+1-k-1 = (k³-k)+3k²+3k = (k³-k)+3(k²+k).
>    Pela H.I., k³-k = 3m. Logo (k+1)³-(k+1) = 3m + 3(k²+k) = 3(m+k²+k). □
>
> 5- Base: n=1, 5¹-1 = 4, 4|4. ✓. Passo: 5^(k+1)-1 = 5·5^k - 1 = 5(5^k-1) + 5-1 = 5(5^k-1)+4.
>    Pela H.I., 5^k-1 = 4m. Logo 5^(k+1)-1 = 5·4m + 4 = 4(5m+1). □
>
> 6- Base: n=1, 2>1. ✓. Passo: 2^(k+1) = 2·2^k > 2k (pela H.I.) = k+k ≥ k+1 (pois k≥1). □
>
> 8- Base: n=2, primo, divide a si mesmo. ✓.
>    Passo (forte): Se k+1 e primo, pronto. Se nao, k+1 = a·b com 2≤a<k+1.
>    Pela H.I., a tem divisor primo p. Logo p|a e a|(k+1), entao p|(k+1). □
>
> 9- Base 1: a₁ = 1, e 3¹ - 2¹ = 1. ✓. Base 2: a₂ = 5, e 3² - 2² = 5. ✓.
>    Passo (forte, k≥2): aₖ₊₁ = 5aₖ - 6aₖ₋₁ = 5(3^k - 2^k) - 6(3^(k-1) - 2^(k-1)) (pela H.I.)
>    = 5·3^k - 5·2^k - 6·3^(k-1) + 6·2^(k-1)
>    = 5·3^k - 2·3^k - 5·2^k + 3·2^k     (pois 6·3^(k-1) = 2·3^k e 6·2^(k-1) = 3·2^k)
>    = 3·3^k - 2·2^k = 3^(k+1) - 2^(k+1). □
>
> 11- Base: n=1, 2⁰+2¹ = 3 = 2²-1. ✓. Passo: ∑ᵢ₌₀^(k+1) 2ⁱ = [∑ᵢ₌₀^k 2ⁱ] + 2^(k+1)
>     = (2^(k+1)-1) + 2^(k+1) (pela H.I.) = 2·2^(k+1) - 1 = 2^(k+2) - 1. □
>
> 12- Bases: 12=4·3+5·0, 13=4·2+5·1, 14=4·1+5·2, 15=4·0+5·3.
>     Passo (forte, k+1≥16): (k+1)-4 = k-3 ≥ 12. Pela H.I., k-3 = 4a+5b.
>     Logo k+1 = 4(a+1)+5b. □

## Referencias
- **Rosen**, Secao 5.1 (fraca) e 5.2 (forte)
- **Book of Proof** (Hammack), Cap. 10 — https://www.people.vcu.edu/~rhammack/BookOfProof/
- **How to Prove It** (Velleman), Cap. 6
- **MIT OCW 6.042J** — Lectures 2-3: Induction
- **Concrete Mathematics** (Graham, Knuth, Patashnik)
- **Trefor Bazett** - Mathematical Induction playlist (YouTube, EN)
- **Neso Academy** - Mathematical Induction (YouTube, EN)
- **Programacao Dinamica** (YouTube, PT) — https://www.youtube.com/@ProgramacaoDinamica
