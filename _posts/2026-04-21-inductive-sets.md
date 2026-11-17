---
layout: distill
title: Inductive Sets and Natural Numbers
description: Natural Numbers, Inductive Proofs and Indexing
tags: mathematics education
giscus_comments: false
date: 2026-04-21
featured: true

authors:
  - name: Sangeet. S
    url: "https://songofphysics.github.io/bio/"
    affiliations:
      name: Rishi Valley School

bibliography: inductive-sets.bib

toc:
  - name: Inductive Sets
  - name: Finite Indexing

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

Up until this point, we have been dodging a very important problem. We started this series with sets because they are allegedly among the most fundamental entities in mathematics. Yet we all start learning mathematics by counting. So shouldn't numbers indisputably be the most fundamental thing?

We dug ourselves further into this hole with the [axiom of foundation](/blog/2026/sets-and-axioms/#def-2-4), which demands that every non-empty set have an element disjoint from it. That leads to a very strange observation. For the axioms to make sense, every element of a set must itself be a set, otherwise "disjoint" means nothing. And yet in the [last post](/blog/2026/operations-on-sets/) we happily took unions and intersections of sets of _numbers_. So, are numbers themselves sets? To answer that, we first need to look at something broader.

---

## Inductive Sets

Every set we build from the axioms starts from somewhere, and the only set the axioms hand us for free is $\varnothing$. Here is a way to keep growing new sets out of old ones. For any set $n$, define its **successor** to be

$$
S(n) := n \cup \lbrace n \rbrace,
$$

the set $n$ with $n$ itself thrown in as one extra element. The [axiom of pairing](/blog/2026/sets-and-axioms/#def-2-4) (applied to $n$ with itself) gives us $\lbrace n \rbrace$, and the [axiom of union](/blog/2026/sets-and-axioms/#def-2-4) then gives us $n \cup \lbrace n \rbrace$, so $S(n)$ is always a set.

<div class="box-definition" markdown="1" id="def-2-12">

**Definition 2.12.** A set $I$ is called an **inductive set** if and only if $\varnothing \in I$ and $\forall n \in I : S(n) \in I$.

</div>

In plain English: an inductive set contains the empty set, and whenever it contains something, it also contains that thing's successor.

<span id="rem-2-6"></span>**Remark 2.6.** This definition is what makes the [axiom of infinity](/blog/2026/sets-and-axioms/#def-2-4) precise. Stated properly, the axiom says: _there exists an inductive set_. Such a set really must be infinite, since starting from $\varnothing$, the successor lets us add new elements to it ad infinitum.

So what is inside an inductive set? Let us start from $\varnothing$ and keep taking successors, giving each new set a rather suggestive name:<d-footnote>This is the construction due to John von Neumann. There are other constructions of the naturals from sets, which give slightly different interpretations.</d-footnote>

$$
\begin{aligned}
0 &:= \varnothing, \\
1 &:= S(0) = \varnothing \cup \lbrace 0 \rbrace = \lbrace 0 \rbrace, \\
2 &:= S(1) = 1 \cup \lbrace 1 \rbrace = \lbrace 0, 1 \rbrace, \\
3 &:= S(2) = 2 \cup \lbrace 2 \rbrace = \lbrace 0, 1, 2 \rbrace, \\
&\;\;\vdots \\
k + 1 &:= S(k) = k \cup \lbrace k \rbrace = \lbrace 0, 1, 2, \dots, k \rbrace.
\end{aligned}
$$

These are the **finite ordinals**, and every inductive set contains all of them. The natural numbers should be exactly these sets and nothing else. The cleanest way to say "nothing else" is to keep only what _every_ inductive set is forced to contain.

<div class="box-definition" markdown="1" id="def-2-13">

**Definition 2.13.** Let $I_0$ be an inductive set. The set of **natural numbers** is

$$
\mathbb{N} := \lbrace x \in I_0 : x \in I \text{ for every inductive set } I \rbrace.
$$

</div>

The axiom of infinity guarantees that some inductive set $I_0$ exists, and the [axiom of specification](/blog/2026/sets-and-axioms/#def-2-4) then makes $\mathbb{N}$ a set. Notice that we only carve $\mathbb{N}$ out of $I_0$. We never write "the set of all $x$ that are in every inductive set" without saying where the $x$ come from, because that is exactly the habit that got us into [Russell's paradox](/blog/2026/sets-and-axioms/#thm-2-2).

<div class="box-theorem" markdown="1" id="thm-2-9">

**Theorem 2.9.** The set $\mathbb{N}$ is an inductive set, and it is a subset of every inductive set. It does not depend on which inductive set $I_0$ we started from.

</div>

{% details Proof %}
_$\mathbb{N}$ is a subset of every inductive set._ Let $I$ be any inductive set and let $x \in \mathbb{N}$. By [Definition 2.13](#def-2-13), $x$ belongs to every inductive set, in particular to $I$. So $\mathbb{N} \subseteq I$.

_$\mathbb{N}$ is inductive._ Every inductive set contains $\varnothing$, and $I_0$ is one of them, so $\varnothing \in I_0$ and $\varnothing \in \mathbb{N}$. Now let $n \in \mathbb{N}$. Then $n \in I$ for every inductive set $I$, and since each such $I$ is inductive, $S(n) \in I$ for every inductive set $I$. In particular $S(n) \in I_0$, so $S(n) \in \mathbb{N}$.

_Independence of $I_0$._ Let $I_0'$ be another inductive set and $\mathbb{N}'$ the set obtained from it. By the first part (applied to $\mathbb{N}$), $\mathbb{N} \subseteq I_0'$, and every element of $\mathbb{N}$ is in every inductive set, so $\mathbb{N} \subseteq \mathbb{N}'$. Swapping the roles of $I_0$ and $I_0'$ gives $\mathbb{N}' \subseteq \mathbb{N}$. By antisymmetry ([Theorem 2.8](/blog/2026/operations-on-sets/#thm-2-8)), $\mathbb{N} = \mathbb{N}'$. $\square$
{% enddetails %}

In other words, $\mathbb{N}$ is the _smallest_ inductive set, and its elements are precisely $0, 1, 2, 3, \dots$ from the construction above.

<span id="rem-2-7"></span>**Remark 2.7.** Before we go any further, let us take a step back and appreciate the philosophical wisdom of the distant past, in which the number zero was always associated with emptiness, void and nothingness. Modern mathematics, in all its glory, gives that idea a precise logical form: $0$ is nothing but a name, or label, for the empty set.<d-footnote>Roughly speaking, starting from $0 = \varnothing$ also makes the construction more natural than starting from the set containing the empty set, i.e., $1$.</d-footnote>

This also settles the puzzle about the axiom of foundation from [Remark 2.1](/blog/2026/sets-and-axioms/#rem-2-1). Take $\lbrace 1, 2, 3 \rbrace$. Its element $1 = \lbrace 0 \rbrace$, and $0 \notin \lbrace 1, 2, 3 \rbrace$, so $1 \cap \lbrace 1, 2, 3 \rbrace = \varnothing$. The number $1$ is literally a set disjoint from $\lbrace 1, 2, 3 \rbrace$, exactly as foundation demands.

While we have defined the natural numbers as a set, we have also quietly used a symbol, $+$, which is not native to the language of sets. Let us formalise it.

<div class="box-definition" markdown="1" id="def-2-14">

**Definition 2.14.** For any $m, n \in \mathbb{N}$, the **sum** $m + n$ is the set obtained by applying the successor $n$ times, starting from $m$:<d-footnote>Making "apply $S$ exactly $n$ times" fully rigorous needs a result called the <em>recursion theorem</em>. The equivalent recursive form, $m + 0 = m$ and $m + S(n) = S(m + n)$, appears in the exercises at the end of this chapter.</d-footnote>

$$
m + n := S^n(m), \qquad \text{where } S^0(m) := m \text{ and } S^{k+1}(m) := S\big(S^k(m)\big).
$$

</div>

<span id="rem-2-8"></span>**Remark 2.8.** In essence, adding $n \in \mathbb{N}$ to $m \in \mathbb{N}$ boils down to starting at $m$ and taking the successor as many times as there are elements in $n$.<d-footnote>Other valid constructions could have other interpretations, but at the end of the day they would still be built out of sets.</d-footnote> In particular $n + 1 = S(n)$, which is why we were allowed to write $k + 1$ in the construction above.

<span id="ex-2-5"></span>**Exercise 2.5.** Show that for any $m, n \in \mathbb{N}$, $m + n = n + m$.

{% details Solution %}
We use the principle of mathematical induction, [Theorem 2.10](#thm-2-10) below, several times. Straight from [Definition 2.14](#def-2-14), for all $m, n \in \mathbb{N}$,

$$
m + 0 = m \qquad \text{and} \qquad m + S(n) = S^{n+1}(m) = S\big(S^n(m)\big) = S(m + n). \tag{$\ast$}
$$

_Step 1: $0 + m = m$ for all $m \in \mathbb{N}$._ Induction on $m$. Base case: $0 + 0 = 0$ by $(\ast)$. Inductive step: if $0 + k = k$, then $0 + S(k) = S(0 + k) = S(k)$ by $(\ast)$.

_Step 2: $S(m) + n = S(m + n)$ for all $m, n \in \mathbb{N}$._ Fix $m$ and use induction on $n$. Base case: $S(m) + 0 = S(m) = S(m + 0)$ by $(\ast)$. Inductive step: if $S(m) + k = S(m + k)$, then

$$
S(m) + S(k) = S\big(S(m) + k\big) = S\big(S(m + k)\big) = S\big(m + S(k)\big),
$$

using $(\ast)$, the hypothesis, and $(\ast)$ again.

_Step 3: $m + n = n + m$._ Fix $m$ and use induction on $n$. Base case: $m + 0 = m = 0 + m$, by $(\ast)$ and Step 1. Inductive step: if $m + k = k + m$, then

$$
m + S(k) = S(m + k) = S(k + m) = S(k) + m,
$$

using $(\ast)$, the hypothesis, and Step 2. By induction, $m + n = n + m$ for all $n$, and since $m$ was arbitrary, for all $m$ too. $\square$
{% enddetails %}

<div class="box-definition" markdown="1" id="def-2-15">

**Definition 2.15.** The **cardinality** or **cardinal number** of a set $A$ is the number of elements in it, and is denoted by $\lvert A \rvert$.

</div>

<span id="rem-2-9"></span>**Remark 2.9.** Look closely at the construction of $\mathbb{N}$, and you will notice that these numbers play a dual role. First, they answer the question _which count?_ (their **ordinal** role). For example, $3 = \lbrace 0, 1, 2 \rbrace$ is the third non-empty set in our construction. Second, they tell us _how many elements_ are in the set (their **cardinal** role), since the set $3$ contains exactly $3$ elements, i.e., $\lvert 3 \rvert = 3$. Pick any natural number from our construction and you will find that the count and the size match perfectly.

<div class="box-definition" markdown="1" id="def-2-16">

**Definition 2.16.** For any $m, n \in \mathbb{N}$, we say that $m$ **is less than** $n$, written $m \lt n$, whenever $m \subset n$. Equivalently, $n$ **is greater than** $m$, written $n \gt m$, when $n \supset m$.

</div>

So $2 \lt 3$ because $\lbrace 0, 1 \rbrace \subset \lbrace 0, 1, 2 \rbrace$. Ordering numbers turns out to be nothing more than proper inclusion of sets.

<span id="ex-2-6"></span>**Exercise 2.6.** Show that if $a, b, c \in \mathbb{N}$ are such that $a \gt b$ and $b \gt c$, then $a \gt c$.

{% details Solution %}
By [Definition 2.16](#def-2-16), we have $c \subset b$ and $b \subset a$, and we must show $c \subset a$, i.e., $c \subseteq a$ and $c \neq a$.

_$c \subseteq a$._ Since $c \subseteq b$ and $b \subseteq a$, transitivity ([Theorem 2.8](/blog/2026/operations-on-sets/#thm-2-8)) gives $c \subseteq a$.

_$c \neq a$._ Since $c \subset b$, we have $c \neq b$, so by [Exercise 2.1](/blog/2026/sets-and-axioms/#ex-2-1) $b \not\subseteq c$ (otherwise $c \subseteq b$ and $b \subseteq c$ would force $c = b$). So there is some $x \in b$ with $x \notin c$. Since $b \subseteq a$, $x \in a$. Thus $x \in a$ but $x \notin c$, so $a \neq c$ by the [axiom of extension](/blog/2026/sets-and-axioms/#def-2-4).

Hence $c \subset a$, i.e., $a \gt c$. $\square$
{% enddetails %}

<span id="rem-2-10"></span>**Remark 2.10.** To add to [Remark 2.9](#rem-2-9): if we try to stretch these finite sets to infinity, the dual role breaks down. We can talk about the size of an infinite set using infinite cardinal numbers, like $\lvert \mathbb{N} \rvert$,<d-footnote>We will revisit the notion of infinity when we study functions.</d-footnote> but we cannot use our finite counting numbers to reach some unique "infinity-th" position. What we can do is label the position reached by the set $\mathbb{N}$ itself as the **first infinite ordinal**, $\omega := \mathbb{N}$. Its successor $\omega + 1 := S(\omega) = \omega \cup \lbrace \omega \rbrace$ is a perfectly good set, and if we extend [Definition 2.16](#def-2-16) to such sets, $\omega \subset \omega + 1$, so $\omega + 1 \gt \omega$. On the other hand, adding one element to an infinite set intuitively still leaves a set of the same infinite size, so $\lvert \omega + 1 \rvert = \lvert \mathbb{N} \rvert$. This is the crux of the poorly phrased idea that "infinity is not a number but a concept". The fact of the matter is that _count_ and _size_ behave very differently once the size is infinite!

Now for the reason anyone outside set theory cares about any of this.

<div class="box-theorem" markdown="1" id="thm-2-10">

**Theorem 2.10 (Principle of Mathematical Induction).** Let $P(n)$ be a predicate on $\mathbb{N}$ such that

- **(Base case)** $P(0)$ is true, and
- **(Inductive step)** $\forall k \in \mathbb{N} : P(k) \implies P(k + 1)$.

Then $\forall n \in \mathbb{N} : P(n)$ is true.

</div>

{% details Proof %}
By the axiom of specification, $A := \lbrace x \in \mathbb{N} : P(x) \rbrace$ is a set, and $A \subseteq \mathbb{N}$. We show that $A$ is inductive.

By the base case, $P(0)$ holds, and $0 = \varnothing \in \mathbb{N}$, so $\varnothing \in A$. Now let $k \in A$. Then $k \in \mathbb{N}$ and $P(k)$ holds. Since $\mathbb{N}$ is inductive ([Theorem 2.9](#thm-2-9)), $S(k) = k + 1 \in \mathbb{N}$, and by the inductive step $P(k + 1)$ holds. So $S(k) \in A$, and $A$ is inductive.

By [Theorem 2.9](#thm-2-9), $\mathbb{N}$ is a subset of every inductive set, so $\mathbb{N} \subseteq A$. Together with $A \subseteq \mathbb{N}$, antisymmetry ([Theorem 2.8](/blog/2026/operations-on-sets/#thm-2-8)) gives $A = \mathbb{N}$. That is, $P(n)$ holds for every $n \in \mathbb{N}$. $\square$
{% enddetails %}

Think of it as a line of dominoes: knock over the first one, make sure each one knocks over the next, and they all fall. The proof above is the set-theoretic reason the dominoes can't skip any: $\mathbb{N}$ has no elements other than the ones the successor reaches from $0$.

<span id="rem-2-11"></span>**Remark 2.11.** Induction is a really powerful technique for writing proofs about any inductive set, and nothing forces us to start at $0$. It extends to the integers from any starting point onwards.<d-footnote>We will see more general versions of this when we study functions.</d-footnote>

<div class="box-theorem" markdown="1" id="thm-2-11">

**Theorem 2.11.** Let $m \in \mathbb{Z}$, and let $P(n)$ be a predicate on the integers $n \geq m$ such that $P(m)$ is true and $P(k) \implies P(k + 1)$ for every integer $k \geq m$. Then $P(n)$ is true for every integer $n \geq m$.

</div>

{% details Proof %}
For $j \in \mathbb{N}$, define the predicate $Q(j) :\iff P(m + j)$. We check the two conditions of [Theorem 2.10](#thm-2-10) for $Q$.

_Base case._ $Q(0) \iff P(m)$, which is true.

_Inductive step._ Let $j \in \mathbb{N}$ with $Q(j)$ true, i.e., $P(m + j)$ is true. Since $j \geq 0$, the integer $k := m + j$ satisfies $k \geq m$, so $P(k) \implies P(k + 1)$ applies and $P(m + j + 1)$ is true. That is exactly $Q(j + 1)$.

By [Theorem 2.10](#thm-2-10), $Q(j)$ is true for every $j \in \mathbb{N}$. Now let $n \geq m$ be any integer. Then $j := n - m \geq 0$ is a natural number, and $Q(n - m) \iff P(n)$, so $P(n)$ is true. $\square$
{% enddetails %}

Here is induction in action.

<span id="eg-2-17"></span>**Example 2.17.** Prove that $\forall n \in \mathbb{N} : P(n)$, where $P(n) :\iff 3 \mid (n^3 + 2n)$.

{% details Proof %}
We use [Theorem 2.10](#thm-2-10).

**Base case.** $P(0) :\iff 3 \mid 0$, which is true, since $0 = 3 \cdot 0$.

**Inductive step.** Let $k \in \mathbb{N}$ be such that $P(k)$ is true, i.e., $3 \mid (k^3 + 2k)$. We need to show that $3 \mid \big((k + 1)^3 + 2(k + 1)\big)$. Expanding,

$$
(k + 1)^3 + 2(k + 1) = k^3 + 3k^2 + 3k + 1 + 2k + 2 = (k^3 + 2k) + 3(k^2 + k + 1).
$$

The first bracket is divisible by $3$ by the hypothesis $P(k)$, and the second term is visibly a multiple of $3$. So their sum is divisible by $3$, and $P(k + 1)$ is true.

Since our choice of $k$ was arbitrary, $\forall k \in \mathbb{N} : P(k) \implies P(k + 1)$. Therefore, by induction, $\forall n \in \mathbb{N} : P(n)$ is true. $\square$
{% enddetails %}

Notice where the hypothesis did its job: we rearranged $P(k + 1)$ until $P(k)$ appeared inside it. That is the whole trick, nearly every time.

<span id="ex-2-7"></span>**Exercise 2.7.** Show that $9^n - 1$ is divisible by $8$ for all natural numbers $n$.

{% details Solution %}
Let $P(n) :\iff 8 \mid (9^n - 1)$. We use [Theorem 2.10](#thm-2-10).

**Base case.** $9^0 - 1 = 0 = 8 \cdot 0$, so $P(0)$ is true.

**Inductive step.** Let $k \in \mathbb{N}$ with $P(k)$ true, so $9^k - 1 = 8q$ for some integer $q$. Then

$$
9^{k+1} - 1 = 9 \cdot 9^k - 1 = 9(9^k - 1) + 9 - 1 = 9 \cdot 8q + 8 = 8(9q + 1),
$$

so $8 \mid (9^{k+1} - 1)$ and $P(k + 1)$ is true. By induction, $8 \mid (9^n - 1)$ for every $n \in \mathbb{N}$. $\square$
{% enddetails %}

A running theme from here on will be to construct newer sets of numbers out of the ones we already have, moving up from the naturals to the integers, and all the way up to the real and complex numbers. That needs more sophisticated machinery, so it will be rather slow going, and we will also have to rebuild arithmetic on each new set as we go. In the meantime, we will keep using these numbers in soft examples, wherever the intuition from middle school can be readily applied.

---

## Finite Indexing

It will be convenient to introduce the notion of indexing, as it lets us write various operations far more compactly.

<div class="box-definition" markdown="1" id="def-2-17">

**Definition 2.17 (Arbitrary Unions and Intersections).** The **union** of all $x \in S$ is written

$$
\bigcup_{x \in S} x.
$$

Similarly, for non-empty $S$,<d-footnote>The intersection over an empty $S$ would have to contain everything, and we have already seen that there is no set of everything.</d-footnote> the **intersection** of all $x \in S$ is written

$$
\bigcap_{x \in S} x.
$$

</div>

The union is a set by the [axiom of union](/blog/2026/sets-and-axioms/#def-2-4). The intersection is a set by the [axiom of specification](/blog/2026/sets-and-axioms/#def-2-4): pick any $y \in S$ and keep those elements of $y$ that lie in every $x \in S$.

<span id="eg-2-18"></span>**Example 2.18.** Let $S = \lbrace \lbrace 1, 2 \rbrace, \lbrace 4, 3, 2 \rbrace, \lbrace 5, 2 \rbrace \rbrace$. Then

$$
\bigcup_{x \in S} x = \lbrace 1, 2 \rbrace \cup \lbrace 4, 3, 2 \rbrace \cup \lbrace 5, 2 \rbrace = \lbrace 1, 2, 3, 4, 5 \rbrace
\quad \text{and} \quad
\bigcap_{x \in S} x = \lbrace 1, 2 \rbrace \cap \lbrace 4, 3, 2 \rbrace \cap \lbrace 5, 2 \rbrace = \lbrace 2 \rbrace.
$$

When $S$ is a finite set, we can express the same things in terms of an _index set_.

<div class="box-definition" markdown="1" id="def-2-18">

**Definition 2.18 (Index Set).** For a finite set $S$ and some $n \in \mathbb{Z}$, the set

$$
I_n := \lbrace k \in \mathbb{Z} : n \leq k \leq n + \lvert S \rvert - 1 \rbrace
$$

is called a **finite index set** for $S$. If $S$ is a set of sets whose elements are labelled $x_k$ with $k \in I_n$, then

$$
\bigcup_{k \in I_n} x_k = \bigcup_{k = n}^{m} x_k = x_n \cup x_{n+1} \cup x_{n+2} \cup \dots \cup x_m, \qquad \text{where } m = n + \lvert S \rvert - 1.
$$

</div>

<span id="rem-2-12"></span>**Remark 2.12.** Intuitively, the index set $I_n$ just lets us put labels on the sets in $S$ and operate on them. How we do the labelling does not matter, since for finite unions and intersections the order of operations is itself irrelevant (thanks to commutativity and associativity, [Theorem 2.5](/blog/2026/operations-on-sets/#thm-2-5)). It is quite common to choose $I_n$ with $n = 0$ or $n = 1$.

Finite indexing is particularly useful for writing sums as well. There we use the symbol $\Sigma$ instead of $\bigcup$ to denote addition, and the objects being combined are numbers instead of sets.

<div class="box-definition" markdown="1" id="def-2-19">

**Definition 2.19 (Summation).** For a finite set $S \subset \mathbb{R}$, the **sum** of all $x \in S$ is written

$$
\sum_{x \in S} x.
$$

</div>

<span id="eg-2-19"></span>**Example 2.19.** Let $S = \lbrace -1.7, \pi, 5, -3 \rbrace$. Then

$$
\sum_{x \in S} x = (-1.7) + \pi + 5 + (-3) = \pi + 0.3.
$$

<span id="eg-2-20"></span>**Example 2.20.** With the elements of $S$ labelled $x_k$ for $k \in I_n$,

$$
\sum_{k \in I_n} x_k = \sum_{k = n}^{m} x_k = x_n + x_{n+1} + x_{n+2} + \dots + x_m, \qquad \text{where } m = n + \lvert S \rvert - 1.
$$

<span id="rem-2-13"></span>**Remark 2.13.** **Summation** over an index set can be extended to infinite sets under some conditions as well, but we will save that discussion for when we are able to state those conditions.

When $S = I_n$ for some $n$, we tend to choose that very index set for convenience, and we can then replace the **summand** $x_k$ by $k$ itself, since every $x_k \in S$ is identical to some $k \in I_n$.

<span id="eg-2-21"></span>**Example 2.21.** The sum of the first $n$ positive integers is

$$
\sum_{k \in I_1} k = \sum_{k = 1}^{n} k = 1 + 2 + \dots + n.
$$

<span id="ex-2-8"></span>**Exercise 2.8.** Express the sum of the squares of the first $5$ naturals as a summation.

{% details Solution %}
Remember our convention that $0 \in \mathbb{N}$. The first $5$ naturals are $0, 1, 2, 3, 4$, which form the index set $I_0 = \lbrace 0, 1, 2, 3, 4 \rbrace$. So the sum is

$$
\sum_{k \in I_0} k^2 = \sum_{k = 0}^{4} k^2 = 0 + 1 + 4 + 9 + 16 = 30.
$$

If you instead wrote $\sum_{k=1}^{5} k^2 = 55$, you summed the squares of the first $5$ _positive_ integers, i.e., the first $5$ elements of $\mathbb{N}^{\ast}$. That is a perfectly good sum, just not the one asked for. Conventions matter!
{% enddetails %}

<span id="rem-2-14"></span>**Remark 2.14.** An alternative notation for $I_n$ is $[n ; N]$, where $N = n + \lvert S \rvert - 1$ is the last index. In particular, writing $N = \lvert S \rvert$, we denote $I_1 = [1 ; N]$ by $[N]$ and $I_0 = [0 ; N - 1]$ by $[N_{\ast}]$.

---

So we can now count, add, compare and sum, all built out of nothing but the empty set. But mathematics is not just a line of numbers. To talk about the plane, coordinates and shapes, we need a way to _pair things up_, and nothing we have built so far does that. [Next time](/blog/2026/products-of-sets/), we fix that.
