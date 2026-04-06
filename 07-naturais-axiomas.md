---
layout: page
title: "7. Axiomas de Peano"
nav_order: 7
---
# 7. Numeros Naturais: Formulacao Axiomatica (Axiomas de Peano)

## Resumo

### Motivacao
Em vez de tomar os numeros naturais como "obvios", a matematica os constroi rigorosamente a partir de axiomas. Os **Axiomas de Peano** definem o que e o conjunto N e quais propriedades ele deve satisfazer.

### Os Axiomas de Peano
Existe um conjunto N, um elemento especial 0 ∈ N e uma funcao **sucessor** S: N → N que satisfazem:

| # | Axioma | Significado |
|---|---|---|
| P1 | 0 ∈ N | Zero e um numero natural |
| P2 | ∀n ∈ N, S(n) ∈ N | O sucessor de todo natural e natural (fechamento) |
| P3 | ∀n ∈ N, S(n) ≠ 0 | Zero nao e sucessor de ninguem |
| P4 | ∀m,n ∈ N, S(m) = S(n) → m = n | A funcao sucessor e injetiva |
| P5 | Se A ⊆ N, 0 ∈ A, e (k ∈ A → S(k) ∈ A), entao A = N | Axioma da inducao |

**Observacao:** Algumas formulacoes comecam com 1 em vez de 0. A estrutura e a mesma.

### Entendendo cada axioma

**P1 e P2 (existencia e fechamento):**
Garantem que N nao e vazio e que podemos sempre "avancar" — 0, S(0), S(S(0)), ...
Identificamos: 1 = S(0), 2 = S(S(0)) = S(1), 3 = S(2), ...

**P3 (zero nao e sucessor):**
Impede ciclos do tipo "... → 2 → 0". Garante que N tem um "comeco".

**P4 (injetividade):**
Impede que dois numeros diferentes tenham o mesmo sucessor. Sem P4, poderiamos ter S(2) = S(5) = 3, o que nao faz sentido.

**P5 (inducao):**
E o axioma mais poderoso. Garante que N nao tem "elementos extras" alem de 0, S(0), S(S(0)), ...
Sem P5, poderiamos ter um conjunto que satisfaz P1-P4 mas contem elementos "fantasmas" que nao sao atingiveis a partir de 0 por aplicacoes sucessivas de S.

### O axioma da inducao (P5) em detalhe
P5 e exatamente o **principio de inducao matematica** expresso como axioma:

Para provar que uma propriedade P vale para todo n ∈ N:
1. Mostre P(0) — corresponde a "0 ∈ A"
2. Mostre que P(k) → P(S(k)) — corresponde a "k ∈ A → S(k) ∈ A"
3. Conclua: P(n) para todo n ∈ N — corresponde a "A = N"

### Axiomas de igualdade

Antes de provar qualquer coisa sobre os naturais, precisamos das regras que governam o simbolo "=". Esses axiomas sao usados **implicitamente em toda prova** — sempre que voce escreve uma cadeia de igualdades, esta usando-os.

| # | Axioma | Enunciado | Significado |
|---|--------|-----------|-------------|
| I1 | Reflexividade | ∀a, a = a | Todo objeto e igual a si mesmo |
| I2 | Simetria | ∀a,b, a = b → b = a | Igualdade funciona nos dois sentidos |
| I3 | Transitividade | ∀a,b,c, (a = b ∧ b = c) → a = c | Cadeias de igualdade funcionam |
| I4 | Substituicao | ∀a,b, a = b → (P(a) → P(b)) | Se a = b, tudo que vale para a vale para b |

**Por que isso importa?**

- **I3 (transitividade)** e o que justifica cadeias como: S(S(0)) + S(0) = S(S(S(0)) + 0) = S(S(S(0))). Cada "=" usa uma definicao (A1 ou A2), e a transitividade conecta os passos.
- **I4 (substituicao)** e o que permite "trocar iguais por iguais" dentro de expressoes. Por exemplo, se sabemos que a + 0 = a (por A1), podemos substituir "a + 0" por "a" em qualquer formula.
- No topico 8, toda prova sobre adicao e multiplicacao depende desses axiomas — mesmo quando nao sao mencionados explicitamente.

**Exemplo:** Para justificar que se a = b e c = d, entao a + c = b + d:
1. a = b (hipotese)
2. a + c = b + c (substituicao I4, aplicada a funcao _ + c)
3. c = d (hipotese)
4. b + c = b + d (substituicao I4, aplicada a funcao b + _)
5. a + c = b + d (transitividade I3, passos 2 e 4)

### Consequencias dos axiomas
A partir dos axiomas de Peano, podemos:
- **Definir** adicao e multiplicacao (topico 8)
- **Provar** que N e infinito
- **Provar** propriedades como comutatividade e associatividade
- **Derivar** o principio da boa ordem (topico 9)

### Modelo dos axiomas
O modelo padrao e N = {0, 1, 2, 3, ...} com S(n) = n + 1.
Mas os axiomas tambem admitem modelos nao-padrao (com "numeros infinitamente grandes") — isso e resultado do Teorema da Compacidade da logica de primeira ordem.

## Pontos-chave para a prova
- Saber enunciar os 5 axiomas
- Entender o papel de cada um (especialmente P3, P4 e P5)
- P5 = principio de inducao
- Sem P5, N poderia ter elementos inalcancaveis a partir de 0

## Exercicio de fixacao
1. Qual axioma impede que S(3) = S(7)?
2. Qual axioma garante que podemos usar inducao?
3. Por que precisamos de P3? O que aconteceria se existisse n com S(n) = 0?
4. Use os axiomas para justificar que 0 ≠ 1, 0 ≠ 2, 1 ≠ 2.

> Respostas: 1- P4 (injetividade). 2- P5. 3- Sem P3 teriamos um ciclo (ex: 0→1→2→0), e N seria finito. 4- 0≠1: P3 diz S(0)≠0, logo 1≠0. 0≠2: S(1)≠0 por P3. 1≠2: se S(0)=S(1), por P4 teriamos 0=1, mas ja provamos 0≠1.

## Referencias
- **Terence Tao**, Analysis I, Cap. 2 — construcao detalhada passo a passo
- **Elon Lages Lima**, Curso de Analise Vol.1, Cap. 1
- **UFS** - Aula 17: Axiomas de Peano — https://cesad.ufs.br/ORBI/public/uploadCatalago/15252216022012Fundamentos_de_Matematica_aula_17.pdf
- **UFPR** - Apostila Numeros Naturais — https://docs.ufpr.br/~fernando.avila/Sem2-2023/CMM011/Apostila/N.pdf
- **UEL** - Matematica Essencial: Peano — https://www.uel.br/projetos/matessencial/superior/algebra/naturais_peano.html
- **Wikipedia** - Peano Axioms — https://en.wikipedia.org/wiki/Peano_axioms
