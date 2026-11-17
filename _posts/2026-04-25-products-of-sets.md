---
layout: distill
title: Products of Sets
description: The Cartesian Product
tags: mathematics education
giscus_comments: false
date: 2026-04-25
featured: true

authors:
  - name: Sangeet. S
    url: "https://songofphysics.github.io/bio/"
    affiliations:
      name: Rishi Valley School

bibliography: products-of-sets.bib

toc:
  - name: Products of Sets

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

In the [last post](/blog/2026/inductive-sets/) we built the natural numbers out of nothing but the empty set, and learnt to count, add, compare and sum with them. That gives us a very crucial subset of the real numbers, which puts us one step closer to describing the so-called _real line_. Filling in the gaps between the naturals, and extending them past zero, will have to wait for later posts.

But a line is not enough. Eventually we want to describe real _space_, so that we can talk about shapes, coordinates and simple geometry. Nothing we have built so far looks remotely like a coordinate. A set does not care about order, since $\lbrace 1, 2 \rbrace = \lbrace 2, 1 \rbrace$, while the point $(1, 2)$ on a graph is most definitely not the point $(2, 1)$. So let us extend our study of sets to handle order.

---

## Products of Sets

The trick is to smuggle the order into the _structure_ of a set, since we cannot put it in the elements.

<div class="box-definition" markdown="1" id="def-2-20">

**Definition 2.20 (Kuratowski Ordered Pair).** A **(Kuratowski) ordered pair** of the sets $x$ and $y$ is given by

$$
(x, y) := \lbrace \lbrace x \rbrace, \lbrace x, y \rbrace \rbrace.
$$

</div>

<span id="rem-2-15"></span>**Remark 2.15.** There are other, nearly equivalent ways to define ordered pairs,<d-footnote>Famously by the likes of Felix Hausdorff and Norbert Wiener, but their definitions had some annoyances, due to which they are no longer common.</d-footnote> but the reason they are called _ordered_ is especially natural in Kuratowski's version. The set $\lbrace x \rbrace$ sits inside $\lbrace x, y \rbrace$, which tells us that $x$ comes first, much like how we compared natural numbers by inclusion in [Definition 2.16](/blog/2026/inductive-sets/#def-2-16). Once $x$ is fixed as first, $y$ automatically comes after it.

Of course, a definition of "ordered pair" is only any good if it remembers both entries and their order. This one does.

<div class="box-lemma" markdown="1" id="lem-2-12-1">

**Lemma 2.12.1 (Characteristic Property of Ordered Pairs).** For any sets $a, b, c, d$,

$$
(a, b) = (c, d) \iff (a = c) \land (b = d).
$$

</div>

{% details Proof %}
($\impliedby$) If $a = c$ and $b = d$, then $\lbrace \lbrace a \rbrace, \lbrace a, b \rbrace \rbrace$ and $\lbrace \lbrace c \rbrace, \lbrace c, d \rbrace \rbrace$ are built from the same sets in the same way, so they are equal.

($\implies$) Suppose $\lbrace \lbrace a \rbrace, \lbrace a, b \rbrace \rbrace = \lbrace \lbrace c \rbrace, \lbrace c, d \rbrace \rbrace$. We split into two cases.

_Case $a = b$._ Then $(a, b) = \lbrace \lbrace a \rbrace, \lbrace a \rbrace \rbrace = \lbrace \lbrace a \rbrace \rbrace$ has a single element. So both elements of $(c, d)$ must equal $\lbrace a \rbrace$. From $\lbrace c \rbrace = \lbrace a \rbrace$ we get $c = a$, and from $\lbrace c, d \rbrace = \lbrace a \rbrace$ we get $d = a$. Hence $c = a$ and $d = a = b$.

_Case $a \neq b$._ Then $b \notin \lbrace a \rbrace$, so $\lbrace a \rbrace \neq \lbrace a, b \rbrace$, and $(a, b)$ has exactly two elements. So $(c, d)$ must have two elements as well, which forces $c \neq d$ (if $c = d$, then $(c, d) = \lbrace \lbrace c \rbrace \rbrace$ would have only one). Now $\lbrace a \rbrace \in (c, d)$, so either $\lbrace a \rbrace = \lbrace c \rbrace$ or $\lbrace a \rbrace = \lbrace c, d \rbrace$. The second would force $c = a = d$, which is impossible, so $\lbrace a \rbrace = \lbrace c \rbrace$ and $a = c$. Next, $\lbrace a, b \rbrace \in (c, d)$, and $\lbrace a, b \rbrace$ has two elements while $\lbrace c \rbrace$ has one, so $\lbrace a, b \rbrace = \lbrace c, d \rbrace = \lbrace a, d \rbrace$. Then $b \in \lbrace a, d \rbrace$ and $b \neq a$, so $b = d$. $\square$
{% enddetails %}

<span id="ex-2-9"></span>**Exercise 2.9.** Show that if $x$ and $y$ are sets with $x \neq y$, then $(x, y) \neq (y, x)$.

{% details Solution %}
Suppose, for contradiction, that $(x, y) = (y, x)$. By [Lemma 2.12.1](#lem-2-12-1), comparing first entries gives $x = y$, which contradicts $x \neq y$. So $(x, y) \neq (y, x)$. $\square$

The condition $x \neq y$ is genuinely needed: if $x = y$, then $(x, y)$ and $(y, x)$ are literally the same pair.
{% enddetails %}

With pairs in hand, we can pair up everything from one set with everything from another.

<div class="box-definition" markdown="1" id="def-2-21">

**Definition 2.21 (Cartesian Product).** The **product** of two sets $X$ and $Y$ is given by

$$
X \times Y := \lbrace (x, y) : (x \in X) \land (y \in Y) \rbrace.
$$

</div>

<span id="rem-2-16"></span>**Remark 2.16.** Ordered pairs, and hence products, are well-defined by the [axioms of pairing](/blog/2026/sets-and-axioms/#def-2-4), [union](/blog/2026/sets-and-axioms/#def-2-4), [power set](/blog/2026/sets-and-axioms/#def-2-4) and [specification](/blog/2026/sets-and-axioms/#def-2-4). If $x \in X$ and $y \in Y$, then $\lbrace x \rbrace$ and $\lbrace x, y \rbrace$ are subsets of $X \cup Y$, so they are elements of $\mathcal{P}(X \cup Y)$. That makes $(x, y)$ a subset of $\mathcal{P}(X \cup Y)$, i.e.,

$$
(x, y) \in \mathcal{P}^2(X \cup Y),
$$

where $\mathcal{P}^2(S) := \mathcal{P}(\mathcal{P}(S))$. So every pair we want already lives inside the set $\mathcal{P}^2(X \cup Y)$, and $X \times Y$ is carved out of it by specification. In plain English: the product is an honest set, not one of those "collection of everything" monsters.

<span id="eg-2-22"></span>**Example 2.22.** Let $X = \lbrace 1, 2 \rbrace$ and $Y = \lbrace 2, 3, 4 \rbrace$. Then

$$
\begin{aligned}
X \times Y &= \lbrace (1, 2), (1, 3), (1, 4), (2, 2), (2, 3), (2, 4) \rbrace, \\
Y \times X &= \lbrace (2, 1), (2, 2), (3, 1), (3, 2), (4, 1), (4, 2) \rbrace.
\end{aligned}
$$

These are clearly different sets, which raises the question of when swapping the factors makes no difference.

<div class="box-theorem" markdown="1" id="thm-2-12">

**Theorem 2.12.** For any two sets $X$ and $Y$, $X \times Y = Y \times X$ if and only if $X = Y$, or one of $X$ and $Y$ is the empty set.

</div>

{% details Proof %}
First, a product is empty exactly when one of its factors is: if $X = \varnothing$ or $Y = \varnothing$, there is no pair $(x, y)$ with $x \in X$ and $y \in Y$, so $X \times Y = \varnothing$; and if $x \in X$ and $y \in Y$ exist, then $(x, y) \in X \times Y$.

($\impliedby$) If $X = Y$, the two products are literally the same. If $X = \varnothing$ or $Y = \varnothing$, then $X \times Y = \varnothing = Y \times X$ by the observation above.

($\implies$) Suppose $X \times Y = Y \times X$, and that neither set is empty; we show $X = Y$. Let $x \in X$, and pick any $y \in Y$. Then $(x, y) \in X \times Y = Y \times X$, so $(x, y) = (y', x')$ for some $y' \in Y$ and $x' \in X$. By [Lemma 2.12.1](#lem-2-12-1), $x = y'$, so $x \in Y$. Hence $X \subseteq Y$. Swapping the roles of $X$ and $Y$ in the same argument gives $Y \subseteq X$, and by [Exercise 2.1](/blog/2026/sets-and-axioms/#ex-2-1), $X = Y$. $\square$
{% enddetails %}

What about bracketing? Pairing a pair with a third thing can be done in two ways, and they are not the same.

<div class="box-theorem" markdown="1" id="thm-2-13">

**Theorem 2.13.** For any three sets $X$, $Y$ and $Z$, $(X \times Y) \times Z = X \times (Y \times Z)$ if and only if one of $X$, $Y$ or $Z$ is the empty set.

</div>

{% details Proof %}
Here the elements of $(X \times Y) \times Z$ are pairs of the form $((x, y), z)$, with an ordered pair inside an ordered pair, while those of $X \times (Y \times Z)$ have the form $(x, (y, z))$.

($\impliedby$) If one of the three sets is empty, then by the observation at the start of the proof of [Theorem 2.12](#thm-2-12), both sides are empty. For example, if $Y = \varnothing$, then $X \times Y = \varnothing$, so $(X \times Y) \times Z = \varnothing$, and $Y \times Z = \varnothing$, so $X \times (Y \times Z) = \varnothing$.

($\implies$) We prove this by contradiction. Suppose $(X \times Y) \times Z = X \times (Y \times Z)$ while $X$, $Y$ and $Z$ are all non-empty. Fix some $x \in X$ and $y \in Y$.

Let $z$ be any element of $Z$. Then $((x, y), z) \in (X \times Y) \times Z = X \times (Y \times Z)$, so

$$
((x, y), z) = (x', (y', z'))
$$

for some $x' \in X$, $y' \in Y$ and $z' \in Z$. Comparing second entries using [Lemma 2.12.1](#lem-2-12-1), $z = (y', z') = \lbrace \lbrace y' \rbrace, \lbrace y', z' \rbrace \rbrace$. By the same lemma, $y'$ and $z'$ are uniquely determined by $z$. So every element $z \in Z$ is a pair whose second entry $z'$ is again an element of $Z$, and

$$
z' \in \lbrace y', z' \rbrace \in z.
$$

Now start from any $z_0 \in Z$ and repeat this: $z_0$ determines $z_1 \in Z$, which determines $z_2 \in Z$, and so on. Writing $w_k := \lbrace y_k', z_{k+1} \rbrace$ for the middle sets, we get

$$
\dots \in z_2 \in w_1 \in z_1 \in w_0 \in z_0,
$$

an infinite descending chain of membership. This contradicts the consequence (iii) of the [axiom of foundation](/blog/2026/sets-and-axioms/#def-2-4) proved in [Theorem 2.6](/blog/2026/operations-on-sets/#thm-2-6). So at least one of $X$, $Y$ and $Z$ must be empty. $\square$
{% enddetails %}

So $(X \times Y) \times Z$ and $X \times (Y \times Z)$ hold "the same information" but are genuinely different sets. For products of more than two sets we therefore have to _choose_ a bracketing, once and for all. We bracket from the left.

<div class="box-definition" markdown="1" id="def-2-22">

**Definition 2.22 (n-ary Product).** For $n \geq 3$, the **ordered $n$-tuple** of the sets $x_1, x_2, \dots, x_n$ is defined from ordered pairs by

$$
(x_1, x_2, \dots, x_n) := \big( (x_1, x_2, \dots, x_{n-1}), x_n \big),
$$

so that, for example, $(x_1, x_2, x_3) := ((x_1, x_2), x_3)$. The **product** of $n$ sets $X_1, X_2, \dots, X_n$ is then given by

$$
X_1 \times X_2 \times \dots \times X_n := \lbrace (x_1, x_2, \dots, x_n) : x_k \in X_k \text{ for every } k \in [n] \rbrace,
$$

where $[n] = \lbrace 1, 2, \dots, n \rbrace$ is the index set from [Remark 2.14](/blog/2026/inductive-sets/#rem-2-14).

</div>

<span id="rem-2-17"></span>**Remark 2.17.** Two things follow directly from this definition. First, $X_1 \times \dots \times X_n = (X_1 \times \dots \times X_{n-1}) \times X_n$, so every $n$-ary product is built by repeatedly taking products of two sets, and is therefore a set by [Remark 2.16](#rem-2-16). Second, two $n$-tuples are equal if and only if all their entries are equal, entry by entry. For $n = 2$ this is [Lemma 2.12.1](#lem-2-12-1). If it holds for $(n-1)$-tuples, then $(x_1, \dots, x_n) = (y_1, \dots, y_n)$ means $((x_1, \dots, x_{n-1}), x_n) = ((y_1, \dots, y_{n-1}), y_n)$, so by the lemma $x_n = y_n$ and $(x_1, \dots, x_{n-1}) = (y_1, \dots, y_{n-1})$, which gives the rest. By induction ([Theorem 2.11](/blog/2026/inductive-sets/#thm-2-11), starting at $n = 2$), it holds for all $n \geq 2$.

<span id="eg-2-23"></span>**Example 2.23.** Let $X = \lbrace 1, 2 \rbrace$, $Y = \lbrace 2, 3 \rbrace$ and $Z = \lbrace 3, 4 \rbrace$. Then

$$
\begin{aligned}
(X \times Y) \times Z = \lbrace\, &((1, 2), 3), ((1, 2), 4), ((1, 3), 3), ((1, 3), 4), \\
&((2, 2), 3), ((2, 2), 4), ((2, 3), 3), ((2, 3), 4) \,\rbrace, \\
X \times (Y \times Z) = \lbrace\, &(1, (2, 3)), (2, (2, 3)), (1, (3, 3)), (2, (3, 3)), \\
&(1, (2, 4)), (2, (2, 4)), (1, (3, 4)), (2, (3, 4)) \,\rbrace.
\end{aligned}
$$

By [Definition 2.22](#def-2-22), the triple product $X \times Y \times Z$ is just $(X \times Y) \times Z$ written more lightly:

$$
X \times Y \times Z = \lbrace (1, 2, 3), (1, 2, 4), (1, 3, 3), (1, 3, 4), (2, 2, 3), (2, 2, 4), (2, 3, 3), (2, 3, 4) \rbrace.
$$

Let us take one element of each bracketing and compare them as sets, to see what is different. Unpacking with [Definition 2.20](#def-2-20),

$$
\begin{aligned}
(1, 2, 3) = ((1, 2), 3) &= \lbrace \lbrace (1, 2) \rbrace, \lbrace (1, 2), 3 \rbrace \rbrace
= \lbrace \lbrace \lbrace \lbrace 1 \rbrace, \lbrace 1, 2 \rbrace \rbrace \rbrace, \lbrace \lbrace \lbrace 1 \rbrace, \lbrace 1, 2 \rbrace \rbrace, 3 \rbrace \rbrace, \\
(1, (2, 3)) &= \lbrace \lbrace 1 \rbrace, \lbrace 1, (2, 3) \rbrace \rbrace
= \lbrace \lbrace 1 \rbrace, \lbrace 1, \lbrace \lbrace 2 \rbrace, \lbrace 2, 3 \rbrace \rbrace \rbrace \rbrace.
\end{aligned}
$$

The first has $(1, 2)$ as its first entry, the second has $1$, so by [Lemma 2.12.1](#lem-2-12-1) they are completely different sets, exactly as [Theorem 2.13](#thm-2-13) predicts.

<span id="ex-2-10"></span>**Exercise 2.10.** Show that for all $x \in X$, $y \in Y$ and $z \in Z$, the triple $(x, y, z) = ((x, y), z) \in \mathcal{P}^2\big(\mathcal{P}^2(X \cup Y) \cup Z\big)$, and that $(x, (y, z)) \in \mathcal{P}^2\big(X \cup \mathcal{P}^2(Y \cup Z)\big)$.

{% details Solution %}
_A general fact first._ For any sets $A$ and $B$, if $a \in A$ and $b \in B$, then $(a, b) \in \mathcal{P}^2(A \cup B)$. Indeed, $a \in A \cup B$ and $b \in A \cup B$, so $\lbrace a \rbrace \subseteq A \cup B$ and $\lbrace a, b \rbrace \subseteq A \cup B$, i.e., both are elements of $\mathcal{P}(A \cup B)$. Hence $(a, b) = \lbrace \lbrace a \rbrace, \lbrace a, b \rbrace \rbrace \subseteq \mathcal{P}(A \cup B)$, which means $(a, b) \in \mathcal{P}(\mathcal{P}(A \cup B)) = \mathcal{P}^2(A \cup B)$.

_The first claim._ By the general fact with $A = X$ and $B = Y$, we have $(x, y) \in \mathcal{P}^2(X \cup Y)$. Now apply the general fact again with $a = (x, y)$, $A = \mathcal{P}^2(X \cup Y)$, $b = z$ and $B = Z$:

$$
((x, y), z) \in \mathcal{P}^2\big(\mathcal{P}^2(X \cup Y) \cup Z\big).
$$

Since $(x, y, z) = ((x, y), z)$ by [Definition 2.22](#def-2-22), this is the first claim.

_The second claim._ By the general fact, $(y, z) \in \mathcal{P}^2(Y \cup Z)$. Applying it again with $a = x$, $A = X$, $b = (y, z)$ and $B = \mathcal{P}^2(Y \cup Z)$ gives

$$
(x, (y, z)) \in \mathcal{P}^2\big(X \cup \mathcal{P}^2(Y \cup Z)\big). \qquad \square
$$

As a bonus, this shows that $X \times Y \times Z$ and $X \times (Y \times Z)$ are both honest sets, carved by specification out of these iterated power sets.
{% enddetails %}

<div class="box-definition" markdown="1" id="def-2-23">

**Definition 2.23 (Cartesian $n$-th Power).** A set $X$ raised to the **$n$-th power**, written $X^n$, is the $n$-ary product of $n$ copies of $X$:

$$
X^n := \underbrace{X \times X \times \dots \times X}_{n \text{ times}}.
$$

</div>

<span id="rem-2-18"></span>**Remark 2.18.** The set $\mathbb{R}^2$ describes the standard Euclidean plane, and the set $\mathbb{R}^3$ describes Euclidean $3$-space. Every point you have ever plotted on graph paper is an element of $\mathbb{R}^2$, which is to say an ordered pair of real numbers, which is to say (once we have built the reals) a rather elaborate set of sets of sets. Your school geometry box was doing set theory all along.

---

And with that, we have gone from the empty set to counting, to adding, to coordinates in space, using nothing but a handful of axioms. Was any of it actually _necessary_? Next time, we step back and ask what all this foundational machinery is for, and leave you with a stack of exercises to chew on.
