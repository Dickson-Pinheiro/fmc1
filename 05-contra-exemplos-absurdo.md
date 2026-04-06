---
layout: page
title: "5. Contra-exemplos e Absurdo"
nav_order: 5
---
# 5. Contra-exemplos e Demonstracao por Absurdo

## Resumo

### O que e um contra-exemplo?

Imagine alguem dizendo: "Todos os passaros voam." Para provar que isso e **falso**, voce nao precisa analisar todos os passaros do mundo — basta mostrar **um** que nao voa. Um pinguim, por exemplo. Pronto: a afirmacao universal caiu.

Na matematica e a mesma coisa. Um **contra-exemplo** e um caso especifico que mostra que uma afirmacao universal (∀x, P(x)) e falsa.

```
Para refutar:  ∀x, P(x)
Basta exibir:  ∃x₀ tal que ¬P(x₀)    (um unico x₀ que nao satisfaz P)
```

**Atencao:** a logica aqui e assimetrica:
- Para **refutar** ∀x, P(x): basta **UM** contra-exemplo
- Para **provar** ∀x, P(x): voce precisa provar para **TODO** x (um exemplo nao basta!)

---

### Como encontrar contra-exemplos: estrategia pratica

Nao existe formula magica, mas algumas dicas ajudam:

```
1. Teste valores "pequenos" primeiro: 0, 1, 2, -1, -2
2. Teste os "casos limite": 0, 1, -1 (onde muitas formulas se comportam diferente)
3. Teste valores que tornam algum termo especial: primos pequenos, potencias de 2
4. Pense: "o que poderia dar errado nessa afirmacao?"
```

**Erro comum:** testar um valor e ele satisfazer a afirmacao, e concluir que ela e verdadeira. Lembre: exemplos nao provam afirmacoes universais!

---

### Exemplos de contra-exemplos

**Exemplo 1 — Valores pequenos resolvem:**

Refute: "∀n ∈ ℕ, 2ⁿ > n²"

```
Testando valores:
  n = 0:  2⁰ = 1,  0² = 0.   1 > 0  ✓ (vale)
  n = 1:  2¹ = 2,  1² = 1.   2 > 1  ✓ (vale)
  n = 2:  2² = 4,  2² = 4.   4 > 4? NAO! ✗

Contra-exemplo: n = 2. Temos 2² = 4 e 2² = 4, logo 2ⁿ > n² e falso. □
```

---

**Exemplo 2 — Valores negativos sao armadilhas classicas:**

Refute: "∀a, b ∈ ℤ, se a² = b² entao a = b"

```
A afirmacao "esquece" dos negativos.
Contra-exemplo: a = 3, b = -3.
  a² = 9 = b².  ✓ (hipotese verdadeira)
  Mas a = 3 ≠ -3 = b.  ✗ (conclusao falsa)

Portanto, a condicional e falsa. □
```

**Dica:** quando a afirmacao envolve quadrados ou valores absolutos, sempre teste pares (x, -x).

---

**Exemplo 3 — Testar primos pequenos:**

Refute: "∀n ∈ ℕ, n² + n + 41 e primo"

```
Essa formula e "quase verdadeira" — funciona para n = 0, 1, 2, ..., 39!
Isso mostra por que testar poucos valores NAO prova uma afirmacao universal.

Contra-exemplo: n = 40.
  40² + 40 + 41 = 1600 + 40 + 41 = 1681 = 41².
  1681 nao e primo. □

Como encontrar? Note que para n = 41, temos 41² + 41 + 41 = 41(41 + 1 + 1),
claramente divisivel por 41. Na verdade, n = 40 ja falha: 40² + 40 + 41 = 41².
```

---

**Exemplo 4 — Divisibilidade com armadilha:**

Refute: "∀a, b, c ∈ ℤ, (a | c ∧ b | c) ⟹ ab | c"

```
A intuicao diz "se 2 divide c e 3 divide c, entao 6 divide c"...
e isso de fato vale para 2 e 3. Mas a afirmacao diz "para todo a, b".

Contra-exemplo: a = 2, b = 4, c = 4.
  2 | 4 ✓  e  4 | 4 ✓  (hipotese verdadeira)
  Mas ab = 8, e 8 ∤ 4.  ✗ (conclusao falsa)

O problema: a e b compartilham fatores (2 | 4), entao ab "conta duas vezes"
o fator em comum. □
```

---

**Exemplo 5 — Refutando com a definicao formal:**

Refute: "∀a, b ∈ ℤ, (a | bc) ⟹ (a | b ∨ a | c)"

```
Contra-exemplo: a = 6, b = 4, c = 3.
  bc = 12 e 6 | 12 (pois 12 = 6 · 2). ✓
  Mas 6 ∤ 4 e 6 ∤ 3.  ✗

Por que falha? Nenhum fator individual (4 ou 3) e divisivel por 6,
mas o produto 4 · 3 = 12 e. A propriedade so vale quando a e primo
(esse e o conteudo do Lema de Euclides). □
```

---

### Resumo visual: contra-exemplos

```
AFIRMACAO UNIVERSAL (∀x, P(x))
├── Para PROVAR:   demonstre para x ARBITRARIO (prova geral)
└── Para REFUTAR:  exiba UM contra-exemplo (∃x₀, ¬P(x₀))

DICAS PARA ENCONTRAR:
├── Teste: 0, 1, -1, 2, -2 (valores extremos e pequenos)
├── Pense em negativos quando ha quadrados ou modulos
├── Pense em fatores comuns quando ha divisibilidade
└── Se funciona para muitos valores, procure o padrao que quebra
```

---

### O que e demonstracao por absurdo (prova por contradicao)?

A ideia e surpreendentemente simples. Imagine que alguem diz "essa porta esta trancada". Voce duvida e assume que nao esta — entao tenta abri-la e nao consegue. Voce chegou a uma **contradicao** com sua suposicao. Conclusao: a porta esta trancada.

Na matematica, funciona assim:

```
Para provar que P e verdadeiro:

1. Suponha, por absurdo, que P e FALSO (assuma ¬P).
2. A partir dessa suposicao, deduza logicamente ate chegar
   a algo IMPOSSIVEL (uma contradicao).
3. Como a suposicao levou a algo impossivel, ela deve estar errada.
4. Portanto, P e verdadeiro.
```

**Por que funciona?** Pelo principio logico da **nao-contradicao**: uma afirmacao nao pode ser verdadeira e falsa ao mesmo tempo. Se assumir ¬P leva a "algo e V e F simultaneamente", entao ¬P e insustentavel, e P deve ser verdadeiro.

---

### Estrutura formal de uma prova por absurdo

```
Teorema: [enunciado P]

Prova:
  Suponha, por absurdo, que ¬P.                ← a negacao do que queremos provar
  [passo 1: use a suposicao para deduzir algo]
  [passo 2: continue deduzindo...]
  ...
  [passo k: chegue a uma CONTRADICAO]          ← algo como "x e par E x e impar"
                                                   ou "0 = 1" ou "mdc = 1 E mdc ≥ 2"
  Isso e uma contradicao.
  Portanto, a suposicao ¬P e falsa, e P e verdadeiro. □
```

**Que tipo de contradicao procurar?** Qualquer afirmacao que seja claramente impossivel:

```
Contradicoes comuns:
  - Um numero e par E impar ao mesmo tempo
  - mdc(a,b) = 1 e ao mesmo tempo a e b tem fator comum
  - Um primo divide 1
  - Um numero e positivo E negativo (ou zero)
  - 0 = 1, ou 1 < 0
```

---

### Exemplo classico: √2 e irracional

Esse e provavelmente o exemplo mais famoso de prova por absurdo em toda a matematica. Vamos passo a passo.

**Enunciado:** Prove que √2 e irracional.

**Antes de comecar:** lembre que um numero e racional se pode ser escrito como a/b com a, b inteiros e b ≠ 0. Alem disso, toda fracao pode ser simplificada ate ficar **irredutivel** (mdc(a,b) = 1).

```
Prova:
  Suponha, por absurdo, que √2 e racional.

  Passo 1 — Escreva como fracao irredutivel:
    Entao √2 = a/b, com a, b ∈ ℤ, b ≠ 0, e mdc(a,b) = 1.
    (Esta e a nossa "ancora" — vamos contradize-la no final.)

  Passo 2 — Eleve ao quadrado:
    2 = a²/b²
    a² = 2b²

  Passo 3 — Deduza que a e par:
    a² = 2b² implica que a² e par.
    Pelo resultado do topico 4 (se n² e par, entao n e par):
    a e par.

  Passo 4 — Substitua e deduza que b e par:
    Como a e par, a = 2k para algum k ∈ ℤ.
    Substituindo: (2k)² = 2b²  →  4k² = 2b²  →  b² = 2k².
    Logo b² e par, e portanto b e par.

  Passo 5 — Identifique a contradicao:
    a e par E b e par.
    Mas se ambos sao pares, mdc(a,b) ≥ 2.
    CONTRADICAO com mdc(a,b) = 1.

  Portanto, √2 e irracional. □
```

**O que tornou essa prova possivel?**
- A suposicao nos deu uma fracao a/b para trabalhar
- A condicao mdc(a,b) = 1 foi a "bomba-relogio" que explodiu no final
- O resultado anterior (n² par ⟹ n par) foi usado duas vezes

**Dica:** provas de irracionalidade quase sempre seguem esse roteiro — fracao irredutivel → manipulacao → ambos pares → contradicao com o mdc.

---

### Exemplo classico: existem infinitos primos

**Enunciado:** Prove que existem infinitos numeros primos.

**Antes de comecar:** a ideia genial (de Euclides!) e construir um numero que "escapa" de qualquer lista finita de primos.

```
Prova:
  Suponha, por absurdo, que existe uma quantidade finita de primos.
  Entao podemos lista-los todos: p₁, p₂, ..., pₙ.

  Passo 1 — Construa um numero especial:
    Defina N = p₁ · p₂ · ... · pₙ + 1.
    (Multiplicamos todos os primos e somamos 1.)

  Passo 2 — Observe que N > 1:
    Como cada pᵢ ≥ 2, o produto e ≥ 2, logo N ≥ 3.

  Passo 3 — N tem algum divisor primo:
    Todo inteiro maior que 1 tem pelo menos um divisor primo.
    Seja p um divisor primo de N.

  Passo 4 — p deveria estar na lista:
    Como listamos TODOS os primos, p deve ser algum pᵢ.
    Entao pᵢ | N.

  Passo 5 — Mas p tambem divide o produto:
    pᵢ | (p₁ · p₂ · ... · pₙ)  (pois pᵢ e um dos fatores).

  Passo 6 — Identifique a contradicao:
    Se pᵢ | N e pᵢ | (p₁ · p₂ · ... · pₙ), entao:
    pᵢ | (N - p₁ · p₂ · ... · pₙ) = 1.
    Mas nenhum primo divide 1. CONTRADICAO.

  Portanto, existem infinitos primos. □
```

**Observacao importante:** a prova NAO diz que N e primo! Ela diz que N tem um divisor primo que nao pode estar na lista. N pode ser primo ou composto — o argumento funciona de qualquer forma.

---

### Mais exemplos de prova por absurdo

#### Exemplo 3 — Absurdo com paridade

**Enunciado:** Prove por absurdo que se n² e par, entao n e par.

Ja provamos isso por contrapositiva no topico 4. Agora, pela via do absurdo:

```
Prova:
  Suponha, por absurdo, que n² e par e n e impar.
  (Negamos a condicional: hipotese verdadeira E conclusao falsa.)

  Como n e impar, ∃k ∈ ℤ tal que n = 2k + 1.
  Entao n² = (2k+1)² = 4k² + 4k + 1 = 2(2k²+2k) + 1.
  Logo n² e impar.

  Mas supusemos que n² e par.
  n² e par E n² e impar — CONTRADICAO.

  Portanto, se n² e par, entao n e par. □
```

**Compare com a contrapositiva:** a prova e quase identica! A diferenca e que na contrapositiva voce conclui ¬p diretamente, enquanto no absurdo voce usa a hipotese p para fabricar a contradicao. O resultado algebrico e o mesmo.

---

#### Exemplo 4 — Absurdo com divisibilidade

**Enunciado:** Prove que ∀n ∈ ℤ, se 3 | n², entao 3 | n.

```
Prova:
  Seja n ∈ ℤ. Suponha, por absurdo, que 3 | n² e 3 ∤ n.

  Se 3 ∤ n, entao pela divisao euclidiana por 3, n = 3q + r com r ∈ {1, 2}.

  Caso r = 1: n = 3q + 1.
    n² = 9q² + 6q + 1 = 3(3q² + 2q) + 1.
    Logo n² deixa resto 1 na divisao por 3, ou seja, 3 ∤ n².

  Caso r = 2: n = 3q + 2.
    n² = 9q² + 12q + 4 = 9q² + 12q + 3 + 1 = 3(3q² + 4q + 1) + 1.
    Logo n² deixa resto 1 na divisao por 3, ou seja, 3 ∤ n².

  Em ambos os casos, 3 ∤ n².
  Mas supusemos que 3 | n². CONTRADICAO.

  Portanto, se 3 | n², entao 3 | n. □
```

**Dica:** quando a prova envolve "3 nao divide n", a divisao euclidiana por 3 e a ferramenta natural — ela da exatamente os casos possiveis.

---

#### Exemplo 5 — Absurdo com numeros reais

**Enunciado:** Prove que nao existe numero racional r tal que r² = 3.

```
Prova:
  Suponha, por absurdo, que ∃r ∈ ℚ tal que r² = 3.
  Entao r = a/b com a, b ∈ ℤ, b ≠ 0, mdc(a,b) = 1.

  r² = 3  ⟹  a²/b² = 3  ⟹  a² = 3b².

  Logo 3 | a² e, pelo exemplo anterior, 3 | a.
  Entao a = 3k para algum k ∈ ℤ.

  Substituindo: (3k)² = 3b²  →  9k² = 3b²  →  b² = 3k².
  Logo 3 | b², e portanto 3 | b.

  Mas a e b sao ambos divisiveis por 3, logo mdc(a,b) ≥ 3.
  CONTRADICAO com mdc(a,b) = 1.

  Portanto, nao existe racional cujo quadrado e 3 (ou seja, √3 e irracional). □
```

**Observe o padrao:** a estrutura e identica a da prova de √2 — troque "2" por "3" e o argumento funciona. Na verdade, o mesmo roteiro prova que √p e irracional para todo primo p.

---

#### Exemplo 6 — Absurdo com desigualdade

**Enunciado:** Prove que ∀x, y ∈ ℝ, se x + y ≥ 2, entao x ≥ 1 ou y ≥ 1.

```
Prova:
  Sejam x, y ∈ ℝ. Suponha, por absurdo, que x + y ≥ 2, x < 1, e y < 1.

  Somando as duas desigualdades: x + y < 1 + 1 = 2.
  Mas supusemos que x + y ≥ 2.
  x + y ≥ 2 E x + y < 2 — CONTRADICAO.

  Portanto, se x + y ≥ 2, entao x ≥ 1 ou y ≥ 1. □
```

**Note:** a negacao de "x ≥ 1 ou y ≥ 1" e "x < 1 e y < 1" (De Morgan). Sempre que a conclusao tem "ou", negar ela da um "e" — o que nos da mais informacao para trabalhar.

---

### Como negar a proposicao corretamente

O passo mais importante (e onde mais se erra) no absurdo e **negar corretamente** o que se quer provar. Vamos treinar:

| O que queremos provar (P) | O que assumimos por absurdo (¬P) |
|---|---|
| √2 e irracional | √2 e racional |
| Existem infinitos primos | Existem finitos primos |
| p → q ("se p entao q") | p e verdadeiro E q e falso |
| ∀x, P(x) | ∃x tal que ¬P(x) |
| ∃x, P(x) | ∀x, ¬P(x) |
| A ∧ B | ¬A ∨ ¬B |
| A ∨ B | ¬A ∧ ¬B |

**A linha mais importante da tabela:** para negar uma condicional p → q, voce assume que p e verdadeiro **e** q e falso. Isso vem da tabela-verdade — o unico caso em que p → q e falso.

```
Exemplo: negar "se n² e par, entao n e par"
  ¬(n² par → n par)  =  n² e par  E  n e impar

Exemplo: negar "∀n ∈ ℤ, n² ≥ 0"
  ∃n ∈ ℤ tal que n² < 0
```

---

### Absurdo vs. contrapositiva: quando usar cada um

| Situacao | Melhor tecnica | Por que |
|---|---|---|
| Proposicao condicional (p → q) e ¬q da boa algebra | **Contrapositiva** | Mais limpa, sem necessidade de achar contradicao |
| Proposicao condicional (p → q) e voce precisa usar p E ¬q juntos | **Absurdo** | Voce tem mais informacao para trabalhar |
| Proposicao NAO condicional ("√2 e irracional", "existem infinitos primos") | **Absurdo** | Nao tem p → q para tomar contrapositiva |
| Proposicao existencial negada ("nao existe x tal que...") | **Absurdo** | Negar da ∀, que e mais facil de manipular |
| Proposicao envolvendo irracionalidade | **Absurdo** | "Irracional" e definido por negacao — absurdo e natural |

**Regra pratica:**
```
1. Tente prova DIRETA primeiro.
2. Se nao rolar, tente CONTRAPOSITIVA (se for condicional).
3. Se nenhuma funcionar, use ABSURDO.

Absurdo e o "ultimo recurso" mais poderoso — sempre funciona,
mas contrapositiva e direta costumam ser mais elegantes.
```

---

### Erros comuns em provas por absurdo

**1. Negar a proposicao errado**
```
ERRADO: quero provar p → q, assumo ¬p → ¬q.
CERTO:  quero provar p → q, assumo p ∧ ¬q.

A negacao de p → q NAO e ¬p → ¬q (isso e a inversa).
A negacao de p → q e:  p e verdadeiro E q e falso.
```

**2. Circular: usar o que quer provar dentro da prova**
```
ERRADO:
  "Suponha por absurdo que √2 e racional.
   Mas sabemos que √2 e irracional, contradicao."

Voce nao pode usar o resultado que esta tentando provar!
A contradicao deve surgir de DEDUCOES a partir da suposicao.
```

**3. Nao identificar claramente a contradicao**
```
ERRADO: "...e isso e absurdo." (sem dizer por que)
CERTO:  "...logo mdc(a,b) ≥ 2, contradizendo mdc(a,b) = 1."

Sempre explicite: QUAL afirmacao contradiz QUAL outra.
```

**4. Fazer absurdo quando contrapositiva bastava**

Se a proposicao e p → q e voce assume p ∧ ¬q, deduz algo, e a "contradicao" e simplesmente ¬(¬q) = q... voce fez uma contrapositiva disfarçada. Nao esta errado, mas e desnecessariamente complicado.

---

### Exemplo com notacao formal e quantificadores

**Enunciado:** Prove que ∀a, b ∈ ℤ, se a² | b² e b ≠ 0, entao a | b.

Esse exercicio combina absurdo com divisao euclidiana.

```
Prova:
  Sejam a, b ∈ ℤ com b ≠ 0. Suponha que a² | b².
  Suponha, por absurdo, que a ∤ b.

  Pela divisao euclidiana: b = aq + r, com 0 < r < |a|.
  (r > 0 porque a ∤ b.)

  Entao:
    b² = (aq + r)² = a²q² + 2aqr + r²
    b² - a²q² - 2aqr = r²
    b² - a²q² - 2aqr = r²

  Como a² | b², temos b² = a²k para algum k ∈ ℤ.
    r² = a²k - a²q² - 2aqr = a²(k - q²) - 2aqr = a(a(k-q²) - 2qr).

  Logo a | r².
  Mas 0 < r < |a|, entao 0 < r² < a².
  Logo r² e um multiplo positivo de a que e menor que a² — o que implica
  que a divide um numero positivo menor que a².

  [Esta prova pode seguir por inducao ou por argumentos mais refinados
  sobre fatores primos. Na pratica, o resultado e mais facilmente
  provado usando a decomposicao em fatores primos.]
```

**Nota:** este exemplo mostra que nem todo problema "cabe" facilmente no absurdo puro. Quando a prova fica muito complicada, pode ser sinal de que outra tecnica (como fatoracao em primos) e mais adequada.

---

## Pontos-chave para a prova

- **Contra-exemplo:** basta UM para refutar ∀ — teste valores pequenos e casos limite
- **Absurdo:** negar a tese, deduzir passo a passo ate algo impossivel
- **Negar corretamente:** ¬(p → q) = p ∧ ¬q; ¬(∀x, P(x)) = ∃x, ¬P(x)
- **Identificar a contradicao claramente** — diga explicitamente o que contradiz o que
- A prova de **√2 irracional** e classica e frequente em provas
- A prova de **infinitos primos** e classica e frequente em provas
- Quando a proposicao e condicional, prefira contrapositiva; quando nao e, use absurdo

## Exercicios de fixacao

**Contra-exemplos:**
1. Refute: "∀n ∈ ℕ, 2ⁿ > n²"
2. Refute: "∀a, b ∈ ℤ, se a² = b² entao a = b"
3. Refute: "∀n ∈ ℤ, se n² e multiplo de 4, entao n e multiplo de 4"
4. Refute: "∀a, b, c ∈ ℤ, se a | (b + c), entao a | b ou a | c"

**Provas por absurdo:**
5. Prove por absurdo: "Se n² e par, entao n e par."
6. Prove que √3 e irracional.
7. Prove por absurdo: "∀x ∈ ℝ, se x e irracional, entao -x e irracional."
8. Prove por absurdo: "Nao existem inteiros a, b tais que 2a + 4b = 1."

**Com notacao formal:**
9. Prove: ¬(∃n ∈ ℤ, n² + 1 ≡ 0 (mod 4)).
10. Prove por absurdo: ∀a, b ∈ ℤ, (a + b ≥ 15) ⟹ (a ≥ 8 ∨ b ≥ 8).

> **Respostas selecionadas:**
>
> 1- n = 2: 2² = 4 e 2² = 4. 4 > 4 e falso. □
>
> 2- a = 1, b = -1: a² = 1 = b², mas 1 ≠ -1. □
>
> 3- n = 2: n² = 4, que e multiplo de 4, mas n = 2 nao e multiplo de 4. □
>
> 4- a = 3, b = 1, c = 2: 3 | (1 + 2) = 3. Mas 3 ∤ 1 e 3 ∤ 2. □
>
> 5- Suponha por absurdo que n² e par e n e impar. Entao n = 2k+1,
>    logo n² = 4k²+4k+1 = 2(2k²+2k)+1, que e impar.
>    Mas n² e par. Contradicao. □
>
> 6- Suponha por absurdo que √3 = a/b com mdc(a,b) = 1.
>    a² = 3b². Logo 3 | a², e portanto 3 | a. Entao a = 3k.
>    9k² = 3b² → b² = 3k² → 3 | b. Mas mdc(a,b) ≥ 3. Contradicao. □
>
> 7- Suponha por absurdo que x e irracional e -x e racional.
>    Se -x e racional, -x = a/b com a, b ∈ ℤ, b ≠ 0.
>    Entao x = -a/b = (-a)/b, que e racional. Contradicao com x irracional. □
>
> 8- Suponha que ∃a, b ∈ ℤ com 2a + 4b = 1.
>    Entao 2(a + 2b) = 1, logo 2 | 1. Mas 2 ∤ 1. Contradicao. □
>
> 9- Suponha por absurdo que ∃n ∈ ℤ, n² + 1 ≡ 0 (mod 4), ou seja, 4 | (n² + 1).
>    Se n e par: n = 2k → n² + 1 = 4k² + 1 ≡ 1 (mod 4). Logo 4 ∤ (n²+1).
>    Se n e impar: n = 2k+1 → n² + 1 = 4k²+4k+1+1 = 4k²+4k+2 ≡ 2 (mod 4). Logo 4 ∤ (n²+1).
>    Em ambos os casos, 4 ∤ (n²+1). Contradicao. □
>
> 10- Suponha por absurdo que a + b ≥ 15, a < 8, e b < 8.
>     Entao a + b < 8 + 8 = 16... mas isso nao contradiz a + b ≥ 15 (poderia ser 15).
>     Ajustando: a ≤ 7 e b ≤ 7 (pois a, b ∈ ℤ). Entao a + b ≤ 14 < 15. Contradicao. □

## Referencias
- **Book of Proof** (Hammack), Cap. 6 (contradicao) e Cap. 9 (contra-exemplos) — https://www.people.vcu.edu/~rhammack/BookOfProof/
- **How to Prove It** (Velleman), Cap. 4
- **Rosen**, Secao 1.7
- **Trefor Bazett** - Proof by Contradiction (YouTube, EN)
- **Khan Academy** (PT) — https://pt.khanacademy.org/
