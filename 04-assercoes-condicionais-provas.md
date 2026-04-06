---
layout: page
title: "4. Provas Diretas e Indiretas"
nav_order: 4
---
# 4. Assercoes Condicionais: Provas Diretas e Indiretas

## Resumo

### O que e uma assercao condicional?

Uma assercao condicional e uma afirmacao do tipo **"se ... entao ..."**. Na matematica, escrevemos **p → q**.

```
p → q    "se p, entao q"

p = hipotese (antecedente)  — a condicao, o "gatilho"
q = conclusao (consequente) — o que segue, a "consequencia"
```

Exemplo do dia a dia: "Se chover, entao eu levo guarda-chuva."
- p = "chove"
- q = "eu levo guarda-chuva"

A condicional faz uma **promessa**: sempre que p acontecer, q tambem acontece. A unica forma de quebrar essa promessa e p ser verdadeiro e q ser falso.

---

### Entendendo a tabela-verdade da condicional

A parte mais contra-intuitiva da logica esta aqui. Vamos analisar caso a caso:

| p | q | p → q | Por que? |
|---|---|---|---|
| V | V | **V** | Choveu e levei guarda-chuva. Promessa cumprida. |
| V | F | **F** | Choveu e NAO levei guarda-chuva. **Promessa quebrada!** |
| F | V | **V** | Nao choveu, mas levei guarda-chuva mesmo assim. Nao quebrei a promessa. |
| F | F | **V** | Nao choveu e nao levei. A promessa so falava de dias de chuva, entao esta ok. |

A regra essencial: **p → q so e FALSO quando p e V e q e F.** Em todos os outros casos, e verdadeiro.

Os casos em que p e falso (linhas 3 e 4) sao chamados de **vacuamente verdadeiros** — a promessa nao foi "testada", entao nao pode ter sido quebrada. Isso confunde no inicio, mas e fundamental:

```
"Se 2 + 2 = 5, entao eu sou o presidente do Brasil."  → VERDADEIRO!

Por que? A hipotese (2+2=5) e FALSA. Quando a hipotese e falsa,
a condicional e verdadeira independentemente da conclusao.
A promessa nunca e "ativada".
```

---

### As muitas formas de dizer p → q

A mesma condicional pode ser expressa de varias formas em portugues. Isso e fonte comum de confusao, entao vale decorar:

Considere p → q onde p = "chove" e q = "a rua fica molhada":

| Forma em portugues | Exemplo |
|---|---|
| Se p, entao q | Se chove, entao a rua fica molhada |
| p implica q | Chover implica a rua ficar molhada |
| p somente se q | Chove somente se a rua fica molhada |
| q se p | A rua fica molhada se chove |
| p e condicao **suficiente** para q | Chover e suficiente para a rua ficar molhada |
| q e condicao **necessaria** para p | A rua ficar molhada e necessario para chover |

**Cuidado com "somente se":** a frase "p somente se q" parece dizer que q → p, mas na verdade significa p → q. Leia como "p so acontece se q acontecer", ou seja, "se p aconteceu, q necessariamente aconteceu".

**Suficiente vs. necessario:**
```
"p e suficiente para q"  →  p → q   (p basta para garantir q)
"p e necessario para q"  →  q → p   (sem p, q nao acontece)

Exemplo: "Ser brasileiro e suficiente para ser sul-americano"  → brasileiro → sul-americano
          "Ser sul-americano e necessario para ser brasileiro"  → brasileiro → sul-americano
          (mesma condicional, lida de perspectivas diferentes!)
```

---

### Formas relacionadas: contrapositiva, reciproca e inversa

Dada a condicional p → q, podemos gerar tres novas afirmacoes. Apenas UMA delas e equivalente a original:

| Nome | Forma | Equivalente a p → q? |
|---|---|---|
| **Original** | p → q | — |
| **Contrapositiva** | ¬q → ¬p | **SIM** (sempre!) |
| **Reciproca (conversa)** | q → p | **NAO** |
| **Inversa** | ¬p → ¬q | **NAO** (mas equivale a reciproca) |

**Exemplo concreto com todas as formas:**

Original: "Se e quadrado, entao tem 4 lados." (V)

```
Contrapositiva: "Se nao tem 4 lados, entao nao e quadrado." (V) ← EQUIVALENTE
Reciproca:      "Se tem 4 lados, entao e quadrado." (F! pentagono nao, mas retangulo tem 4 lados e nao e quadrado)
Inversa:        "Se nao e quadrado, entao nao tem 4 lados." (F! retangulo)
```

Observe o padrao: a reciproca e a inversa sao equivalentes ENTRE SI, mas NAO equivalem a original.

**Por que a contrapositiva e equivalente?**

Compare as tabelas-verdade:

```
p → q:      so e F quando p=V e q=F
¬q → ¬p:   so e F quando ¬q=V e ¬p=F, ou seja, q=F e p=V

Mesma condicao! Portanto, sao logicamente equivalentes.
```

**Erro classico a evitar:** confundir a contrapositiva com a reciproca.

```
"Se estudei, entao passei na prova."        (original: p → q)
"Se passei na prova, entao estudei."        (reciproca: q → p — NAO equivalente!)
"Se nao passei na prova, entao nao estudei." (contrapositiva: ¬q → ¬p — EQUIVALENTE!)

A reciproca pode ser falsa: voce pode ter passado colando.
A contrapositiva e tao verdadeira quanto a original.
```

---

### Prova direta

**Estrategia:** Para provar p → q, assuma que p e verdadeiro e, passo a passo, deduza que q e verdadeiro.

**Por que funciona?** Lembre da tabela-verdade: p → q so e falso quando p=V e q=F. Se mostramos que, partindo de p=V, sempre chegamos em q=V, eliminamos o unico caso de falsidade.

**Estrutura:**
```
Suponha que p e verdadeiro.
[passo 1: use a definicao de p]
[passo 2: manipule algebricamente]
...
Portanto, q e verdadeiro. □
```

**Exemplo 1 — Paridade:** Provar "se n e par, entao n² e par".

```
Prova:
  Suponha que n e par.                    ← assumimos a hipotese
  Entao n = 2k para algum inteiro k.     ← usamos a DEFINICAO de par
  Logo, n² = (2k)² = 4k² = 2(2k²).      ← manipulacao algebrica
  Como 2k² e inteiro, n² = 2·(inteiro).  ← isso e a definicao de par!
  Portanto, n² e par. □
```

**Exemplo 2 — Soma:** Provar "se m e n sao inteiros impares, entao m + n e par".

```
Prova:
  Suponha que m e n sao impares.
  Entao m = 2a + 1 e n = 2b + 1 para inteiros a, b.  ← definicao de impar
  Logo, m + n = (2a + 1) + (2b + 1) = 2a + 2b + 2 = 2(a + b + 1).
  Como a + b + 1 e inteiro, m + n e par. □
```

**Exemplo 3 — Divisibilidade:** Provar "se a | b e b | c, entao a | c".
(Lembre: "a | b" significa "a divide b", ou seja, b = a·k para algum inteiro k)

```
Prova:
  Suponha que a | b e b | c.
  Entao b = a·k para algum inteiro k, e c = b·j para algum inteiro j.
  Logo, c = b·j = (a·k)·j = a·(kj).
  Como kj e inteiro, a | c. □
```

Perceba o padrao: (1) assumir hipotese, (2) abrir as definicoes, (3) manipular, (4) reconhecer a definicao da conclusao.

---

### Prova pela contrapositiva (indireta)

**Estrategia:** Em vez de provar p → q diretamente, provar a contrapositiva ¬q → ¬p. Como sao equivalentes, provar uma e provar a outra.

**Quando usar?** Quando a hipotese p nao oferece "material" facil de manipular, mas a negacao da conclusao (¬q) sim. Tipicamente quando:
- A conclusao envolve "nao" ou uma negacao
- Assumir q diretamente nao leva a lugar nenhum
- Assumir ¬q nos da uma forma algebrica util

**Estrutura:**
```
Provaremos a contrapositiva: ¬q → ¬p.
Suponha que ¬q (a conclusao e falsa).
[passo 1]
[passo 2]
...
Portanto, ¬p (a hipotese e falsa). □
```

**Exemplo 1 — Paridade ao quadrado:** Provar "se n² e par, entao n e par".

Por que nao prova direta? A hipotese "n² e par" nos da n² = 2k... e agora? Tirar raiz de 2k nao leva a uma forma limpa. Mas a contrapositiva troca a direcao:

```
Contrapositiva: "se n e impar, entao n² e impar."

Prova:
  Suponha que n e impar.                              ← assumimos ¬q
  Entao n = 2k + 1 para algum inteiro k.
  Logo, n² = (2k+1)² = 4k² + 4k + 1 = 2(2k²+2k) + 1.
  Como 2k²+2k e inteiro, n² e impar.                  ← concluimos ¬p
  Portanto, pela contrapositiva, se n² e par entao n e par. □
```

**Exemplo 2 — Envolvendo produto:** Provar "se xy e impar, entao x e impar e y e impar".

Direta seria complicada (xy = 2k+1 nao nos diz muito sobre x e y individualmente).
Contrapositiva: "se x e par ou y e par, entao xy e par."

```
Prova:
  Suponha que x e par ou y e par.
  Caso 1: x e par. Entao x = 2k, logo xy = 2k·y = 2(ky), que e par.
  Caso 2: y e par. Entao y = 2k, logo xy = x·2k = 2(xk), que e par.
  Em ambos os casos, xy e par.
  Portanto, pela contrapositiva, se xy e impar entao x e y sao impares. □
```

Note como a negacao de "x impar E y impar" e "x par OU y par" (De Morgan!).

**Exemplo 3 — Com numeros reais:** Provar "se x + y ≥ 2, entao x ≥ 1 ou y ≥ 1".

Contrapositiva: "se x < 1 e y < 1, entao x + y < 2."

```
Prova:
  Suponha que x < 1 e y < 1.
  Somando as desigualdades: x + y < 1 + 1 = 2.
  Portanto, pela contrapositiva, se x + y ≥ 2 entao x ≥ 1 ou y ≥ 1. □
```

---

### Comparacao: quando usar cada tecnica

| Situacao | Tecnica | Por que |
|---|---|---|
| A hipotese tem definicao facil de "abrir" | Direta | Ex: "n e par" da n=2k, pronto pra manipular |
| A conclusao tem definicao facil de negar | Contrapositiva | Ex: negar "n e par" da "n e impar", que tem forma algebrica util |
| A hipotese envolve produto/composicao | Contrapositiva | Ex: "xy e impar" e dificil de decompor; negar a conclusao e mais simples |
| A conclusao tem "ou" | Contrapositiva | Negar "A ou B" da "¬A e ¬B" (De Morgan), que costuma ser mais forte |
| A hipotese tem "e" | Direta | Voce tem duas informacoes para trabalhar |

Dica pratica: tente a prova direta primeiro. Se travar (nao sabe o proximo passo), escreva a contrapositiva e tente de novo.

---

### Condicionais com "ou" e "e"

Na pratica, hipoteses e conclusoes raramente sao atomicas — muitas vezes envolvem "ou" (∨) e "e" (∧). Saber como lidar com eles e essencial para montar provas corretamente.

---

#### "E" (∧) na hipotese — voce GANHA duas informacoes

Quando a hipotese e "p₁ e p₂", assuma que **ambas** sao verdadeiras ao mesmo tempo. Voce tem duas ferramentas para trabalhar.

**Exemplo:** Provar "se n e par **e** n > 2, entao n nao e primo".

```
Prova:
  Suponha que n e par e n > 2.
  Como n e par, n = 2k para algum inteiro k.
  Como n > 2, temos 2k > 2, logo k > 1.
  Entao n = 2·k onde 2 ≥ 2 e k ≥ 2, ou seja, n tem um divisor
  diferente de 1 e de si mesmo.
  Portanto, n nao e primo. □
```

Note como **usamos as duas partes** da hipotese: "par" nos deu a forma n = 2k, e "n > 2" nos garantiu que k > 1.

---

#### "E" (∧) na conclusao — voce DEVE provar as duas partes

Se a conclusao e "q₁ e q₂", voce precisa provar **cada parte separadamente**. A prova nao esta completa se so provar uma.

**Exemplo:** Provar "se n² = 4, entao n e par **e** |n| = 2".

```
Prova:
  Suponha que n² = 4. Entao n = 2 ou n = -2.

  Parte 1 (n e par):
    Se n = 2: 2 = 2·1, par. ✓
    Se n = -2: -2 = 2·(-1), par. ✓

  Parte 2 (|n| = 2):
    Se n = 2: |2| = 2. ✓
    Se n = -2: |-2| = 2. ✓

  Portanto, n e par e |n| = 2. □
```

---

#### "Ou" (∨) na hipotese — voce deve considerar CADA CASO

Quando a hipotese e "p₁ ou p₂", voce nao sabe qual das duas e verdadeira. Entao deve provar que a conclusao vale em **cada caso separadamente** (prova por casos).

**Exemplo:** Provar "se n e divisivel por 2 **ou** n e divisivel por 3, entao n² + 5n e par ou divisivel por 3".

Isso pode parecer complexo, entao vamos com algo mais limpo:

**Exemplo:** Provar "se x = 2 **ou** x = -2, entao x² = 4".

```
Prova:
  Suponha que x = 2 ou x = -2.

  Caso 1: x = 2.
    x² = 2² = 4. ✓

  Caso 2: x = -2.
    x² = (-2)² = 4. ✓

  Em ambos os casos, x² = 4. □
```

**Exemplo mais elaborado:** Provar "se n e divisivel por 4 **ou** n e divisivel por 6, entao n e par".

```
Prova:
  Suponha que 4 | n ou 6 | n.

  Caso 1: 4 | n.
    Entao n = 4k = 2(2k) para algum inteiro k. Logo n e par. ✓

  Caso 2: 6 | n.
    Entao n = 6k = 2(3k) para algum inteiro k. Logo n e par. ✓

  Em ambos os casos, n e par. □
```

---

#### "Ou" (∨) na conclusao — basta provar UMA das partes

Se a conclusao e "q₁ ou q₂", voce so precisa mostrar que **pelo menos uma** e verdadeira. Muitas vezes basta encaminhar a prova ate encontrar qual delas sai naturalmente.

**Exemplo:** Provar "se n² e par, entao n e par **ou** n = 0".

```
Prova:
  Suponha que n² e par.
  Pela contrapositiva (ja provada antes), n e par.
  Como n e par, a disjuncao "n e par ou n = 0" e verdadeira
  (basta uma parte ser verdadeira). □
```

Mas existe uma tecnica mais poderosa para conclusoes com "ou": **assumir que uma parte e falsa e provar a outra**. Isso funciona porque:

```
p → (q₁ ∨ q₂)   e equivalente a   (p ∧ ¬q₁) → q₂
```

**Por que?** Se a conclusao "q₁ ou q₂" deve ser verdadeira e q₁ e falso, entao q₂ obrigatoriamente e verdadeiro.

**Exemplo:** Provar "se n e inteiro, entao n e par **ou** n e impar".

```
Prova:
  Suponha que n e inteiro e que n NAO e par.     ← assumimos ¬q₁
  Entao, pela divisao euclidiana por 2, n = 2k + r com r ∈ {0, 1}.
  Como n nao e par, r ≠ 0, logo r = 1.
  Entao n = 2k + 1, ou seja, n e impar.          ← provamos q₂
  Portanto, n e par ou n e impar. □
```

**Exemplo:** Provar "para todo inteiro n, n(n+1) e divisivel por 2".

(Podemos reformular como: "n e par **ou** n+1 e par".)

```
Prova:
  Seja n um inteiro. Suponha que n NAO e par.     ← assumimos ¬q₁
  Entao n e impar, logo n = 2k + 1.
  Entao n + 1 = 2k + 2 = 2(k+1), que e par.      ← provamos q₂
  Em qualquer caso, pelo menos um entre n e n+1 e par,
  logo n(n+1) e divisivel por 2. □
```

---

#### Interacao entre "ou"/"e" e a contrapositiva (De Morgan)

As leis de De Morgan sao o elo entre "ou", "e" e negacao. Quando voce toma a contrapositiva, elas transformam:

```
¬(A ∧ B) = ¬A ∨ ¬B     (negar "e" vira "ou")
¬(A ∨ B) = ¬A ∧ ¬B     (negar "ou" vira "e")
```

Isso muda a estrutura da prova:

| Original | Contrapositiva | Efeito |
|---|---|---|
| (p₁ **∧** p₂) → q | ¬q → (¬p₁ **∨** ¬p₂) | Hipotese "e" vira conclusao "ou" |
| (p₁ **∨** p₂) → q | ¬q → (¬p₁ **∧** ¬p₂) | Hipotese "ou" vira hipotese "e" (mais forte!) |
| p → (q₁ **∧** q₂) | (¬q₁ **∨** ¬q₂) → ¬p | Conclusao "e" vira hipotese "ou" (casos!) |
| p → (q₁ **∨** q₂) | (¬q₁ **∧** ¬q₂) → ¬p | Conclusao "ou" vira hipotese "e" (mais forte!) |

**A regra de ouro:** se a contrapositiva transforma um "ou" em "e", ela provavelmente facilita a prova — porque "e" te da mais informacao.

**Exemplo completo:** Provar "se x² ≥ 1, entao x ≥ 1 **ou** x ≤ -1".

Direta: como usar x² ≥ 1 para concluir um "ou"? Complicado.
Contrapositiva: "se x < 1 **e** x > -1, entao x² < 1."

```
Prova (contrapositiva):
  Suponha que x < 1 e x > -1, ou seja, -1 < x < 1.  ← "ou" virou "e"!
  Como |x| < 1, temos x² = |x|² < 1² = 1.
  Portanto, pela contrapositiva, se x² ≥ 1 entao x ≥ 1 ou x ≤ -1. □
```

Observe: o "ou" na conclusao virou "e" na hipotese da contrapositiva, tornando a prova muito mais simples.

---

#### Resumo visual: "ou" e "e" em provas

```
HIPOTESE com "E":     voce tem duas informacoes → use ambas
HIPOTESE com "OU":    voce nao sabe qual vale → faca prova por CASOS

CONCLUSAO com "E":    voce deve provar AMBAS as partes
CONCLUSAO com "OU":   basta provar UMA, ou assumir ¬q₁ e provar q₂

CONTRAPOSITIVA:       "e" ↔ "ou" se invertem (De Morgan)
                      isso costuma simplificar a prova!
```

---

### Prova de bicondicional (p ↔ q)

O bicondicional "p se e somente se q" (p ↔ q) significa que p e q sao equivalentes: um vale exatamente quando o outro vale.

**Para provar p ↔ q, prove DUAS condicionais:**
```
1. p → q   (direcao "ida": se p entao q)
2. q → p   (direcao "volta": se q entao p)
```

Cada direcao pode usar a tecnica mais adequada (direta ou contrapositiva).

**Exemplo:** Provar "n e par se e somente se n² e par".

```
Direcao 1 (→): "Se n e par, entao n² e par."
  Prova direta: n = 2k → n² = 4k² = 2(2k²), par. ✓

Direcao 2 (←): "Se n² e par, entao n e par."
  Prova pela contrapositiva: "Se n e impar, entao n² e impar."
  n = 2k+1 → n² = 4k²+4k+1 = 2(2k²+2k)+1, impar. ✓

Como ambas as direcoes foram provadas, n e par ↔ n² e par. □
```

Note que cada direcao usou a tecnica mais natural: ida por prova direta, volta por contrapositiva.

---

### Erros comuns ao trabalhar com condicionais

**1. Confundir condicional com bicondicional**
```
"Se chove, a rua fica molhada"  ≠  "Chove se e somente se a rua esta molhada"
 (p → q)                           (p ↔ q)

A rua pode estar molhada por outros motivos (lavagem, enchente).
p → q nao garante q → p!
```

**2. Afirmar o consequente (falacia)**
```
"Se chove, a rua fica molhada."   (p → q)
"A rua esta molhada."             (q)
"Logo, choveu."                   (p)  ← ERRADO!

Isso e usar a reciproca (q → p) como se fosse a original.
```

**3. Negar o antecedente (falacia)**
```
"Se chove, a rua fica molhada."   (p → q)
"Nao choveu."                     (¬p)
"Logo, a rua nao esta molhada."   (¬q) ← ERRADO!

Isso e usar a inversa (¬p → ¬q) como se fosse a original.
```

**4. Trocar a contrapositiva pela reciproca**
```
Original:       "Se e gato, entao e animal."       (V)
Contrapositiva: "Se nao e animal, entao nao e gato." (V) ← esta e equivalente
Reciproca:      "Se e animal, entao e gato."          (F) ← esta NAO e equivalente
```

## Pontos-chave para a prova
- Contrapositiva ≡ original (mesma tabela-verdade) — reciproca NAO
- Numa prova direta, voce ASSUME a hipotese e DEDUZ a conclusao
- Numa prova por contrapositiva, voce ASSUME ¬conclusao e DEDUZ ¬hipotese
- Bicondicional exige provar as duas direcoes
- Cuidado com as falacias: afirmar o consequente e negar o antecedente

## Exemplos com notacao formal e quantificadores

Na prova, os enunciados costumam aparecer com simbolos matematicos (∀, ∃, |, ≡) e definicoes formais. Abaixo estao as definicoes mais usadas e exemplos resolvidos nessa linguagem.

### Definicoes formais recorrentes

```
Par:            n e par   ⟺  ∃k ∈ ℤ, n = 2k
Impar:          n e impar ⟺  ∃k ∈ ℤ, n = 2k + 1
Divisibilidade: a | b     ⟺  ∃k ∈ ℤ, b = ak
Congruencia:    a ≡ b (mod n)  ⟺  n | (a - b)  ⟺  ∃k ∈ ℤ, a - b = nk
```

A chave para resolver esses exercicios e a mesma: **abrir a definicao**, manipular algebricamente, e **reconhecer a definicao** no resultado.

---

### Exemplo 1 — Prova direta com congruencia (soma)

**Enunciado:** Prove que ∀a, b, c, d ∈ ℤ, ∀n ∈ ℤ⁺, (a ≡ b (mod n) ∧ c ≡ d (mod n)) ⟹ a + c ≡ b + d (mod n).

```
Prova:
  Sejam a, b, c, d ∈ ℤ e n ∈ ℤ⁺.
  Suponha que a ≡ b (mod n) e c ≡ d (mod n).

  Pela definicao de congruencia:
    n | (a - b)  ⟹  ∃k₁ ∈ ℤ, a - b = nk₁
    n | (c - d)  ⟹  ∃k₂ ∈ ℤ, c - d = nk₂

  Entao:
    (a + c) - (b + d) = (a - b) + (c - d) = nk₁ + nk₂ = n(k₁ + k₂).

  Como k₁ + k₂ ∈ ℤ, temos n | ((a + c) - (b + d)).
  Portanto, a + c ≡ b + d (mod n). □
```

Note o padrao: abrimos a definicao de congruencia (∃k tal que...), manipulamos, e reconhecemos a definicao no resultado.

---

### Exemplo 2 — Prova direta com congruencia (produto)

**Enunciado:** Prove que ∀a, b ∈ ℤ, (a ≡ 1 (mod 3) ∧ b ≡ 1 (mod 3)) ⟹ ab ≡ 1 (mod 3).

```
Prova:
  Sejam a, b ∈ ℤ. Suponha que a ≡ 1 (mod 3) e b ≡ 1 (mod 3).

  Pela definicao:
    ∃k₁ ∈ ℤ, a - 1 = 3k₁  ⟹  a = 3k₁ + 1
    ∃k₂ ∈ ℤ, b - 1 = 3k₂  ⟹  b = 3k₂ + 1

  Entao:
    ab = (3k₁ + 1)(3k₂ + 1)
       = 9k₁k₂ + 3k₁ + 3k₂ + 1
       = 3(3k₁k₂ + k₁ + k₂) + 1.

  Logo ab - 1 = 3(3k₁k₂ + k₁ + k₂).
  Como 3k₁k₂ + k₁ + k₂ ∈ ℤ, temos 3 | (ab - 1), ou seja, ab ≡ 1 (mod 3). □
```

---

### Exemplo 3 — Contrapositiva com divisibilidade

**Enunciado:** Prove que ∀n ∈ ℤ, 3 ∤ n² ⟹ 3 ∤ n.

(Lembre: 3 ∤ n significa "3 nao divide n".)

```
Contrapositiva: ∀n ∈ ℤ, 3 | n ⟹ 3 | n².

Prova:
  Seja n ∈ ℤ. Suponha que 3 | n.
  Pela definicao, ∃k ∈ ℤ tal que n = 3k.
  Entao n² = (3k)² = 9k² = 3(3k²).
  Como 3k² ∈ ℤ, temos 3 | n².
  Portanto, pela contrapositiva, 3 ∤ n² ⟹ 3 ∤ n. □
```

---

### Exemplo 4 — Prova direta com combinacao linear

**Enunciado:** Prove que ∀a, b ∈ ℤ, ∀d ∈ ℤ⁺, (d | a ∧ d | b) ⟹ ∀x, y ∈ ℤ, d | (ax + by).

```
Prova:
  Sejam a, b ∈ ℤ e d ∈ ℤ⁺. Suponha que d | a e d | b.

  Pela definicao:
    ∃k₁ ∈ ℤ, a = dk₁
    ∃k₂ ∈ ℤ, b = dk₂

  Sejam x, y ∈ ℤ quaisquer. Entao:
    ax + by = dk₁x + dk₂y = d(k₁x + k₂y).

  Como k₁x + k₂y ∈ ℤ, temos d | (ax + by). □
```

Esse resultado e importante: se d divide a e b, entao d divide **qualquer combinacao linear** de a e b.

---

### Exemplo 5 — Refutacao por contraexemplo

Nem toda afirmacao universal e verdadeira. Para **refutar** ∀x, P(x), basta exibir **um** contraexemplo: ∃x tal que ¬P(x).

**Enunciado:** Refute: ∀n ∈ ℤ, n² > n.

```
Contraexemplo: tome n = 0.
  n² = 0² = 0 e n = 0.
  Temos 0 > 0, que e FALSO.
  Portanto, a afirmacao e falsa. □
```

**Enunciado:** Refute: ∀a, b ∈ ℤ, (a | bc ⟹ a | b ∨ a | c).

```
Contraexemplo: tome a = 6, b = 4, c = 3.
  bc = 12 e 6 | 12 (pois 12 = 6·2). ✓
  Mas 6 ∤ 4 e 6 ∤ 3.
  Logo a hipotese vale, mas a conclusao e falsa. □
```

---

### Exemplo 6 — Prova existencial (∃)

Para provar ∃x, P(x), basta **exibir** um x que satisfaca P. Para provar ∀x, P(x), voce deve provar para um x **arbitrario**.

**Enunciado:** Prove que ∃n ∈ ℤ tal que n² + n - 6 = 0.

```
Prova:
  Tome n = 2.
  n² + n - 6 = 4 + 2 - 6 = 0. ✓
  Portanto, existe tal n. □
```

**Enunciado:** Prove que ∃a, b ∈ ℤ tal que a | b ∧ b | a ∧ a ≠ b.

```
Prova:
  Tome a = 3 e b = -3.
  a | b pois -3 = 3·(-1). ✓
  b | a pois 3 = (-3)·(-1). ✓
  E a ≠ b pois 3 ≠ -3. ✓
  Portanto, existem tais a, b. □
```

---

## Exercicios de fixacao

**Identificacao de formas:**
1. Escreva a contrapositiva, a reciproca e a inversa de: "Se n e divisivel por 6, entao n e divisivel por 3."
2. Classifique como condicional, bicondicional, ou nenhum: "Voce entra no cinema somente se tiver ingresso."

**Provas diretas:**
3. Prove: "Se m e n sao pares, entao m + n e par."
4. Prove: "Se a | b e a | c, entao a | (b + c)."

**Provas por contrapositiva:**
5. Prove: "Se n³ e impar, entao n e impar."
6. Prove: "Se x² - 2x + 7 e par, entao x e impar."

**Bicondicional:**
7. Prove: "n e impar se e somente se n² e impar."

**Condicionais com "ou" e "e":**
8. Prove (hipotese com "ou"): "Se n e divisivel por 4 ou n e divisivel por 6, entao n e par."
9. Prove (conclusao com "e"): "Se 6 | n, entao 2 | n e 3 | n."
10. Prove (contrapositiva com De Morgan): "Se ab e par, entao a e par ou b e par."
11. Prove (conclusao com "ou", tecnica de assumir ¬q₁): "Se n e inteiro, entao n ≤ 0 ou n ≥ 1."
12. Escreva a contrapositiva e identifique a transformacao De Morgan: "Se x > 0 e y > 0, entao xy > 0."

**Com notacao formal e quantificadores:**
13. Prove: ∀a, b, c, d ∈ ℤ, ∀n ∈ ℤ⁺, (a ≡ b (mod n) ∧ c ≡ d (mod n)) ⟹ ac ≡ bd (mod n).
14. Prove: ∀n ∈ ℤ, 2 | n(n + 1).
15. Prove ou refute: ∀n ∈ ℤ, n² ≡ 0 (mod 4) ∨ n² ≡ 1 (mod 4).
16. Prove: ∀a, b ∈ ℤ, (a ≡ 2 (mod 5) ∧ b ≡ 3 (mod 5)) ⟹ ab ≡ 1 (mod 5).
17. Refute: ∀a, b, c ∈ ℤ, (a | bc) ⟹ (a | b ∨ a | c).
18. Prove: ∃n ∈ ℤ tal que n² ≡ 2 (mod 7).

> **Respostas selecionadas:**
>
> 1- Contrapositiva: "Se n nao e divisivel por 3, entao n nao e divisivel por 6."
>    Reciproca: "Se n e divisivel por 3, entao n e divisivel por 6." (FALSA! 3 e divisivel por 3 mas nao por 6)
>    Inversa: "Se n nao e divisivel por 6, entao n nao e divisivel por 3." (FALSA pelo mesmo motivo)
>
> 2- Condicional (p → q). "Somente se" indica condicional: "entrar no cinema → ter ingresso".
>
> 4- Prova: Se a | b, entao b = ak. Se a | c, entao c = aj. Logo b + c = ak + aj = a(k+j). Como k+j e inteiro, a | (b+c). □
>
> 5- Contrapositiva: "Se n e par, entao n³ e par." Se n = 2k, entao n³ = 8k³ = 2(4k³), par. □
>
> 6- Contrapositiva: "Se x e par, entao x² - 2x + 7 e impar." Se x = 2k, entao x² - 2x + 7 = 4k² - 4k + 7 = 2(2k² - 2k + 3) + 1. Como 2k² - 2k + 3 e inteiro, x² - 2x + 7 e impar. □
>
> 9- Prova: Suponha 6 | n. Entao n = 6k. Parte 1: n = 6k = 2(3k), logo 2 | n. Parte 2: n = 6k = 3(2k), logo 3 | n. □
>
> 10- Contrapositiva: "Se a e impar e b e impar, entao ab e impar." (De Morgan: ¬(par ou par) = impar e impar)
>     Prova: a = 2j+1, b = 2k+1. ab = (2j+1)(2k+1) = 4jk+2j+2k+1 = 2(2jk+j+k)+1, impar. □
>
> 12- Contrapositiva: "Se xy ≤ 0, entao x ≤ 0 ou y ≤ 0." O "e" na hipotese virou "ou" na conclusao (De Morgan).
>
> 13- Prova direta: Por definicao, a - b = nk₁ e c - d = nk₂. Queremos mostrar n | (ac - bd).
>     ac - bd = ac - bc + bc - bd = c(a - b) + b(c - d) = c·nk₁ + b·nk₂ = n(ck₁ + bk₂).
>     Como ck₁ + bk₂ ∈ ℤ, temos ac ≡ bd (mod n). □
>
> 14- Prova por casos: Se n e par, n = 2k, logo n(n+1) = 2k(n+1), e 2 | n(n+1).
>     Se n e impar, n+1 e par, logo n+1 = 2m, e n(n+1) = n·2m = 2(nm), e 2 | n(n+1). □
>
> 15- Prova por casos: Se n e par, n = 2k, logo n² = 4k², e n² ≡ 0 (mod 4).
>     Se n e impar, n = 2k+1, logo n² = 4k²+4k+1 = 4(k²+k)+1, e n² ≡ 1 (mod 4). □
>
> 16- Prova direta: a = 5k₁ + 2 e b = 5k₂ + 3. ab = (5k₁+2)(5k₂+3) = 25k₁k₂ + 15k₁ + 10k₂ + 6
>     = 5(5k₁k₂ + 3k₁ + 2k₂ + 1) + 1. Logo ab - 1 = 5·(inteiro), ou seja, ab ≡ 1 (mod 5). □
>
> 17- Contraexemplo: a = 6, b = 4, c = 3. bc = 12 e 6 | 12 (12 = 6·2). Mas 6 ∤ 4 e 6 ∤ 3. □
>
> 18- Prova: tome n = 3. n² = 9 = 7·1 + 2. Logo 9 ≡ 2 (mod 7), e existe tal n. □

## Referencias
- **How to Prove It** (Velleman), Cap. 3 — provas diretas e contrapositivas
- **Book of Proof** (Hammack), Cap. 4-5 — https://www.people.vcu.edu/~rhammack/BookOfProof/
- **Rosen**, Secao 1.7 (metodos de prova)
- **Trefor Bazett** - "Intro to Proofs" (YouTube, EN)
- **MIT OCW 6.042J** — Lectures sobre provas
- **Notas MAC0105** (IME-USP)
