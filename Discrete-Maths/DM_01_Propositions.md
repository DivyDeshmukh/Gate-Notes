# Discrete Mathematics — Chapter 1: Propositions (Logical Statements)

> **Source:** Amit Khurana — DM for GATE  
> **Subject:** Discrete Mathematics  
> **Topic:** Propositional Logic — Lecture 1  
> **Last Updated:** April 2026

---

## 1. What is a Proposition?

> **Definition:** A **proposition** (also called a logical statement) is any **declarative sentence** that is **either true or false, but not both.**

Three words to lock in:

| Word | Meaning |
|------|---------|
| **Declarative** | It makes a factual claim about the world — not a question, command, or exclamation |
| **Either True or False** | It must have a definite truth value |
| **But Not Both** | It cannot be both true and false at the same time (Law of Non-Contradiction) |

---

## 2. Types of Sentences — Which Are Propositions?

There are 4 types of sentences in English. Only **declarative** sentences can be propositions.

| Sentence Type | Example | Proposition? | Why |
|---|---|---|---|
| Declarative | "The moon is made of cheese" | ✅ Yes | Makes a factual claim — it's false, but it has a truth value |
| Interrogative (question) | "Who are you?" | ❌ No | Questions don't have truth values |
| Imperative (command) | "Get out!" | ❌ No | Commands are neither true nor false |
| Exclamatory | "What a car!" | ❌ No | Exclamations express emotion, not facts |

---

## 3. Key Rules for Identifying Propositions

### Rule 1 — A proposition must be a closed statement

A statement with **free variables** (unknowns) is **NOT** a proposition because its truth value is undefined.

```
x + y = 2     ❌ NOT a proposition  (x and y are unknown — could be true or false)
2 + 3 = 5     ✅ Proposition (True)
2 + 3 = 6     ✅ Proposition (False)
```

> **GATE trick:** Open statements like `x > 5` or `P(x) = true` are called **predicates**, not propositions. A predicate becomes a proposition only when the variable is assigned a value or **quantified** (e.g., "for all x" or "there exists x").

### Rule 2 — Pronouns without context make a statement non-propositional

```
"Amit is tall"    ✅ Proposition (specific person, has a truth value)
"He is tall"      ❌ NOT a proposition (who is "he"? — undefined reference)
```

### Rule 3 — A proposition must be completely stated

```
"Two plus three is —"    ❌ NOT a proposition (incomplete sentence)
"Two plus three is five" ✅ Proposition (True)
```

### Rule 4 — Future uncertain statements

```
"Tomorrow it will rain"    ✅ Proposition (it will either rain or not — definite truth value even if unknown now)
"Tomorrow it may rain"     ❌ Debatable — "may" expresses possibility, not a definite claim
```

> **GATE note:** Most GATE questions treat future statements with "will" as propositions (truth value exists, just not known yet). Statements with "may", "might", "possibly" are often excluded. When in doubt, follow this rule.

---

## 4. Examples From the Lecture — Classified

| Statement | Proposition? | Truth Value | Reason |
|---|---|---|---|
| Moon is made of cheese | ✅ Yes | False | Declarative — factually wrong but has a definite value |
| Jupiter is made of gas | ✅ Yes | True | Declarative factual statement |
| Amit is tall | ✅ Yes | True/False | Specific person, definite value |
| He is tall | ❌ No | — | Pronoun without reference = undefined |
| 2 + 3 = 5 | ✅ Yes | True | Mathematical statement — completely defined |
| 2 + 3 = 6 | ✅ Yes | False | Mathematical statement — false but has truth value |
| x + y = 2 | ❌ No | — | Free variables — open statement |
| Get out! | ❌ No | — | Imperative sentence |
| What a car! | ❌ No | — | Exclamatory sentence |
| Who are you? | ❌ No | — | Interrogative sentence |
| Two plus three is — | ❌ No | — | Incomplete statement |

---

## 5. The Liar Paradox

This is the most famous example of something that **looks** like a proposition but **isn't**.

### Statement: *"This sentence is false."*

Let's trace what happens:

```
Assume it is TRUE
→ Then what it says must hold
→ It says "this sentence is false"
→ So it must be FALSE
→ Contradiction!

Assume it is FALSE
→ Then what it says is wrong
→ It says "this sentence is false" — if that's wrong, then it must be TRUE
→ Contradiction again!
```

**Conclusion:** This statement can be neither consistently true nor consistently false. It violates the definition of a proposition.

> This is called a **self-referential** or **self-contradictory** sentence. It refers to itself in a way that creates an infinite loop of contradictions.

### Other forms of the Liar Paradox:

| Statement | Why it's a paradox |
|---|---|
| "This sentence is false" | Self-referential contradiction |
| "I am lying" | If I'm lying about lying, I'm telling the truth — which means I'm lying — loop |
| "This statement is not true" | Same mechanism |

### What about *"This sentence is true"*?

```
Assume it is TRUE → It says it's true → Consistent ✅
Assume it is FALSE → It says it's true but we said it's false → Consistent ✅
```

It can be either true or false without contradiction — but we **cannot determine which one**. It is therefore also **not a proposition** because the truth value cannot be determined even in principle.

> **Key distinction for GATE:**
> - "This sentence is false" — NOT a proposition (creates contradiction)
> - "This sentence is true" — NOT a proposition (truth value is indeterminate)
> - Both are **self-referential sentences** and are excluded from propositional logic

### Why This Matters for GATE

GATE occasionally asks questions like:

> *"Which of the following is NOT a proposition?"*
> (a) The moon orbits the earth  
> (b) This statement is false  
> (c) 5 is a prime number  
> (d) x + 1 = 5  

**Answer: (b) and (d)** — (b) is the liar paradox, (d) has a free variable. If asked to pick one, the most famous non-proposition is (b).

---

## 6. Notation

Propositions are denoted by lowercase letters:

```
p, q, r, s  — proposition variables
p: "The sky is blue"   →  p is True (T)
q: "5 is even"         →  q is False (F)
```

---

## 7. Summary — Quick Revision Card

```
PROPOSITION = Declarative + Definite truth value (T or F) + Not both

NOT a proposition if:
  → Question / Command / Exclamation
  → Contains free variables (x, y without values)
  → Has an ambiguous pronoun (he, she, they — without context)
  → Self-referential paradox (liar paradox)
  → Incomplete sentence

LIAR PARADOX:
  "This sentence is false" → Neither T nor F → Not a proposition
  Key: self-reference creates contradiction
```

---

## 8. Practice Questions

Classify each as **Proposition (P)** or **Not a Proposition (NP)** and give the reason.

---

**Q1.** 4 is a prime number.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value: **False** (4 is divisible by 2, so not prime)  
It's a clear declarative statement with a definite truth value.

</details>

---

**Q2.** I have time and I will go to town.

<details>
<summary>Answer</summary>

**P — Proposition**  
This is a **compound proposition** (two statements joined by "and").  
Each part has a truth value, so the whole sentence has a truth value.  
Note: "I" here refers to a specific person in context — not ambiguous like "he/she".

</details>

---

**Q3.** Tomorrow it will rain.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value is unknown but **definite** — it will either rain or it won't.  
Future statements with "will" are generally accepted as propositions in GATE.

</details>

---

**Q4.** Tomorrow it may rain.

<details>
<summary>Answer</summary>

**NP — Not a Proposition** (debatable, but most standard texts say NP)  
"May" expresses possibility, not a definite claim.  
It doesn't assert that it will or won't rain — it sits in a middle ground.  
**GATE approach:** Treat "may/might/possibly" as non-propositional.

</details>

---

**Q5.** I don't exist.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value: **False** (the fact that someone is saying it proves they exist — Descartes' *cogito*)  
Despite being philosophically interesting, it makes a definite claim with a truth value.

</details>

---

**Q6.** Grass is green.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value: **True**  
Straightforward declarative statement.

</details>

---

**Q7.** Everything is a plant or an animal.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value: **False** (rocks, water, air are neither)  
It makes a universal claim that is factually incorrect, but it has a definite truth value.

</details>

---

**Q8.** My name is Amit.

<details>
<summary>Answer</summary>

**P — Proposition** (context-dependent)  
If "my" refers to a known, specific person, it has a truth value.  
If the speaker is identified, this is a proposition (true or false depending on their actual name).  
This is different from "He is tall" because "my" at least refers to the speaker consistently.

</details>

---

**Q9.** This board is white.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value: **True** (the whiteboard in the lecture is white)  
"This board" refers to a specific, identifiable object.

</details>

---

**Q10.** This is a book.

<details>
<summary>Answer</summary>

**P — Proposition**  
Truth value depends on what "this" refers to — but in a given context (pointing to something), it has a definite truth value.  
GATE usually accepts context-dependent statements as propositions if the reference is clear.

</details>

---

**Bonus Q11.** "This statement is false."

<details>
<summary>Answer</summary>

**NP — Not a Proposition**  
This is the **Liar Paradox**.  
Assuming it's true leads to a contradiction. Assuming it's false also leads to a contradiction.  
It violates the fundamental requirement that a proposition must have exactly one truth value.

</details>

---

**Bonus Q12.** x² ≥ 0

<details>
<summary>Answer</summary>

**NP — Not a Proposition** (as a raw statement)  
x is a free variable — truth value is undefined.  
However, **"For all real x, x² ≥ 0"** IS a proposition (True).  
The addition of a quantifier closes the statement and gives it a definite truth value.

</details>

---

## 9. Common GATE Traps

| Trap | What to remember |
|---|---|
| "He is tall" looks like a proposition | No — pronoun without reference = not a proposition |
| Future statements feel uncertain | Uncertainty ≠ no truth value. "Will rain" is a proposition. "May rain" is not. |
| Math equations with variables | Open statements are predicates, not propositions |
| "This is true/false" sentences | Self-referential → automatically not a proposition |
| Philosophical oddities like "I don't exist" | Still a proposition — it has a truth value (False) |

---

## 10. What's Next

**Next lecture:** Logical Connectives — AND (∧), OR (∨), NOT (¬), Implication (→), Biconditional (↔)  
These are used to **combine** propositions into compound propositions (like Q2 above).

---
