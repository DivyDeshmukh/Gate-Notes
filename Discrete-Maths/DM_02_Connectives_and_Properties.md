# Discrete Mathematics — Chapter 2: Logical Connectives & Properties of Operators

> **Topic:** Logical Operators / Connectives + Properties of Basic Operators  
> **Prerequisite:** DM_01_Propositions.md  
> **Last Updated:** April 2026

---

## 1. Propositional Variables

When we work with propositions repeatedly, we assign them **variables** to avoid writing the full sentence every time.

```
p : "I have time"
q : "I will go to market"
```

These variables (p, q, r, s...) are called **logical variables** or **propositional variables**.

We can now combine them using **logical operators (connectives)** to form **compound propositions**.

```
p ∧ q  means  "I have time AND I will go to market"
```

---

## 2. Types of Logical Operators

Operators are divided into two categories:

```
Logical Operators
       │
  ┌────┴────┐
Primary   Secondary
(∧, ∨, ¬)  (↑, ↓, ⊕, →, ↔)
```

### Primary Operators (Fundamental / Basic)

These three are the foundation — every other logical operation can be built from them.

| Symbol | Name | Meaning |
|--------|------|---------|
| ∧ | AND (Conjunction) | Both must be true |
| ∨ | OR (Disjunction) | At least one must be true |
| ¬ | NOT (Negation) | Flips the truth value |

### Secondary Operators (Derived)

These 5 operators are built from the primary three. Each one has a specific truth table and a specific meaning you must know cold for GATE.

---

#### ↑ NAND (Not AND)

```
p ↑ q  ≡  ¬(p ∧ q)
```

Truth table:

| p | q | p ∧ q | p ↑ q |
|---|---|-------|-------|
| F | F | F | **T** |
| F | T | F | **T** |
| T | F | F | **T** |
| T | T | T | **F** ← only false when both true |

> **Key insight:** NAND is the exact opposite of AND. AND is only true when both are true. NAND is only false when both are true.

> **Functionally complete:** You can build ANY logical circuit using only NAND gates. This is why CPUs are built from NAND gates — one gate type does everything.

---

#### ↓ NOR (Not OR)

```
p ↓ q  ≡  ¬(p ∨ q)
```

Truth table:

| p | q | p ∨ q | p ↓ q |
|---|---|-------|-------|
| F | F | F | **T** ← only true when both false |
| F | T | T | **F** |
| T | F | T | **F** |
| T | T | T | **F** |

> **Key insight:** NOR is the exact opposite of OR. OR is only false when both are false. NOR is only true when both are false.

> **Also functionally complete:** NOR alone can build any circuit too.

> **GATE trap:** NAND and NOR are both functionally complete. AND, OR, and NOT individually are NOT functionally complete — you need combinations. {AND, NOT} is complete. {OR, NOT} is complete. But AND alone, OR alone, NOT alone — none are.

---

#### ⊕ XOR (Exclusive OR)

```
p ⊕ q  ≡  (p ∨ q) ∧ ¬(p ∧ q)
         ≡  (p ∧ ¬q) ∨ (¬p ∧ q)
```

Truth table:

| p | q | p ⊕ q |
|---|---|-------|
| F | F | **F** |
| F | T | **T** |
| T | F | **T** |
| T | T | **F** ← false when both same |

> **Plain English:** XOR is true when the two inputs are **different**. False when they are the **same**.

> **Memory trick:** "Exclusive OR" — only one of them can be true, not both.

> **GATE uses:** XOR appears in addition circuits, parity checks, and many simplification problems. Key property: `p ⊕ p = 0` (false) and `p ⊕ 0 = p`.

---

#### → Implication (If-Then)

```
p → q  ≡  ¬p ∨ q
```

Read as: "If p then q" or "p implies q"

Truth table:

| p | q | p → q |
|---|---|-------|
| F | F | **T** |
| F | T | **T** |
| T | F | **F** ← only false here |
| T | T | **T** |

> **The hardest one to understand intuitively.** Why is "If p then q" true when p is false?

> **Think of it as a promise:** "If it rains, I will carry an umbrella." This promise is only BROKEN (false) when it rains (p=T) but you don't carry an umbrella (q=F). If it doesn't rain at all (p=F), the promise is never broken — you can't be accused of lying regardless of whether you carry an umbrella or not.

> **Critical GATE equivalence:** `p → q ≡ ¬p ∨ q`  
> This is how every implication gets simplified. Anytime you see an arrow in a GATE question, immediately convert it: flip p to ¬p, change → to ∨.

> **Example:** "If it rains, I carry an umbrella" = "It is not raining OR I carry an umbrella" — logically identical.

---

#### ↔ Biconditional (If and only if)

```
p ↔ q  ≡  (p → q) ∧ (q → p)
         ≡  (¬p ∨ q) ∧ (¬q ∨ p)
         ≡  (p ∧ q) ∨ (¬p ∧ ¬q)
```

Read as: "p if and only if q" (written as "p iff q")

Truth table:

| p | q | p ↔ q |
|---|---|-------|
| F | F | **T** |
| F | T | **F** |
| T | F | **F** |
| T | T | **T** |

> **Plain English:** Biconditional is true when both are the **same** (both T or both F). False when they are **different**.

> **Notice:** XOR and Biconditional are exact opposites of each other.  
> `p ↔ q ≡ ¬(p ⊕ q)` — this is a useful GATE identity.

> **Real life example:** "You pass the exam if and only if you score above 50%."  
> True when: you score above 50 AND you pass. Or you score ≤ 50 AND you fail.  
> False when: you score above 50 but fail (unfair!). Or score ≤ 50 but pass (also unfair!).

---

#### Secondary Operators — Summary Table

| Operator | Symbol | True when | False when |
|----------|--------|-----------|------------|
| NAND | ↑ | At least one is False | Both are True |
| NOR | ↓ | Both are False | At least one is True |
| XOR | ⊕ | Inputs are **different** | Inputs are **same** |
| Implication | → | p is False OR q is True | p is True AND q is False |
| Biconditional | ↔ | Inputs are **same** | Inputs are **different** |

> **Quick opposites to remember:**  
> AND ↔ NAND (flip AND)  
> OR ↔ NOR (flip OR)  
> XOR ↔ Biconditional (they are negations of each other)

---

## 3. The Three Domains — Same Concept, Different Notation

This is a critical insight. The same fundamental operations exist in three different domains, just written differently.

| Concept | Logic | Boolean Algebra | Set Theory |
|---------|-------|----------------|------------|
| AND | ∧ | · (dot) or A' | ∩ (intersection) |
| OR | ∨ | + | ∪ (union) |
| NOT | ¬ | overline (Ā) | Aᶜ (complement) |
| True | T | 1 | U (universal set) |
| False | F | 0 | ∅ (empty set) |

```
Boolean Algebra mapping:
0 → F (False)
1 → T (True)
```

> **Why this matters:** GATE Discrete Math, Digital Logic, and Set Theory all use these same operations. If you understand them once in logic, you understand them in all three domains.

---

## 4. The NOT Operator — Truth Table

The simplest operator. It just flips.

| A | ¬A |
|---|-----|
| T | F |
| F | T |

In Boolean: Ā (A-bar)  
In Sets: Aᶜ

---

## 5. The AND Operator (∧) — Truth Table

AND is **true only when BOTH inputs are true**. One false input makes the whole thing false.

**Logic:**

| A | B | A ∧ B |
|---|---|-------|
| F | F | **F** |
| F | T | F |
| T | F | F |
| T | T | **T** ← only one T |

**Boolean equivalent (A · B):**

| A | B | A·B | A+B | Ā |
|---|---|-----|-----|---|
| 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 |

> **Memory trick for AND:** Think of it as multiplication. 0 × anything = 0. Only 1 × 1 = 1.

---

## 6. The OR Operator (∨) — Truth Table

OR is **false only when BOTH inputs are false**. One true input makes the whole thing true.

| A | B | A ∨ B |
|---|---|-------|
| F | F | **F** ← only one F |
| F | T | T |
| T | F | T |
| T | T | T |

> **Memory trick for OR:** Think of it as addition (Boolean). 1 + anything = 1. Only 0 + 0 = 0.

---

## 7. Set Theory Equivalents — Truth Table

Same operations, set notation. Here ∅ = false, U = true.

| A | B | A ∩ B | A ∪ B | Aᶜ |
|---|---|-------|-------|-----|
| ∅ | ∅ | ∅ | ∅ | U |
| ∅ | U | ∅ | U | U |
| U | ∅ | ∅ | U | ∅ |
| U | U | U | U | ∅ |

---

## 8. Properties of Logical Operators

Divided into **Basic (5)** and **Derived (5)**.

---

### 8.1 BASIC Properties

These 5 properties are the axioms — they are taken as given, not proven.

#### 1. Commutative Law
Order doesn't matter.

```
p ∧ q  ≡  q ∧ p
p ∨ q  ≡  q ∨ p
```

Boolean: A·B = B·A and A+B = B+A  
Set: A ∩ B = B ∩ A and A ∪ B = B ∪ A

---

#### 2. Associative Law
Grouping doesn't matter.

```
(p ∧ q) ∧ r  ≡  p ∧ (q ∧ r)
(p ∨ q) ∨ r  ≡  p ∨ (q ∨ r)
```

> **Note:** AND is associative with AND, OR is associative with OR.  
> You **cannot** mix: (p ∧ q) ∨ r ≠ p ∧ (q ∨ r) — that's distributive, not associative.

---

#### 3. Distributive Law
AND distributes over OR, and OR distributes over AND.

```
p ∧ (q ∨ r)  ≡  (p ∧ q) ∨ (p ∧ r)    [AND over OR]
p ∨ (q ∧ r)  ≡  (p ∨ q) ∧ (p ∨ r)    [OR over AND]
```

Boolean equivalent:
```
A · (B + C)  =  A·B + A·C
A + (B · C)  =  (A+B) · (A+C)
```

> **GATE tip:** Both directions work. Unlike regular arithmetic where only multiplication distributes over addition, in Boolean/Logic **both** operators distribute over the other.

---

#### 4. Identity Law
Operating with the identity element leaves the variable unchanged.

```
p ∧ T  ≡  p          (AND with True = itself)
p ∨ F  ≡  p          (OR with False = itself)
```

Boolean:
```
A · 1  =  A
A + 0  =  A
```

> **Memory trick:** True is the identity for AND (like 1 in multiplication). False is the identity for OR (like 0 in addition).

---

#### 5. Complement Law
A variable AND its negation = False. A variable OR its negation = True.

```
p ∧ ¬p  ≡  F          (Contradiction — can't be both T and F)
p ∨ ¬p  ≡  T          (Tautology — must be one or the other)
```

Boolean:
```
A · Ā  =  0
A + Ā  =  1
```

---

### 8.2 DERIVED Properties

These 5 are **proved** from the basic 5 above — they are not axioms.

#### 6. Idempotent Law
Operating a variable with itself gives itself.

```
p ∧ p  ≡  p
p ∨ p  ≡  p
```

Boolean: A · A = A and A + A = A

> **Proof of A · A = A:**  
> A · A = A · A + 0 = A · A + A · Ā = A · (A + Ā) = A · 1 = A ✓

> **Why "derived"?** Because we can prove it using Identity and Complement laws. It's not assumed.

---

#### 7. Absorption Law
One variable "absorbs" the compound expression.

```
p ∧ (p ∨ q)  ≡  p          [AND absorbs OR]
p ∨ (p ∧ q)  ≡  p          [OR absorbs AND]
```

Boolean:
```
A · (A + B)  =  A
A + (A · B)  =  A
```

> **Intuition for p ∨ (p ∧ q) = p:** If p is true, the whole thing is true regardless of q. If p is false, p ∧ q is also false, so the result is false. Either way — the result is just p.

---

#### 8. Law of Double Complement (Double Negation)
Two negations cancel out.

```
¬(¬p)  ≡  p
```

Boolean: $\overline{\overline{A}}$ = A

> **Intuition:** Saying "it is not the case that it is not raining" = "it is raining."

---

#### 9. De Morgan's Laws ⭐
**Most important derived law. Appears in almost every GATE paper.**

```
¬(p ∧ q)  ≡  ¬p ∨ ¬q          [NOT of AND = OR of NOTs]
¬(p ∨ q)  ≡  ¬p ∧ ¬q          [NOT of OR = AND of NOTs]
```

Boolean:
```
(A · B)̄  =  Ā + B̄
(A + B)̄  =  Ā · B̄
```

Set theory:
```
(A ∩ B)ᶜ  =  Aᶜ ∪ Bᶜ
(A ∪ B)̄ᶜ  =  Aᶜ ∩ Bᶜ
```

**Proof by truth table:**

| p | q | p ∧ q | ¬(p ∧ q) | ¬p | ¬q | ¬p ∨ ¬q |
|---|---|-------|----------|----|----|---------|
| T | T | T | **F** | F | F | **F** ✓ |
| T | F | F | **T** | F | T | **T** ✓ |
| F | T | F | **T** | T | F | **T** ✓ |
| F | F | F | **T** | T | T | **T** ✓ |

Both columns match → De Morgan's first law is proved.

> **GATE trick — how to remember:**  
> When you push NOT inside a bracket, **flip the operator** (∧ ↔ ∨) and negate each variable.  
> `¬(p ∧ q ∧ r)` = `¬p ∨ ¬q ∨ ¬r`  
> `¬(p ∨ q ∨ r)` = `¬p ∧ ¬q ∧ ¬r`

---

#### 10. Domination Law
Certain fixed values dominate regardless of the other operand.

```
p ∧ F  ≡  F          (AND with False always gives False)
p ∨ T  ≡  T          (OR with True always gives True)
```

Boolean:
```
A · 0  =  0
A + 1  =  1
```

> **Memory trick:** False dominates AND (one false kills everything). True dominates OR (one true saves everything).

---

## 9. All 10 Properties — Quick Reference Table

| # | Law | AND form | OR form |
|---|-----|---------|---------|
| 1 | Commutative | p∧q ≡ q∧p | p∨q ≡ q∨p |
| 2 | Associative | (p∧q)∧r ≡ p∧(q∧r) | (p∨q)∨r ≡ p∨(q∨r) |
| 3 | Distributive | p∧(q∨r) ≡ (p∧q)∨(p∧r) | p∨(q∧r) ≡ (p∨q)∧(p∨r) |
| 4 | Identity | p∧T ≡ p | p∨F ≡ p |
| 5 | Complement | p∧¬p ≡ F | p∨¬p ≡ T |
| 6 | Idempotent | p∧p ≡ p | p∨p ≡ p |
| 7 | Absorption | p∧(p∨q) ≡ p | p∨(p∧q) ≡ p |
| 8 | Double Complement | ¬(¬p) ≡ p | — |
| 9 | De Morgan's | ¬(p∧q) ≡ ¬p∨¬q | ¬(p∨q) ≡ ¬p∧¬q |
| 10 | Domination | p∧F ≡ F | p∨T ≡ T |

**Basic (1–5):** Commutative, Associative, Distributive, Identity, Complement  
**Derived (6–10):** Idempotent, Absorption, Double Complement, De Morgan's, Domination

---

## 10. Summary — Revision Card

```
PRIMARY OPERATORS:  ∧ (AND)  ∨ (OR)  ¬ (NOT)
SECONDARY:          ↑ NAND   ↓ NOR   ⊕ XOR   → Implication   ↔ Biconditional

TRUTH TABLE KEY FACTS:
  AND: True only when BOTH are True
  OR:  False only when BOTH are False
  NOT: Just flips T↔F

BOOLEAN MAPPING:  0=F, 1=T, ·=AND, +=OR, overline=NOT

DE MORGAN'S (most important):
  ¬(p ∧ q) = ¬p ∨ ¬q    → push NOT in, flip the operator
  ¬(p ∨ q) = ¬p ∧ ¬q    → push NOT in, flip the operator

DOMINATION vs IDENTITY:
  AND: F dominates, T is identity
  OR:  T dominates, F is identity
```

---

## 11. Practice Questions

---

**Q1.** Simplify: `p ∧ (p ∨ q)`

<details>
<summary>Answer</summary>

**= p**  
This is the **Absorption Law**: p ∧ (p ∨ q) ≡ p  
The outer AND with p absorbs the inner OR expression.

</details>

---

**Q2.** Simplify: `¬(¬p ∨ ¬q)`

<details>
<summary>Answer</summary>

Apply De Morgan's to flip the outer NOT inside:  
`¬(¬p ∨ ¬q) = ¬(¬p) ∧ ¬(¬q)` ← flip ∨ to ∧, negate each  
`= p ∧ q` ← double complement cancels  
**= p ∧ q**

</details>

---

**Q3.** Which law states: `p ∨ (p ∧ q) ≡ p`?

<details>
<summary>Answer</summary>

**Absorption Law**  
OR form: p ∨ (p ∧ q) ≡ p

</details>

---

**Q4.** Simplify: `(p ∧ q) ∨ (p ∧ ¬q)`

<details>
<summary>Answer</summary>

Factor out p using Distributive Law:  
`= p ∧ (q ∨ ¬q)`  
`= p ∧ T` ← Complement Law: q ∨ ¬q = T  
`= p` ← Identity Law  
**= p**

</details>

---

**Q5.** Simplify: `p ∨ (¬p ∧ q)`

<details>
<summary>Answer</summary>

Use Distributive Law:  
`= (p ∨ ¬p) ∧ (p ∨ q)` ← OR distributes over AND  
`= T ∧ (p ∨ q)` ← Complement Law  
`= p ∨ q` ← Identity Law  
**= p ∨ q**

</details>

---

**Q6.** Prove: `p ∧ F ≡ F` using other laws (not just stating it).

<details>
<summary>Answer</summary>

```
p ∧ F
= p ∧ (p ∧ ¬p)     ← Complement Law: p ∧ ¬p = F
= (p ∧ p) ∧ ¬p     ← Associative Law
= p ∧ ¬p            ← Idempotent: p ∧ p = p
= F                 ← Complement Law
```
**= F** ✓

</details>

---

**Q7.** What does De Morgan's give you for `¬(p ∧ q ∧ r)`?

<details>
<summary>Answer</summary>

Apply De Morgan's:  
`¬(p ∧ q ∧ r) = ¬p ∨ ¬q ∨ ¬r`  

Thinking of it step by step:  
`¬((p ∧ q) ∧ r) = ¬(p ∧ q) ∨ ¬r = (¬p ∨ ¬q) ∨ ¬r = ¬p ∨ ¬q ∨ ¬r`

**= ¬p ∨ ¬q ∨ ¬r**

</details>

---

**Q8. [GATE-style]** Which of the following is equivalent to `¬p ∨ q`?

(a) p ∧ ¬q  
(b) p → q  
(c) p ↔ q  
(d) ¬(p ∨ q)

<details>
<summary>Answer</summary>

**(b) p → q**  

The definition of implication is: `p → q ≡ ¬p ∨ q`  
This is one of the most important equivalences for GATE — implication can always be rewritten as OR.

</details>

---

**Q9.** True or False: Complement Law and Domination Law say the same thing.

<details>
<summary>Answer</summary>

**False — they are different.**

| Law | AND form | OR form |
|-----|---------|---------|
| Complement | p ∧ ¬p ≡ F | p ∨ ¬p ≡ T |
| Domination | p ∧ F ≡ F | p ∨ T ≡ T |

Complement involves a variable and its negation.  
Domination involves a variable and a fixed constant (T or F).  
They both produce the same results (F for AND, T for OR) but through different mechanisms.

</details>

---

**Q10. [GATE-style]** Simplify the Boolean expression: `A + A·B`

<details>
<summary>Answer</summary>

This is **Absorption Law** in Boolean notation:  
`A + A·B = A` ← OR form: p ∨ (p ∧ q) ≡ p  
**= A**

</details>

---

## 12. Common GATE Traps

**Trap 1 — De Morgan's only for 2 variables**

Wrong thinking: De Morgan's applies only to `¬(p ∧ q)`.

Correct: Works for any number of variables. Just push NOT inside and flip every operator.

```
¬(p ∧ q ∧ r)   =   ¬p ∨ ¬q ∨ ¬r
¬(p ∨ q ∨ r)   =   ¬p ∧ ¬q ∧ ¬r
```

---

**Trap 2 — Confusing AND identity vs OR identity**

AND identity = **True** → `p ∧ T = p`  
OR identity = **False** → `p ∨ F = p`

Why does this feel backwards? Because you're used to arithmetic where + is the "simpler" operation and × is "bigger." In logic, AND behaves like multiplication (×) and OR behaves like addition (+).

```
Arithmetic:   n × 1 = n   →   AND: p ∧ T = p     (T is the 1 of AND)
Arithmetic:   n + 0 = n   →   OR:  p ∨ F = p     (F is the 0 of OR)
```

Once you see AND=× and OR=+, the identities are exactly what you already know.

---

**Trap 3 — Distributive only works one way**

Both directions work in logic — unlike arithmetic where only × distributes over +:

```
AND over OR:   p ∧ (q ∨ r)  =  (p ∧ q) ∨ (p ∧ r)   ✓
OR over AND:   p ∨ (q ∧ r)  =  (p ∨ q) ∧ (p ∨ r)   ✓ (this one has no arithmetic equivalent)
```

---

**Trap 4 — Forgetting implication ≡ ¬p ∨ q**

This is the single most-used equivalence in GATE Discrete Math questions. Any time you see → in a simplification problem, your first move is to rewrite it.

```
p → q   becomes   ¬p ∨ q
```

The pattern: **flip the left side (NOT it), change arrow to OR, right side stays.**

Multi-step example:
```
(p → q) → r
= (¬p ∨ q) → r          ← convert inner implication
= ¬(¬p ∨ q) ∨ r         ← convert outer implication
= (p ∧ ¬q) ∨ r          ← De Morgan's on ¬(¬p ∨ q)
```

---

**Trap 5 — XOR vs Biconditional**

```
XOR (⊕):           TRUE when inputs are DIFFERENT
Biconditional (↔):  TRUE when inputs are SAME
```

They are exact opposites: `p ↔ q ≡ ¬(p ⊕ q)`

Easy check: look at the T,T row. XOR gives F (same = false for XOR). Biconditional gives T (same = true for bicon).

---

**Trap 6 — Treating implication as symmetric**

`p → q` and `q → p` are completely different statements.

```
"If it rains, I carry an umbrella"   (p → q)
"If I carry an umbrella, it rains"   (q → p)   ← clearly not the same
```

Direction matters. This is why the biconditional (p ↔ q) exists — it means BOTH directions hold simultaneously.

---

## 13. What's Next

**Next lecture:** Truth Tables for compound propositions — Tautology, Contradiction, Contingency  
**Then:** Logical equivalence and how to prove two expressions are equal without truth tables (using the 10 laws above)

---
