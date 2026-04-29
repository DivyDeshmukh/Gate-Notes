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

These are derived from the primary three and appear heavily in GATE.

| Symbol | Name | Built From |
|--------|------|-----------|
| ↑ | NAND | NOT(AND) |
| ↓ | NOR | NOT(OR) |
| ⊕ | XOR (Exclusive OR) | (p ∨ q) ∧ ¬(p ∧ q) |
| → | Implication (If-Then) | ¬p ∨ q |
| ↔ | Biconditional (If and only if) | (p → q) ∧ (q → p) |

> **Why this matters for GATE:** NAND and NOR are **functionally complete** — any logical expression can be built using only NAND gates or only NOR gates. This appears frequently in Digital Logic too.

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

| Trap | Correct understanding |
|------|----------------------|
| Thinking De Morgan's only works for 2 variables | Works for any number: ¬(p∧q∧r) = ¬p∨¬q∨¬r |
| Confusing AND identity (T) with OR identity (F) | AND + T = itself. OR + F = itself. Opposite of what feels natural. |
| Thinking distributive only works one way | BOTH AND over OR and OR over AND work |
| Mixing up Idempotent and Identity | Idempotent: same variable twice (p∧p=p). Identity: variable + constant (p∧T=p) |
| Forgetting implication ≡ ¬p ∨ q | This comes up constantly in GATE questions |

---

## 13. What's Next

**Next lecture:** Truth Tables for compound propositions — Tautology, Contradiction, Contingency  
**Then:** Logical equivalence and how to prove two expressions are equal without truth tables (using the 10 laws above)

---

*Notes maintained on GitHub · DM_02_Connectives_and_Properties.md · Divy Deshmukh · GATE 2027*
