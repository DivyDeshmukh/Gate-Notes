# Discrete Mathematics — Chapter 3: Derived Operators & Their Properties

> **Topic:** Derived Operators — Truth Tables, Commutativity, Associativity, Implication Properties
> **Prerequisite:** DM_02_Connectives_and_Properties.md
> **Last Updated:** April 2026

---

## 1. The Five Derived Operators — Quick Recall

```
↑   NAND          (Not AND)
↓   NOR           (Not OR)
⊕   XOR           (Exclusive OR)
→   Implication   (If-Then)
↔   Biconditional (If and only if)
⊙   XNOR          (Exclusive NOR — similarity operator)
```

> **Note:** XNOR (⊙) is the complement of XOR. ⊕ checks differences, ⊙ checks similarities. Both appear heavily in GATE.

---

## 2. Complete Truth Tables — All Derived Operators

| p | q | p↑q | p↓q | p⊕q | p→q | p↔q (p⊙q) |
|---|---|-----|-----|-----|-----|------------|
| F | F | T   | T   | F   | T   | T          |
| F | T | T   | F   | T   | T   | F          |
| T | F | T   | F   | T   | F   | F          |
| T | T | F   | F   | F   | T   | T          |

**Read each column:**

| Operator | True when | False when |
|----------|-----------|------------|
| NAND ↑ | At least one is F | Both are T (only TT row) |
| NOR ↓ | Both are F (only FF row) | At least one is T |
| XOR ⊕ | Inputs are DIFFERENT | Inputs are SAME |
| → | p is F OR q is T | p is T AND q is F (only TF row) |
| ↔ / XNOR ⊙ | Inputs are SAME | Inputs are DIFFERENT |

> **Memory trick:** NAND and NOR are just AND and OR with their truth tables flipped completely. XOR and XNOR (↔) are opposites of each other.

---

## 3. XOR and XNOR — Negation Identities

⊕ checks **differences** between two values.
⊙ checks **similarities** between two values.

When you negate one input, differences become similarities and vice versa:

```
¬p ⊕  q  =  p ⊙ q
 p ⊕ ¬q  =  p ⊙ q
¬p ⊙  q  =  p ⊕ q
 p ⊙ ¬q  =  p ⊕ q
¬p ⊕ ¬q  =  p ⊙ q    ← negating BOTH keeps similarity
¬p ⊙ ¬q  =  p ⊙ q    ← negating BOTH keeps similarity
```

**Intuition:** If you flip one side, you flip whether you're checking differences or similarities. If you flip both sides, the comparison stays the same.

**Proof for ¬p ⊕ q = p ⊙ q using truth table:**

| p | q | ¬p | ¬p ⊕ q | p ⊙ q |
|---|---|----|--------|-------|
| F | F | T  | T⊕F=T  | T ✓   |
| F | T | T  | T⊕T=F  | F ✓   |
| T | F | F  | F⊕F=F  | F ✓   |
| T | T | F  | F⊕T=T  | T ✓   |

Both columns match — identity proved.

---

## 4. Commutativity — Which Operators Commute?

**Rule:** An operator ★ is commutative if p★q = q★p for all p, q.

| Operator | Commutative? | Why |
|----------|-------------|-----|
| ↑ NAND | ✅ Yes | p↑q ↔ q↑p |
| ↓ NOR | ✅ Yes | p↓q ↔ q↓p |
| ⊕ XOR | ✅ Yes | p⊕q ↔ q⊕p |
| → Implication | ❌ **NO** | p→q ≠ q→p |
| ↔ Biconditional | ✅ Yes | p↔q ↔ q↔p |
| ⊙ XNOR | ✅ Yes | p⊙q ↔ q⊙p |

> **Key rule to memorise:** **All derived operators are commutative EXCEPT →**

**Why → is NOT commutative:**
```
"If it rains, I carry an umbrella"   (p → q)
"If I carry an umbrella, it rains"   (q → p)
```
These are clearly different statements. When p=T, q=F: p→q is F but q→p is T. Different results → not commutative.

---

## 5. Associativity — Which Operators Associate?

**Rule:** An operator ★ is associative if (p★q)★r = p★(q★r) for all p, q, r.

| Operator | Associative? |
|----------|-------------|
| ↑ NAND | ❌ No |
| ↓ NOR | ❌ No |
| ⊕ XOR | ✅ Yes |
| → Implication | ❌ No |
| ↔ / ⊙ Biconditional/XNOR | ✅ Yes |

> **Key rule:** Only ⊕ and ⊙ are associative among derived operators.

---

### 5.1 Proof: NAND is NOT Associative

We need to show: p↑(q↑r) ≠ (p↑q)↑r

Convert using Boolean (↑ means NOT AND, so A↑B = Ā+B̄ by De Morgan):

**Left side:** p↑(q↑r)
```
q↑r = q̄ + r̄           ← De Morgan on q↑r
p↑(q̄+r̄) = p̄ + (q̄+r̄)̄   ← apply NAND definition
         = p̄ + (q · r)  ← De Morgan on overline(q̄+r̄)
         = p̄ + qr
```

**Right side:** (p↑q)↑r
```
p↑q = p̄ + q̄             ← De Morgan
(p̄+q̄)↑r = (p̄+q̄)̄ + r̄    ← apply NAND definition
         = (p · q) + r̄   ← De Morgan on overline(p̄+q̄)
         = pq + r̄
```

**Compare:**
```
Left:   p̄ + qr
Right:  pq + r̄
```

These are NOT equal — NAND is not associative. ✓

---

### 5.2 Proof: NOR is NOT Associative

Similar reasoning. Convert using Boolean (A↓B = Ā·B̄):

**Left:** p↓(q↓r)
```
q↓r = q̄·r̄
p↓(q̄·r̄) = p̄·(q̄·r̄)̄ = p̄·(q+r)
```

**Right:** (p↓q)↓r
```
p↓q = p̄·q̄
(p̄·q̄)↓r = (p̄·q̄)̄·r̄ = (p+q)·r̄
```

```
Left:  p̄·(q+r) = p̄q + p̄r
Right: (p+q)·r̄ = pr̄ + qr̄
```

Not equal → NOR is not associative. ✓

---

### 5.3 Proof: XOR IS Associative

We need to show: (p⊕q)⊕r = p⊕(q⊕r)

**Convert XOR to Boolean:** p⊕q = p̄q + pq̄

**Left side:** (p⊕q)⊕r
```
Let A = p⊕q = p̄q + pq̄
A⊕r = Ār + Ar̄
     = (p̄q + pq̄)̄·r + (p̄q + pq̄)·r̄
     = (p̄q̄ + pq)·r + (p̄q + pq̄)·r̄     ← De Morgan + distribute
     = p̄q̄r + pqr + p̄qr̄ + pq̄r̄
```

**Right side:** p⊕(q⊕r)
```
Let B = q⊕r = q̄r + qr̄
p⊕B = p̄B + pB̄
     = p̄(q̄r + qr̄) + p(q̄r + qr̄)̄
     = p̄q̄r + p̄qr̄ + p(qr + q̄r̄)        ← De Morgan on overline B
     = p̄q̄r + p̄qr̄ + pqr + pq̄r̄
```

Both sides = **p̄q̄r + pqr + p̄qr̄ + pq̄r̄** ✓

XOR is associative. This is why we can write p⊕q⊕r without brackets.

---

### 5.4 Proof: → is NOT Associative

We need to show: (p→q)→r ≠ p→(q→r)

**Left side:** (p→q)→r
```
p→q = p̄ + q                    ← key implication equivalence
(p̄+q)→r = (p̄+q)̄ + r           ← apply → definition again
         = (p·q̄) + r            ← De Morgan on overline(p̄+q)
         = pq̄ + r
```

**Right side:** p→(q→r)
```
q→r = q̄ + r
p→(q̄+r) = p̄ + (q̄+r) = p̄ + q̄ + r
```

**Compare:**
```
Left:  pq̄ + r
Right: p̄ + q̄ + r
```

Different. So (p→q)→r ≠ p→(q→r) → Implication is NOT associative. ✓

---

## 6. Key Implication Equivalences

These come directly from the definition p→q ≡ ¬p∨q:

### 6.1 The core equivalence
```
p → q  ≡  ¬p ∨ q
```
> This is the most important. Every time you see → in GATE, convert it immediately.

### 6.2 Contrapositive
```
p → q  ≡  ¬q → ¬p
```
The contrapositive is logically identical to the original — same truth table.

Example:
```
"If it rains → I carry umbrella"
Contrapositive: "If I don't carry umbrella → it doesn't rain"
Both say the exact same thing.
```

> **GATE trap:** The CONVERSE (q→p) and INVERSE (¬p→¬q) are NOT equivalent to p→q. Only the contrapositive is.

### 6.3 Converse and Inverse — NOT equivalent to original

```
Original:   p → q
Converse:   q → p        ← NOT equivalent to original
Inverse:    ¬p → ¬q      ← NOT equivalent to original
Contrapositive: ¬q → ¬p  ← equivalent to original ✓
```

| Pair | Equivalent? |
|------|------------|
| Original ↔ Contrapositive | ✅ Yes |
| Converse ↔ Inverse | ✅ Yes (to each other, not to original) |
| Original ↔ Converse | ❌ No |
| Original ↔ Inverse | ❌ No |

---

## 7. Distributivity of → Over Other Operators

→ does NOT distribute over all operators. Here's what holds:

```
→ distributes over ∨:
p → (q ∨ r)  ↔  (p→q) ∨ (p→r)   ✓

→ distributes over ∧:
p → (q ∧ r)  ↔  (p→q) ∧ (p→r)   ✓

→ distributes over ⊕:
p → (q ⊕ r)  ↔  (p→q) ⊕ (p→r)   ✓

⊕ distributes over →:
p ⊕ (q → r)  ↔  (p⊕q) → (p⊕r)   ✓
```

> **GATE note:** → is distributive over ∨. This question "is → distributive over ∨?" is directly from the lecture and the answer is YES.

---

## 8. Properties Summary — All Derived Operators

| Property | ↑ | ↓ | ⊕ | → | ↔/⊙ |
|----------|---|---|---|---|-----|
| Commutative | ✅ | ✅ | ✅ | ❌ | ✅ |
| Associative | ❌ | ❌ | ✅ | ❌ | ✅ |
| Idempotent (p★p=p) | ❌ | ❌ | ❌ | ✅ | ✅ |

**Idempotent details:**
```
p ↑ p = ¬p     (not idempotent — gives NOT p, not p)
p ↓ p = ¬p     (not idempotent — gives NOT p, not p)
p ⊕ p = F      (not idempotent — always gives False)
p → p = T      (always True — tautology, not idempotent in standard sense)
p ↔ p = T      (always True — tautology)
```

> GATE trick: p⊕p = F always. p⊙p = T always. These are very commonly tested.

---

## 9. The □ Operator — What is It?

The lecture introduces a mystery operator □ with this truth table:

| p | q | p □ q |
|---|---|-------|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

Observe: the output is always ¬p regardless of q. This means:
- □ is **NOT commutative** (q□p would give ¬q, which is different)
- □ is **NOT associative**
- p□q ≠ q□p

> **Why this matters for GATE:** This is a trick to test whether you identify an operator's properties from its truth table without getting distracted by the symbol. Always build the truth table first, then determine properties from the table — don't assume based on the symbol.

---

## 10. Quick Reference — GATE Essentials

```
COMMUTATIVITY:
  All commutative EXCEPT →
  Remember: "Arrow doesn't turn around"

ASSOCIATIVITY:
  Only ⊕ and ⊙ are associative
  ↑, ↓, → are NOT associative

IMPLICATION CONVERSION (use instantly):
  p → q  ≡  ¬p ∨ q     ← flip left, change to OR
  p → q  ≡  ¬q → ¬p    ← contrapositive

XOR/XNOR TOGGLE:
  Negate one side → switches between ⊕ and ⊙
  Negate both sides → stays the same operator

KEY VALUES:
  p ⊕ p = F     p ⊙ p = T
  p ⊕ 0 = p     p ⊕ 1 = ¬p
  p → p = T     (always tautology)
  p ↔ p = T     (always tautology)
```

---

## 11. Practice Questions

---

**Q1.** Is NAND commutative? Justify.

<details>
<summary>Answer</summary>

**Yes.** p↑q = ¬(p∧q) = ¬(q∧p) = q↑p by commutativity of AND. The result is symmetric in p and q, so order doesn't matter.

</details>

---

**Q2.** Is NAND associative? Give a counterexample.

<details>
<summary>Answer</summary>

**No.** Let p=T, q=T, r=F:

Left: p↑(q↑r) = T↑(T↑F) = T↑T = F
Right: (p↑q)↑r = (T↑T)↑F = F↑F = T

F ≠ T → NAND is not associative.

</details>

---

**Q3.** Simplify: ¬p ⊕ ¬q

<details>
<summary>Answer</summary>

Negate both sides of p⊕q. From the identity: ¬p⊕¬q = p⊙q = p↔q

**= p ↔ q**

(Negating both sides of XOR keeps the similarity operator — they cancel each other out.)

</details>

---

**Q4.** Is (p→q)→r the same as p→(q→r)?

<details>
<summary>Answer</summary>

**No** — → is not associative.

Counterexample: p=F, q=F, r=F

Left: (F→F)→F = T→F = **F**
Right: F→(F→F) = F→T = **T**

F ≠ T. Brackets matter with implication.

</details>

---

**Q5.** Express p→q using only ∧ and ¬

<details>
<summary>Answer</summary>

```
p → q  ≡  ¬p ∨ q        ← definition
       ≡  ¬(¬(¬p ∨ q))   ← double negation
       ≡  ¬(p ∧ ¬q)      ← De Morgan on inner
```

**= ¬(p ∧ ¬q)**

</details>

---

**Q6.** What is p⊕p⊕p⊕p (four times)?

<details>
<summary>Answer</summary>

```
p ⊕ p = F         (first pair)
F ⊕ p = p         (F is identity for XOR)
p ⊕ p = F         (last pair)
```

Or simply: even number of p's → F, odd number → p.
Four is even → **= F**

> GATE pattern: p repeated n times under XOR: if n is even = F, if n is odd = p.

</details>

---

**Q7. [GATE style]** Which of the following is NOT commutative?

(a) p ↑ q  (b) p ↓ q  (c) p → q  (d) p ⊕ q

<details>
<summary>Answer</summary>

**(c) p → q**

All derived operators are commutative EXCEPT implication. p→q means "if p then q" which is different from q→p ("if q then p").

</details>

---

**Q8. [GATE style]** Which pair of operators is associative?

(a) ↑ and ↓  (b) ⊕ and ↔  (c) → and ↑  (d) ↓ and ⊕

<details>
<summary>Answer</summary>

**(b) ⊕ and ↔**

Only XOR (⊕) and Biconditional/XNOR (↔ or ⊙) are associative among derived operators. ↑, ↓, and → are all non-associative.

</details>

---

**Q9.** Prove: p→q ≡ ¬q→¬p (contrapositive)

<details>
<summary>Answer</summary>

```
¬q → ¬p
≡ ¬(¬q) ∨ ¬p       ← implication definition: A→B = ¬A∨B
≡ q ∨ ¬p            ← double negation
≡ ¬p ∨ q            ← commutativity of ∨
≡ p → q             ← implication definition in reverse
```

Proved. ✓

</details>

---

**Q10.** Given p⊕q = r, what is p⊕r?

<details>
<summary>Answer</summary>

```
p ⊕ r = p ⊕ (p ⊕ q)   ← substitute r = p⊕q
      = (p ⊕ p) ⊕ q    ← associativity of ⊕
      = F ⊕ q           ← p⊕p = F
      = q               ← F is identity for ⊕
```

**= q**

> This is a very common GATE pattern. XOR is its own inverse: if you know p⊕q=r, then p⊕r=q and q⊕r=p.

</details>

---

## 12. What's Next

**Next topic:** Tautology, Contradiction, Contingency — classifying compound propositions by their truth tables
**Then:** Logical equivalence proofs using the 10 laws without truth tables

---
