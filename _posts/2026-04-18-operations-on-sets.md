---
layout: distill
title: Operations on Sets
description: What can we do with sets and how do the axioms help?
tags: mathematics education
giscus_comments: false
date: 2026-04-18
featured: true

authors:
  - name: Sangeet. S
    url: "https://songofphysics.github.io/bio/"
    affiliations:
      name: Rishi Valley School

bibliography: operations-on-sets.bib

toc:
  - name: Operations on Sets

_styles: >
  .box-definition, .box-theorem {
    padding: 0.8rem 1rem;
    margin: 1.5rem 0;
    border-left: 3px solid;
    border-radius: 0 4px 4px 0;
  }
  .box-definition {
    border-left-color: #1ca9e8;
    background: rgba(28, 169, 232, 0.10);
  }
  .box-theorem {
    border-left-color: #fdbc42;
    background: rgba(253, 188, 66, 0.12);
  }
  .box-lemma {
    padding: 0.2rem 1rem;
    margin: 1.5rem 0;
    border-left: 3px solid #e53935;
  }
  [id] {
    scroll-margin-top: 4rem;
  }
  .box-definition > p:last-child,
  .box-theorem > p:last-child,
  .box-lemma > p:last-child {
    margin-bottom: 0;
  }
---

In the [previous post](/blog/2026/sets-and-axioms/) we worked out what sets are, how to compare them, and which axioms stop them from swallowing themselves whole. All very respectable, and all a bit static. A set that just sits there is about as useful as a number we are not allowed to add. So in this post we start _doing_ things with sets: combining them, cutting them down and flipping them inside out.

Two things come out of this. First, sets turn out to have an algebra of their own, with rules that look suspiciously like the ones we know from numbers and from logic. Second, the axioms finally start paying their way. The strange-looking [axiom of foundation](/blog/2026/sets-and-axioms/#def-2-4), in particular, will rule out some genuinely weird objects.

---

## Operations on Sets

First, a small notational convenience. From here on, whenever we write $\lbrace x : P(x) \rbrace$, we mean $\lbrace x \in U : P(x) \rbrace$, where $U$ is some universal set for the set $S$ of sets we are working with ([Definition 2.6](/blog/2026/sets-and-axioms/#def-2-6)). This is not pedantry. Without the hidden "$\in U$", the notation $\lbrace x : P(x) \rbrace$ would be exactly the kind of unrestricted collection that landed us in Russell's paradox.

<div class="box-definition" markdown="1" id="def-2-7">

**Definition 2.7.** For any two sets $A, B \in S$, their **union**<d-footnote>The set containing every individual element of $A$ and of $B$.</d-footnote> $A \cup B$ is given by

$$
A \cup B := \lbrace x : (x \in A) \lor (x \in B) \rbrace.
$$

</div>

<div class="box-definition" markdown="1" id="def-2-8">

**Definition 2.8.** For any two sets $A, B \in S$, their **intersection**<d-footnote>The set containing every element that $A$ and $B$ have in common.</d-footnote> $A \cap B$ is given by

$$
A \cap B := \lbrace x : (x \in A) \land (x \in B) \rbrace.
$$

</div>

Notice the pattern: union is built from "or" ($\lor$), intersection from "and" ($\land$). Keep that in mind, because it is the key to almost everything in this post.

<span id="eg-2-10"></span>**Example 2.10.** If $A = \lbrace 1, 2, 3 \rbrace$ and $B = \lbrace 3, 4, 5 \rbrace$, then $A \cup B = \lbrace 1, 2, 3, 4, 5 \rbrace$ and $A \cap B = \lbrace 3 \rbrace$.

<span id="eg-2-11"></span>**Example 2.11.** Let $A = \lbrace n \in \mathbb{N} : 2 \mid n \rbrace$ and $B = \lbrace n \in \mathbb{N} : 4 \mid n \rbrace$. Then

$$
A \cup B = \lbrace n \in \mathbb{N} : (2 \mid n) \lor (4 \mid n) \rbrace = \lbrace n \in \mathbb{N} : 2 \mid n \rbrace = A,
$$

since every multiple of $4$ is already a multiple of $2$. Similarly, $A \cap B = B$.

<div class="box-definition" markdown="1" id="def-2-9">

**Definition 2.9.** For any set $A \in S$, its **complement**<d-footnote>The set of all elements of the universal set that are not in $A$.</d-footnote> $\overline{A}$ is given by

$$
\overline{A} := \lbrace x : x \notin A \rbrace.
$$

</div>

And complement is built from "not" ($\neg$). Because of our notational convenience, the complement always means "not in $A$, _but still in $U$_". Change the universal set and you change the complement, which brings us to a classic blunder.

<span id="eg-2-12"></span>**Example 2.12.** The complement of the set of rational numbers in $\mathbb{R}$, i.e.,<d-footnote>Most sad excuses for a textbook claim that any number that is not rational is irrational. That is only true when the universal set is $\mathbb{R}$. Quite pathetic, considering most of these textbooks also cover complex numbers.</d-footnote> of

$$
\mathbb{Q} = \lbrace x \in \mathbb{R} : (x = pq^{-1}) \land (p, q \in \mathbb{Z}) \land (q \neq 0) \rbrace,
$$

is the set of irrational numbers $\overline{\mathbb{Q}}$.

<span id="eg-2-13"></span>**Example 2.13.** The complement of the set of even integers in $\mathbb{Z}$, i.e., of $2\mathbb{Z} = \lbrace n \in \mathbb{Z} : 2 \mid n \rbrace$, is the set of odd integers $2\mathbb{Z} + 1 = \lbrace n \in \mathbb{Z} : 2 \nmid n \rbrace$.

<span id="ex-2-4"></span>**Exercise 2.4.** Construct three examples each of unions, intersections and complements in $\mathbb{Z}$.

{% details Solution %}
Throughout, the universal set is $\mathbb{Z}$, and for any $k \in \mathbb{Z}$ we write $k\mathbb{Z} := \lbrace n \in \mathbb{Z} : k \mid n \rbrace$ for the multiples of $k$. Many other answers are equally valid.

_Unions._

1. $\lbrace 1, 2 \rbrace \cup \lbrace 2, 3 \rbrace = \lbrace 1, 2, 3 \rbrace$. Note that $2$ appears once, since a set's elements are distinct.
2. $2\mathbb{Z} \cup (2\mathbb{Z} + 1) = \mathbb{Z}$. Every integer leaves remainder $0$ or $1$ on division by $2$, so every integer is in one of the two sets, and both sets are subsets of $\mathbb{Z}$.
3. $3\mathbb{Z} \cup 6\mathbb{Z} = 3\mathbb{Z}$. If $6 \mid n$, say $n = 6m$, then $n = 3(2m)$, so $3 \mid n$. Hence every element of $6\mathbb{Z}$ is already in $3\mathbb{Z}$, and the union adds nothing new.

_Intersections._

1. $2\mathbb{Z} \cap (2\mathbb{Z} + 1) = \varnothing$. No integer is both even and odd.
2. $\lbrace n \in \mathbb{Z} : n \ge 0 \rbrace \cap \lbrace n \in \mathbb{Z} : n \le 0 \rbrace = \lbrace 0 \rbrace$, since $n \ge 0$ and $n \le 0$ together force $n = 0$.
3. $2\mathbb{Z} \cap 3\mathbb{Z} = 6\mathbb{Z}$. If $6 \mid n$, then $n = 6m = 2(3m) = 3(2m)$, so $n$ is in both sets. Conversely, suppose $2 \mid n$ and $3 \mid n$. Write $n = 2m$. Since $3$ is prime and $3 \mid 2m$, either $3 \mid 2$ or $3 \mid m$. The first is false, so $m = 3k$ for some integer $k$, and $n = 6k$. Both inclusions hold, so the sets are equal by [Exercise 2.1](/blog/2026/sets-and-axioms/#ex-2-1).

_Complements in $\mathbb{Z}$._

1. $\overline{\mathbb{N}} = \lbrace n \in \mathbb{Z} : n \lt 0 \rbrace$, the strictly negative integers, since $\mathbb{N} = \lbrace 0, 1, 2, \dots \rbrace$.
2. $\overline{\lbrace 0 \rbrace} = \lbrace n \in \mathbb{Z} : n \neq 0 \rbrace$, the non-zero integers.
3. $\overline{3\mathbb{Z}} = \lbrace n \in \mathbb{Z} : 3 \nmid n \rbrace = (3\mathbb{Z} + 1) \cup (3\mathbb{Z} + 2)$, the integers leaving remainder $1$ or $2$ on division by $3$. Here $3\mathbb{Z} + r := \lbrace 3m + r : m \in \mathbb{Z} \rbrace$.
{% enddetails %}

Now for the algebra. If union is "or", intersection is "and" and complement is "not", then every law of logic should hand us a law of sets. It does.

<div class="box-theorem" markdown="1" id="thm-2-5">

**Theorem 2.5 (Algebraic Properties of Sets).** The following properties hold for **unions**, **intersections** and **complements** of the sets $A, B, C \in S$:

- **(Identity)** $A \cap U = A = A \cup \varnothing$.
- **(Complementarity)** $A \cup \overline{A} = U$ and $A \cap \overline{A} = \varnothing$.
- **(Commutativity)** $A \cup B = B \cup A$ and $A \cap B = B \cap A$.
- **(Associativity)** $(A \cup B) \cup C = A \cup (B \cup C)$ and $(A \cap B) \cap C = A \cap (B \cap C)$.
- **(Distributivity)** $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ and $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$.
- **(Idempotence)** $A \cup A = A = A \cap A$.
- **(Domination)** $A \cup U = U$ and $A \cap \varnothing = \varnothing$.
- **(Absorption)** $A \cup (A \cap B) = A = A \cap (A \cup B)$.
- **(De Morgan)** $\overline{A \cup B} = \overline{A} \cap \overline{B}$ and $\overline{A \cap B} = \overline{A} \cup \overline{B}$.
- **(Involution)** $\overline{\overline{A}} = A$.
- **(Duality)** $\overline{\varnothing} = U$ and $\overline{U} = \varnothing$.

</div>

{% details Proof %}
Every set in the theorem is a subset of the universal set $U$, so by the [axiom of extension](/blog/2026/sets-and-axioms/#def-2-4) it is enough to show that, for each law, an arbitrary $x \in U$ is in the left-hand side if and only if it is in the right-hand side.

Fix $x \in U$, and write $a$, $b$, $c$ for the statements $x \in A$, $x \in B$, $x \in C$. Write $\top$ for a statement that is always true and $\bot$ for one that is always false. By [Definitions 2.7](#def-2-7) to [2.9](#def-2-9), and because $x \in U$,

$$
x \in A \cup B \iff a \lor b, \qquad x \in A \cap B \iff a \land b, \qquad x \in \overline{A} \iff \neg a,
$$

while $x \in U \iff \top$ and $x \in \varnothing \iff \bot$. Applying these rules repeatedly turns "$x$ is in the left-hand side" and "$x$ is in the right-hand side" of each law into statements built from $a$, $b$, $c$, $\top$ and $\bot$. The law holds as soon as those two statements are logically equivalent. The eleven laws become:

- **(Identity)** $a \land \top \equiv a \equiv a \lor \bot$.
- **(Complementarity)** $a \lor \neg a \equiv \top$; $a \land \neg a \equiv \bot$.
- **(Commutativity)** $a \lor b \equiv b \lor a$; $a \land b \equiv b \land a$.
- **(Associativity)** $(a \lor b) \lor c \equiv a \lor (b \lor c)$; $(a \land b) \land c \equiv a \land (b \land c)$.
- **(Distributivity)** $a \lor (b \land c) \equiv (a \lor b) \land (a \lor c)$; $a \land (b \lor c) \equiv (a \land b) \lor (a \land c)$.
- **(Idempotence)** $a \lor a \equiv a \equiv a \land a$.
- **(Domination)** $a \lor \top \equiv \top$; $a \land \bot \equiv \bot$.
- **(Absorption)** $a \lor (a \land b) \equiv a \equiv a \land (a \lor b)$.
- **(De Morgan)** $\neg(a \lor b) \equiv \neg a \land \neg b$; $\neg(a \land b) \equiv \neg a \lor \neg b$.
- **(Involution)** $\neg \neg a \equiv a$.
- **(Duality)** $\neg \bot \equiv \top$; $\neg \top \equiv \bot$.

Each of these is verified by a truth table: list every combination of truth values of the letters involved (two rows for one letter, four for two, eight for three) and check that both sides agree in every row. For instance, the first distributive law:

| $a$ | $b$ | $c$ | $b \land c$ | $a \lor (b \land c)$ | $a \lor b$ | $a \lor c$ | $(a \lor b) \land (a \lor c)$ |
| :-: | :-: | :-: | :---------: | :------------------: | :--------: | :--------: | :---------------------------: |
|  T  |  T  |  T  |      T      |        **T**         |     T      |     T      |             **T**             |
|  T  |  T  |  F  |      F      |        **T**         |     T      |     T      |             **T**             |
|  T  |  F  |  T  |      F      |        **T**         |     T      |     T      |             **T**             |
|  T  |  F  |  F  |      F      |        **T**         |     T      |     T      |             **T**             |
|  F  |  T  |  T  |      T      |        **T**         |     T      |     T      |             **T**             |
|  F  |  T  |  F  |      F      |        **F**         |     T      |     F      |             **F**             |
|  F  |  F  |  T  |      F      |        **F**         |     F      |     T      |             **F**             |
|  F  |  F  |  F  |      F      |        **F**         |     F      |     F      |             **F**             |

The two bold columns agree in all eight rows. The other laws are checked in exactly the same way, and each check is just as mechanical. Since every law reduces to a logical equivalence that holds in every row, $x$ is in the left-hand side exactly when it is in the right-hand side, and each set identity follows by the axiom of extension. $\square$
{% enddetails %}

So far the axioms have been sitting quietly in the background. Time to put one of them to work. We now prove some important results stemming from the [axiom of foundation](/blog/2026/sets-and-axioms/#def-2-4), as promised in the [previous post](/blog/2026/sets-and-axioms/#rem-2-2).

<div class="box-theorem" markdown="1" id="thm-2-6">

**Theorem 2.6.** The following are direct consequences of the axiom of foundation:

- **(i)** There exist no non-empty sets<d-footnote>The empty set has no elements at all, so $\varnothing \in \varnothing$ is false from the start.</d-footnote> which are members of themselves.
- **(ii)** There exist no two sets which form a membership loop.
- **(iii)** There exist no sets which form an infinite descending chain of membership.

</div>

{% details Proof %}
We will prove each case by contradiction.

**Case (i).** Let $A$ be a set with $A \in A$. By the [axiom of pairing](/blog/2026/sets-and-axioms/#def-2-4) applied to $A$ with itself, $X := \lbrace A \rbrace$ is a set. Since $X$ is non-empty, the axiom of foundation says some element of $X$ is disjoint from $X$. The only element of $X$ is $A$, so we must have $A \cap X = \varnothing$. But $A \in A$ and $A \in X$, so $A \in A \cap X$. This is a contradiction.

**Case (ii).** Let $X$ and $Y$ be sets with $X \in Y$ and $Y \in X$. By the axiom of pairing, $A := \lbrace X, Y \rbrace$ is a set. It is non-empty, so by the axiom of foundation either $A \cap X = \varnothing$ or $A \cap Y = \varnothing$. But $Y \in A$ and $Y \in X$, so $Y \in A \cap X$. Likewise $X \in A$ and $X \in Y$, so $X \in A \cap Y$. Neither intersection is empty, which is a contradiction.

**Case (iii).** Let $\dots \in X_{n+1} \in X_n \in \dots \in X_1 \in X_0$ be an infinite descending chain of membership, i.e., $X_{n+1} \in X_n$ for every $n \ge 0$. Consider the set

$$
A := \lbrace X_0, X_1, X_2, \dots \rbrace.
$$

That this collection is a set needs the [axiom of replacement](/blog/2026/sets-and-axioms/#def-2-4), applied to the natural numbers via $n \mapsto X_n$.<d-footnote>We have not built the natural numbers out of sets yet. That happens in the next post, and we are borrowing the result here.</d-footnote> The set $A$ is non-empty, since $X_0 \in A$, so by the axiom of foundation some element $X_n$ of $A$ is disjoint from $A$. But $X_{n+1} \in X_n$ and $X_{n+1} \in A$, so $X_{n+1} \in A \cap X_n$, and $A \cap X_n \neq \varnothing$. This holds for every $n \ge 0$, so no element of $A$ is disjoint from $A$. This contradicts the axiom of foundation.

Thus no such sets exist, and this completes the proof. $\square$
{% enddetails %}

So the axiom that looked so strange last time is precisely what bans sets that contain themselves, pairs of sets that contain each other, and bottomless chains of sets inside sets. Not bad for one line.

Back to operations. There is one more way to combine two sets, and it is the one we use whenever we "remove" things.

<div class="box-definition" markdown="1" id="def-2-10">

**Definition 2.10.** For any two sets $A, B \in S$, their **difference**<d-footnote>Sometimes denoted by $A - B$, and often read as "the set $A$ without the elements of $B$". As a result, it is also called the <strong>relative complement</strong> of $B$ with respect to $A$.</d-footnote> $A \setminus B$ is given by

$$
A \setminus B := \lbrace x : (x \in A) \land (x \notin B) \rbrace.
$$

</div>

<div class="box-definition" markdown="1" id="def-2-11">

**Definition 2.11.** For any two sets $A, B \in S$, their **symmetric difference** is given by

$$
A \,\Delta\, B := (A \setminus B) \cup (B \setminus A).
$$

</div>

In plain English, $A \,\Delta\, B$ is the set of elements that are in exactly one of $A$ and $B$.

<span id="eg-2-14"></span>**Example 2.14.** The subset of the reals $\mathbb{R} \setminus \lbrace 0 \rbrace$ is the set of non-zero real numbers $\mathbb{R}^{\ast}$.

<span id="eg-2-15"></span>**Example 2.15.** The set of integers $\mathbb{Z}$ without the set of natural numbers $\mathbb{N}$, i.e., $\mathbb{Z} \setminus \mathbb{N}$, is the set of strictly negative integers. Here we stick to the convention that<d-footnote>Historically, whether $0 \in \mathbb{N}$ was a hotly debated topic, which gave us nonsensical names like "whole numbers" and what not. In modern mathematics, $0 \in \mathbb{N}$ is the accepted convention, and the older natural numbers are written $\mathbb{N}^{\ast}$.</d-footnote> $0 \in \mathbb{N}$.

<span id="eg-2-16"></span>**Example 2.16.** Let $\mathbb{P} \subset \mathbb{N}$ be the set of primes and $2\mathbb{N}$ the set of even naturals. The only even prime is $2$, so

$$
\mathbb{P} \setminus 2\mathbb{N} = \lbrace 3, 5, 7, 11, 13, \dots \rbrace \quad \text{and} \quad 2\mathbb{N} \setminus \mathbb{P} = \lbrace 0, 4, 6, 8, 10, \dots \rbrace.
$$

Therefore the symmetric difference $\mathbb{P} \,\Delta\, 2\mathbb{N}$ is the set of odd primes together with every even natural number except $2$. Note what is _not_ in it: $1$ and the odd composites such as $9$ and $15$, which are in neither set, and $2$, which is in both.

Differences can be rewritten in terms of what we already have, and that gives us another batch of identities.

<div class="box-theorem" markdown="1" id="thm-2-7">

**Theorem 2.7 (Algebra of Relative Complements).** For any universal set $U$ and subsets $A, B, C \subseteq U$, the following identities hold:

1. $C \setminus (A \cap B) = (C \setminus A) \cup (C \setminus B)$.
2. $C \setminus (A \cup B) = (C \setminus A) \cap (C \setminus B)$.
3. $C \setminus (B \setminus A) = (A \cap C) \cup (C \setminus B)$.
4. $(B \setminus A) \cap C = (B \cap C) \setminus (A \cap C) = (B \cap C) \setminus A = B \cap (C \setminus A)$.
5. $(B \setminus A) \cup C = (B \cup C) \setminus (A \setminus C)$.
6. $(B \setminus A) \setminus C = B \setminus (A \cup C)$.
7. $A \setminus A = \varnothing \setminus A = A \setminus U = \varnothing$.
8. $A \setminus \varnothing = A = U \setminus \overline{A}$.
9. $B \setminus A = \overline{A} \cap B$.
10. $\overline{B \setminus A} = A \cup \overline{B}$.

</div>

{% details Proof %}
We use the method from the proof of [Theorem 2.5](#thm-2-5). Fix $x \in U$ and let $a$, $b$, $c$ stand for $x \in A$, $x \in B$, $x \in C$. By [Definition 2.10](#def-2-10),

$$
x \in B \setminus A \iff b \land \neg a,
$$

and the rules for $\cup$, $\cap$, $\overline{\phantom{A}}$, $U$ and $\varnothing$ are as before. All sets involved are subsets of $U$, so by the axiom of extension each identity follows once the membership conditions of its sides are shown to be logically equivalent. Each step below uses a law from the proof of [Theorem 2.5](#thm-2-5).

1. $c \land \neg(a \land b) \equiv c \land (\neg a \lor \neg b) \equiv (c \land \neg a) \lor (c \land \neg b)$, by De Morgan and then Distributivity. The right-hand side is the condition for $x \in (C \setminus A) \cup (C \setminus B)$.
2. $c \land \neg(a \lor b) \equiv c \land \neg a \land \neg b \equiv (c \land \neg a) \land (c \land \neg b)$, by De Morgan, then Idempotence ($c \equiv c \land c$) with Commutativity and Associativity. This is the condition for $x \in (C \setminus A) \cap (C \setminus B)$.
3. $c \land \neg(b \land \neg a) \equiv c \land (\neg b \lor a) \equiv (c \land \neg b) \lor (a \land c)$, by De Morgan with Involution, then Distributivity and Commutativity. This is the condition for $x \in (A \cap C) \cup (C \setminus B)$.
4. The four sets have the conditions $(b \land \neg a) \land c$, $(b \land c) \land \neg(a \land c)$, $(b \land c) \land \neg a$ and $b \land (c \land \neg a)$. The first, third and fourth are all equivalent to $b \land c \land \neg a$ by Commutativity and Associativity. For the second, De Morgan and Distributivity give $(b \land c) \land (\neg a \lor \neg c) \equiv (b \land c \land \neg a) \lor (b \land c \land \neg c)$. The last term contains $c \land \neg c \equiv \bot$ (Complementarity), so it is $\bot$ by Domination, and Identity leaves $b \land c \land \neg a$.
5. The right-hand side has condition $(b \lor c) \land \neg(a \land \neg c) \equiv (b \lor c) \land (\neg a \lor c)$, by De Morgan and Involution. By Commutativity this is $(c \lor b) \land (c \lor \neg a)$, which Distributivity turns into $c \lor (b \land \neg a)$. That is the condition for $x \in (B \setminus A) \cup C$.
6. $(b \land \neg a) \land \neg c \equiv b \land (\neg a \land \neg c) \equiv b \land \neg(a \lor c)$, by Associativity and then De Morgan. This is the condition for $x \in B \setminus (A \cup C)$.
7. The conditions are $a \land \neg a$, $\bot \land \neg a$ and $a \land \neg \top$. The first is $\bot$ by Complementarity, the second by Commutativity and Domination, and the third because $\neg \top \equiv \bot$ (Duality) and then Domination. Each matches $x \in \varnothing \iff \bot$.
8. $a \land \neg \bot \equiv a \land \top \equiv a$, by Duality and Identity. Also $\top \land \neg\neg a \equiv \top \land a \equiv a$, by Involution, Commutativity and Identity. Both match $x \in A \iff a$.
9. $b \land \neg a \equiv \neg a \land b$, by Commutativity, which is the condition for $x \in \overline{A} \cap B$.
10. $\neg(b \land \neg a) \equiv \neg b \lor \neg\neg a \equiv a \lor \neg b$, by De Morgan, Involution and Commutativity, which is the condition for $x \in A \cup \overline{B}$.

This proves all ten identities. $\square$
{% enddetails %}

Finally, the subset relation itself has an algebra, and it ties everything in this post together.

<div class="box-theorem" markdown="1" id="thm-2-8">

**Theorem 2.8 (Algebra of Inclusion).** If $A, B, C$ are sets, then the following hold:

- **(Reflexivity)** $A \subseteq A$.
- **(Antisymmetry)** $A \subseteq B$ and $B \subseteq A \iff A = B$.
- **(Transitivity)** $A \subseteq B$ and $B \subseteq C \implies A \subseteq C$.

If $A, B, C \subseteq S$, then the following hold:

- **(Min-Max)** $\varnothing \subseteq A \subseteq S$.
- **(Joining)** $A \subseteq A \cup B$, and $A, B \subseteq C \implies A \cup B \subseteq C$.
- **(Meeting)** $A \cap B \subseteq A$, and $A, B \supseteq C \implies A \cap B \supseteq C$.

Furthermore, for any two subsets $A, B$ of a universal set $U$,

$$
A \subseteq B \iff A \cap B = A \iff A \cup B = B \iff A \setminus B = \varnothing \iff \overline{B} \subseteq \overline{A}.
$$

</div>

{% details Proof %}
**Reflexivity** is [Theorem 2.1](/blog/2026/sets-and-axioms/#thm-2-1), and **Antisymmetry** is [Exercise 2.1](/blog/2026/sets-and-axioms/#ex-2-1).

**Transitivity.** Let $x \in A$. Since $A \subseteq B$, $x \in B$, and since $B \subseteq C$, $x \in C$. So $A \subseteq C$.

**Min-Max.** The statement $x \in \varnothing$ is false for every $x$, so $\forall x : (x \in \varnothing \implies x \in A)$ holds (an implication with a false hypothesis is true). Hence $\varnothing \subseteq A$. Also $A \subseteq S$ is given.

**Joining.** If $x \in A$, then $(x \in A) \lor (x \in B)$ is true, so $x \in A \cup B$. For the second part, let $x \in A \cup B$. Then $x \in A$ or $x \in B$. In the first case $x \in C$ because $A \subseteq C$, and in the second case $x \in C$ because $B \subseteq C$. So $A \cup B \subseteq C$.

**Meeting.** If $x \in A \cap B$, then $x \in A$ in particular, so $A \cap B \subseteq A$. For the second part, let $x \in C$. Since $C \subseteq A$ and $C \subseteq B$, we have $x \in A$ and $x \in B$, i.e., $x \in A \cap B$. So $C \subseteq A \cap B$.

**The chain of equivalences.** Let $A, B \subseteq U$. We prove five implications in a cycle, which makes all five statements equivalent.

1. _$A \subseteq B \implies A \cap B = A$._ By Meeting, $A \cap B \subseteq A$. Conversely, if $x \in A$ then $x \in B$ because $A \subseteq B$, so $x \in A \cap B$. Hence $A \subseteq A \cap B$, and Antisymmetry gives $A \cap B = A$.
2. _$A \cap B = A \implies A \cup B = B$._ Substituting, $A \cup B = (A \cap B) \cup B = B \cup (B \cap A)$, by Commutativity ([Theorem 2.5](#thm-2-5)). This is $B$ by Absorption.
3. _$A \cup B = B \implies A \setminus B = \varnothing$._ Suppose $x \in A \setminus B$. Then $x \in A \subseteq A \cup B = B$ (by Joining), so $x \in B$. But $x \notin B$ by the definition of $A \setminus B$, a contradiction. So $A \setminus B$ has no elements, i.e., $A \setminus B = \varnothing$.
4. _$A \setminus B = \varnothing \implies \overline{B} \subseteq \overline{A}$._ Let $x \in \overline{B}$, i.e., $x \in U$ and $x \notin B$. If $x \in A$, then $x \in A \setminus B = \varnothing$, which is impossible. So $x \notin A$, i.e., $x \in \overline{A}$.
5. _$\overline{B} \subseteq \overline{A} \implies A \subseteq B$._ Let $x \in A$, so $x \in U$. If $x \notin B$, then $x \in \overline{B} \subseteq \overline{A}$, so $x \notin A$, a contradiction. So $x \in B$.

This completes the proof. $\square$
{% enddetails %}

---

So sets are good for quite a lot. They come with a full algebra, inherited directly from logic, and the axioms are not just decoration: foundation alone outlaws an entire zoo of pathological sets. But we have been dodging a very important problem this whole time. Every example in sight has been a set of _numbers_, while the axiom of foundation quietly insists that every element of a set is itself a set. So, are numbers themselves sets? That is the question for the [next post](/blog/2026/inductive-sets/).
