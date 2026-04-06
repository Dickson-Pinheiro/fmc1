---
layout: page
title: "2. Conectivos e Relacoes"
nav_order: 2
---
# 2. Conectivos Logicos e Relacoes

## Resumo

### Conectivos logicos
Conectivos combinam proposicoes simples para formar proposicoes compostas.

| Conectivo | Simbolo | Nome | Exemplo |
|---|---|---|---|
| Negacao | ¬p | "nao p" | ¬"chove" = "nao chove" |
| Conjuncao | p ∧ q | "p e q" | "chove e faz frio" |
| Disjuncao | p ∨ q | "p ou q" | "chove ou faz sol" |
| Condicional | p → q | "se p entao q" | "se chove, entao levo guarda-chuva" |
| Bicondicional | p ↔ q | "p se e somente se q" | "passo se e somente se estudo" |

### Tabelas-verdade

**Negacao (¬p):**

| p | ¬p |
|---|---|
| V | F |
| F | V |

**Conjuncao (p ∧ q):** so e V quando ambos sao V

| p | q | p ∧ q |
|---|---|---|
| V | V | V |
| V | F | F |
| F | V | F |
| F | F | F |

**Disjuncao (p ∨ q):** so e F quando ambos sao F

| p | q | p ∨ q |
|---|---|---|
| V | V | V |
| V | F | V |
| F | V | V |
| F | F | F |

**Condicional (p → q):** so e F quando p e V e q e F

| p | q | p → q |
|---|---|---|
| V | V | V |
| V | F | F |
| F | V | V |
| F | F | V |

> **Atencao:** "F → qualquer coisa" e sempre V. Essa e a parte mais contra-intuitiva. "Se 2+2=5 entao eu sou o rei" e verdadeiro!

**Bicondicional (p ↔ q):** V quando ambos tem o mesmo valor

| p | q | p ↔ q |
|---|---|---|
| V | V | V |
| V | F | F |
| F | V | F |
| F | F | V |

### Equivalencias logicas importantes
- **Contrapositiva:** p → q ≡ ¬q → ¬p
- **De Morgan:** ¬(p ∧ q) ≡ ¬p ∨ ¬q e ¬(p ∨ q) ≡ ¬p ∧ ¬q
- **Dupla negacao:** ¬(¬p) ≡ p
- **Implicacao como disjuncao:** p → q ≡ ¬p ∨ q

### Relacoes

#### De onde surgem as relacoes?
Ate aqui, trabalhamos com proposicoes ("3 e primo") e conectivos (∧, ∨, →). Mas muitas afirmacoes matematicas nao falam de um objeto so — elas **comparam dois objetos**:

- "3 **e menor que** 5"
- "6 **e divisivel por** 3"
- "Ana **e irma de** Bia"

Essas afirmacoes sao **funcoes proposicionais de duas variaveis**: P(x, y). Dado um par (x, y), P(x, y) e V ou F. O conjunto de todos os pares para os quais P e verdadeira **e** a relacao.

#### A conexao: predicado de 2 variaveis → relacao → conjunto de pares

Veja o caminho completo com um exemplo concreto:

**Passo 1 — Predicado:** Considere P(x, y) = "x e menor que y", com dominio A = {1, 2, 3}.

**Passo 2 — Produto cartesiano:** Listamos todos os pares possiveis A × A:
```
A × A = {(1,1), (1,2), (1,3), (2,1), (2,2), (2,3), (3,1), (3,2), (3,3)}
```

**Passo 3 — Avaliar o predicado em cada par:**
```
P(1,1) = "1 < 1" → F       P(2,1) = "2 < 1" → F       P(3,1) = "3 < 1" → F
P(1,2) = "1 < 2" → V  ✓    P(2,2) = "2 < 2" → F       P(3,2) = "3 < 2" → F
P(1,3) = "1 < 3" → V  ✓    P(2,3) = "2 < 3" → V  ✓    P(3,3) = "3 < 3" → F
```

**Passo 4 — A relacao e o conjunto dos pares verdadeiros:**
```
R = {(1,2), (1,3), (2,3)}
```

Entao: 1R2 ("1 esta relacionado com 2") significa simplesmente que (1,2) ∈ R, ou seja, P(1,2) e verdadeira.

#### Resumindo
```
Funcao proposicional P(x,y)  →  avalia pares de A × B  →  pares verdadeiros formam R ⊆ A × B
```

Uma **relacao** nao e nada mais do que o "rastro" que um predicado de duas variaveis deixa no produto cartesiano: o conjunto de pares que tornam o predicado verdadeiro.

#### Definicao formal
Uma **relacao** R de um conjunto A para um conjunto B e um subconjunto de A × B (produto cartesiano). Se (a, b) ∈ R, escrevemos aRb.

Quando A = B, dizemos que R e uma relacao **em** A (ou "sobre" A), e podemos analisar suas propriedades estruturais.

#### Visualizando relacoes
Uma forma util de visualizar e com um **diagrama de setas** ou uma **matriz**:

Para R = {(1,2), (1,3), (2,3)} em {1, 2, 3}:
```
Matriz:       1  2  3           Diagrama:
        1  [  .  ✓  ✓ ]         1 → 2
        2  [  .  .  ✓ ]         1 → 3
        3  [  .  .  . ]         2 → 3
```

**Propriedades de relacoes em A × A:**

Quando uma relacao R e definida de um conjunto A para ele mesmo (R ⊆ A × A), podemos perguntar se ela obedece a certas propriedades estruturais. Pense nelas como "regras" que a relacao pode ou nao seguir.

---

**1. Reflexiva** — "todo elemento se relaciona consigo mesmo"

Definicao formal: ∀a ∈ A: aRa

Ideia: olhe para cada elemento do conjunto. Se TODOS possuem um "laco" (seta apontando para si mesmo), a relacao e reflexiva.

```
Exemplo: R = "≤" em {1, 2, 3}
  1 ≤ 1? Sim ✓    2 ≤ 2? Sim ✓    3 ≤ 3? Sim ✓
  → Reflexiva!

Contra-exemplo: R = "<" em {1, 2, 3}
  1 < 1? Nao ✗
  → Nao e reflexiva (basta um falhar)
```

Dica visual na matriz: a diagonal principal deve estar TODA preenchida.
```
     1  2  3
1  [ ✓  .  . ]    ← diagonal toda com ✓ = reflexiva
2  [ .  ✓  . ]
3  [ .  .  ✓ ]
```

---

**2. Simetrica** — "se a se relaciona com b, entao b se relaciona com a"

Definicao formal: ∀a,b ∈ A: aRb → bRa

Ideia: toda seta e uma "via de mao dupla". Se existe uma seta de a para b, obrigatoriamente existe uma de b para a.

```
Exemplo: R = "tem o mesmo resto na divisao por 2" em {1, 2, 3, 4}
  1R3 (ambos impares) e 3R1 (ambos impares) ✓
  2R4 (ambos pares) e 4R2 (ambos pares) ✓
  → Simetrica!

Contra-exemplo: R = "<" em {1, 2, 3}
  1 < 2? Sim, mas 2 < 1? Nao ✗
  → Nao e simetrica
```

Dica visual na matriz: a matriz e espelhada em relacao a diagonal (como uma matriz simetrica em algebra linear).
```
     1  2  3               1  2  3
1  [ .  ✓  . ]          1 [ .  ✓  . ]
2  [ ✓  .  . ]  ←→      2 [ ✓  .  . ]   posicao (1,2) = posicao (2,1)
3  [ .  .  . ]          3 [ .  .  . ]
```

---

**3. Antissimetrica** — "se a via e de mao dupla, entao a e b sao o mesmo elemento"

Definicao formal: ∀a,b ∈ A: (aRb ∧ bRa) → a = b

Ideia: dois elementos DISTINTOS nunca podem se relacionar mutuamente. A unica situacao em que aRb e bRa ocorrem juntos e quando a = b.

**Cuidado:** antissimetrica NAO e o oposto de simetrica! Uma relacao pode ser ambas (ex: igualdade) ou nenhuma das duas.

```
Exemplo: R = "≤" em {1, 2, 3}
  1 ≤ 2 e 2 ≤ 1? Nao (so a primeira vale), ok ✓
  2 ≤ 3 e 3 ≤ 2? Nao (so a primeira vale), ok ✓
  1 ≤ 1 e 1 ≤ 1? Sim, mas 1 = 1, ok ✓
  → Antissimetrica!

Contra-exemplo: R = {(1,2), (2,1), (1,1), (2,2)} em {1, 2}
  1R2 e 2R1, mas 1 ≠ 2 ✗
  → Nao e antissimetrica
```

Dica visual na matriz: fora da diagonal, nunca ha ✓ em posicoes espelhadas simultaneamente.
```
     1  2  3
1  [ ✓  ✓  ✓ ]    (1,2)=✓ mas (2,1)=.  → ok
2  [ .  ✓  ✓ ]    (1,3)=✓ mas (3,1)=.  → ok
3  [ .  .  ✓ ]    nenhum par espelhado fora da diagonal
```

---

**4. Transitiva** — "se a cadeia a→b→c existe, entao o atalho a→c tambem existe"

Definicao formal: ∀a,b,c ∈ A: (aRb ∧ bRc) → aRc

Ideia: se voce consegue ir de a ate c passando por b, entao deve existir um caminho direto de a ate c.

```
Exemplo: R = "<" em {1, 2, 3}
  1 < 2 e 2 < 3 → 1 < 3? Sim ✓
  (verificar todas as cadeias possiveis)
  → Transitiva!

Contra-exemplo: R = "e amigo de" em {Ana, Bia, Carol}
  Ana amiga de Bia, Bia amiga de Carol, mas Ana NAO e amiga de Carol ✗
  → Nao e transitiva
```

Dica para verificar: para cada par (a,b) ∈ R, olhe todos os pares (b,c) ∈ R e confira se (a,c) ∈ R.

---

**Resumo rapido:**

| Propriedade | Pergunta-chave | Dica na matriz |
|---|---|---|
| Reflexiva | Todo elemento aponta pra si mesmo? | Diagonal toda preenchida |
| Simetrica | Toda seta tem volta? | Matriz espelhada |
| Antissimetrica | Setas de ida-e-volta so entre iguais? | Sem espelhos fora da diagonal |
| Transitiva | Todo caminho a→b→c tem atalho a→c? | (verificar cadeias) |

---

### Relacao de equivalencia vs. Relacao de ordem parcial

Essas sao as duas combinacoes de propriedades mais importantes. A diferenca fundamental esta em **uma unica propriedade** que muda: **simetrica** vs. **antissimetrica**. Isso gera comportamentos completamente diferentes.

```
Equivalencia = reflexiva + SIMETRICA     + transitiva  → "agrupar iguais"
Ordem parcial = reflexiva + ANTISSIMETRICA + transitiva  → "organizar em hierarquia"
```

---

**Relacao de equivalencia** — "estes elementos sao iguais sob algum criterio"

Propriedades: reflexiva + simetrica + transitiva

A simetria e a chave: se a e equivalente a b, entao b e equivalente a a. Nao ha "direcao", nao ha "quem vem antes". Os elementos sao tratados como **intercambiaveis** dentro do seu grupo.

```
Exemplo concreto: "ter o mesmo resto na divisao por 3" em {0, 1, 2, 3, 4, 5, 6}

  Verificando as propriedades:
  - Reflexiva: 4 tem o mesmo resto que 4? Sim ✓
  - Simetrica: se 1 tem o mesmo resto que 4, entao 4 tem o mesmo resto que 1? Sim ✓
  - Transitiva: 1 mesmo resto que 4, 4 mesmo resto que 7 → 1 mesmo resto que 7? Sim ✓

  Isso gera CLASSES DE EQUIVALENCIA (grupos):
  - Classe resto 0: {0, 3, 6}
  - Classe resto 1: {1, 4}
  - Classe resto 2: {2, 5}
```

Observe que as classes:
- **Nao se sobrepoe:** nenhum elemento aparece em duas classes
- **Cobrem tudo:** todo elemento esta em alguma classe
- Isso e uma **particao** do conjunto — dividir em grupos sem sobra e sem repeticao

Analogia: equivalencia e como separar meias por cor. Todas as meias azuis sao "iguais" para esse criterio. Nao existe meia azul "maior" que outra meia azul — elas sao intercambiaveis dentro do grupo.

```
Diagrama das classes (cada circulo e um grupo de "iguais"):

   (0, 3, 6)     (1, 4)     (2, 5)
   [  resto 0 ]  [ resto 1 ] [ resto 2 ]

   Dentro de cada grupo: todos equivalentes entre si
   Entre grupos: ninguem se relaciona
```

---

**Relacao de ordem parcial** — "este elemento vem antes daquele"

Propriedades: reflexiva + antissimetrica + transitiva

A antissimetria e a chave: se a vem antes de b E b vem antes de a, entao a = b. Isso cria uma **direcao** — um sentido de "menor para maior", uma hierarquia.

```
Exemplo concreto: "a divide b" (a | b) em {1, 2, 3, 4, 6, 12}

  Verificando as propriedades:
  - Reflexiva: 4 | 4? Sim ✓
  - Antissimetrica: 2 | 4 e 4 | 2? Nao (so a primeira), ok ✓
                    Se a | b e b | a, entao a = b ✓
  - Transitiva: 2 | 4 e 4 | 12 → 2 | 12? Sim ✓

  Isso gera uma HIERARQUIA (diagrama de Hasse):

            12
           / \
          4   6
          | / |
          2   3
           \ /
            1

  Leitura: cada aresta de baixo para cima significa "divide".
  1→2, 1→3, 2→4, 2→6, 3→6, 4→12, 6→12
  Note que 2 conecta tanto a 4 quanto a 6 (porque 2|4 e 2|6).
```

Observe que:
- Ha uma **direcao**: 1 esta "abaixo" de todos, 12 esta "acima" de todos
- **Nem todos sao comparaveis**: 4 divide 6? Nao. E 6 divide 4? Tambem nao. Entao 4 e 6 sao **incomparaveis**. Da mesma forma, 4 e 3 sao incomparaveis (nenhum divide o outro)
- Mas cuidado: 2 e 6 **sao** comparaveis (2 | 6), mesmo estando em "ramos" diferentes do diagrama. Comparabilidade depende da relacao, nao da posicao visual
- Por isso e "ordem **parcial**" — nem todo par tem relacao de "quem vem antes", mas alguns pares que parecem distantes no diagrama podem sim ser comparaveis

Analogia: ordem parcial e como um organograma de empresa. O CEO esta acima de todos. Dois gerentes de departamentos diferentes? Nenhum "manda" no outro — sao incomparaveis. Mas um gerente e um coordenador abaixo dele sao comparaveis, mesmo que o coordenador apareca visualmente longe no organograma.

---

**Comparacao lado a lado com o mesmo conjunto {1, 2, 3, 4}:**

```
EQUIVALENCIA: "ter a mesma paridade"       ORDEM PARCIAL: "a divide b"
(par/impar)

Pares na relacao:                           Pares na relacao:
(1,1) (1,3) (3,1) (3,3)  ← impares        (1,1) (1,2) (1,3) (1,4)
(2,2) (2,4) (4,2) (4,4)  ← pares          (2,2) (2,4)
                                            (3,3) (4,4)

Matriz:                                     Matriz:
     1  2  3  4                                  1  2  3  4
1  [ ✓  .  ✓  . ]  espelhada!              1  [ ✓  ✓  ✓  ✓ ]  triangular!
2  [ .  ✓  .  ✓ ]                          2  [ .  ✓  .  ✓ ]
3  [ ✓  .  ✓  . ]                          3  [ .  .  ✓  . ]
4  [ .  ✓  .  ✓ ]                          4  [ .  .  .  ✓ ]

Resultado: GRUPOS                           Resultado: HIERARQUIA
{1,3} e {2,4}                                   4
Sem direcao, sem hierarquia                    / \      (2 e 3: incomparaveis)
                                              2   3
                                               \ /
                                                1
```

---

**Resumo da distincao:**

| | Equivalencia | Ordem parcial |
|---|---|---|
| Propriedades | reflexiva + **simetrica** + transitiva | reflexiva + **antissimetrica** + transitiva |
| Diferenca-chave | simetrica (ida = volta) | antissimetrica (ida ≠ volta, exceto iguais) |
| O que faz | agrupa elementos "iguais" | organiza em hierarquia |
| Resultado | **classes/particao** (grupos) | **diagrama de Hasse** (hierarquia) |
| Comparabilidade | todo par dentro da classe se relaciona | pode haver pares **incomparaveis** |
| Analogia | separar por cor | organograma |
| Exemplos | ≡ mod n, mesma paridade, igualdade | ≤, divisibilidade, ⊆ entre conjuntos |

## Pontos-chave para a prova
- Saber construir tabelas-verdade
- Dominar a contrapositiva (essencial para provas indiretas)
- Leis de De Morgan (usadas o tempo todo em manipulacao de quantificadores)
- Distinguir entre relacao de equivalencia e de ordem

## Exercicio de fixacao
1. Construa a tabela-verdade de: (p → q) ∧ (q → r) → (p → r)
2. Dada a relacao R em {1,2,3} onde R = {(1,1),(2,2),(3,3),(1,2),(2,1)}, ela e: reflexiva? simetrica? transitiva?

> Respostas: 1- Tautologia (sempre V). 2- Reflexiva (sim), simetrica (sim), transitiva (sim, verificar todos os casos) — e relacao de equivalencia.

## Referencias
- **Book of Proof** (Hammack), Cap. 2 (logica) e Cap. 11 (relacoes) — https://www.people.vcu.edu/~rhammack/BookOfProof/
- **Rosen**, Cap. 1 (conectivos) e Cap. 9 (relacoes)
- **Susanna Epp**, Discrete Mathematics with Applications, Cap. 2 e 8
- **TrevTutor** - Discrete Math (YouTube, EN): truth tables, logical equivalences
- **Neso Academy** - Discrete Mathematics (YouTube, EN)
- **Me Salva!** - Conectivos logicos (https://www.mesalva.com/)
