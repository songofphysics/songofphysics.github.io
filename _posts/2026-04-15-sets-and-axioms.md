---
layout: distill
title: The Axioms of Set Theory
description: What Sets Are, Why Naive Set Theory Breaks, and the ZFC Axioms That Fix It
tags: mathematics education
giscus_comments: false
date: 2026-04-15
featured: true

authors:
  - name: Sangeet. S
    url: "https://songofphysics.github.io/bio/"
    affiliations:
      name: Rishi Valley School

bibliography: sets-and-axioms.bib

toc:
  - name: Sets and Subsets
  - name: Axioms of Set Theory

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
  .box-definition > p:last-child,
  .box-theorem > p:last-child,
  .box-lemma > p:last-child {
    margin-bottom: 0;
  }
---

Ask a room full of students what the most fundamental thing in mathematics is and most of them will say _numbers_. Fair enough. We all start learning mathematics by counting. Yet a vast majority of mathematics can be built directly out of something even more primitive: **sets**. Over this series we will actually do it, constructing the natural numbers out of nothing but sets (and, as we will see, quite literally out of nothing).

This post is the first in a series on elementary set theory, adapted from my textbook in progress. Our goal is to get a working introduction to sets, and then to peel back a few layers and look at their foundational nature. The hope is that we come away knowing not only how to use and play with sets, but also how they shape the very fabric of modern mathematics.

---

## Sets and Subsets

<div class="box-definition" markdown="1">

**Definition 2.1.** A **set** is a _well-defined_<d-footnote>What it means for a set to be <em>well-defined</em> is exactly what the <strong>axioms of set theory</strong>, further down this post, are for.</d-footnote> collection of _distinct_ **elements**.

</div>

Notation first, because we are going to use a lot of it.

**Remark 2.1.** A few comments on notation before we proceed.

1. A **set** $X$ can often<d-footnote>There are sets for which a roster is not possible, such as the real numbers. One of the axioms below gives us a more general way to specify sets.</d-footnote> be _specified_ by a **roster** or **list** of its elements enclosed within curly braces, i.e., $X := \lbrace \dots \rbrace$, where the "$\dots$" are placeholders for the elements of $X$.
2. If $x$ is an element of the set $X$, we write $x \in X$. We read this as "$x$ **is in** $X$" or "$x$ **belongs to** $X$".
3. If $x$ is not an element of the set $X$, we write $x \notin X$. We read this as "$x$ **is not in** $X$" or "$x$ **does not belong to** $X$".

**Example 2.1.** $X := \lbrace 1, 2, 3 \rbrace$ is a set, and $2 \in X$, but $5 \notin X$.

**Example 2.2.** $\mathbb{Z} := \lbrace \dots, -2, -1, 0, 1, 2, \dots \rbrace$ is the set of **integers**, and $-7 \in \mathbb{Z}$, but $0.5 \notin \mathbb{Z}$.

Once we have sets, the most basic question we can ask about two of them is whether one sits inside the other.

<div class="box-definition" markdown="1">

**Definition 2.2.** A set $A$ is called a **subset** of a set $B$ if and only if $\forall a : (a \in A \implies a \in B)$, and we write $A \subseteq B$. The set $B$ is then called a **superset** of $A$, written $B \supseteq A$. When this is not the case, we write $A \not\subseteq B$ and $B \not\supseteq A$.

</div>

In plain English: _every element of $A$ is also an element of $B$_.

**Example 2.3.** Let $A := \lbrace 1, 2, 3 \rbrace$ and $B := \lbrace 1, 2, 3, 4, 5 \rbrace$. Then $A \subseteq B$, but $C := \lbrace 5, 6 \rbrace \not\subseteq B$.

The next example trips up a surprising number of people, so read it slowly.

**Example 2.4.** Let $A := \lbrace 1, \lbrace 2, 3 \rbrace \rbrace$. Then $B := \lbrace 2, 3 \rbrace \in A$, but $B \not\subseteq A$, since $2 \in B$ while $2 \notin A$. However, the set $\lbrace B \rbrace \subseteq A$. Furthermore, $\lbrace 2 \rbrace \not\subseteq A$, and $2 \notin A$ either, despite $2 \in B$ and $B \in A$. Being an element of an element does not make you an element.

**Example 2.5.** The set of natural numbers is a subset of the set of integers, which is in turn a subset of the set of rational numbers, i.e., $\mathbb{N} \subseteq \mathbb{Z} \subseteq \mathbb{Q}$.

<div class="box-theorem" markdown="1">

**Theorem 2.1.** Every set is a subset of itself.

</div>

{% details Proof %}
We will prove this by contradiction. Let $A$ be a set with $A \not\subseteq A$. Then<d-footnote>Here we use that $P \implies Q$ is logically equivalent to $\neg P \lor Q$, so its negation is $P \land \neg Q$.</d-footnote> it is not the case that $\forall a : (a \in A \implies a \in A)$, so $\exists a : (a \in A \land a \notin A)$, which is a contradiction. Thus $A \subseteq A$. $\square$
{% enddetails %}

<div class="box-definition" markdown="1">

**Definition 2.3.** Two sets are **disjoint** when they share no common elements.

</div>

**Example 2.6.** The set $\lbrace 1, 2 \rbrace$ is disjoint from $\lbrace 3, 4 \rbrace$ but not from $\lbrace 1, 3 \rbrace$.

**Example 2.7.** The set of rational numbers and the set of irrational numbers are disjoint.

So far, so harmless. Collect some things in curly braces, check what is inside what. What could possibly go wrong?

---

## Axioms of Set Theory

Historically, set theory was not developed as a consistent axiomatic system. It was developed intuitively, in simple language, and simple language turned out to be a trap. It led to a bunch of paradoxes, which in turn led to what is now called the _foundational crisis in mathematics_. Let's look at the most famous one.

<div class="box-theorem" markdown="1">

**Theorem 2.2 (Russell).** There is no set of all sets that are not members of themselves.<d-footnote>This is the much-famed <strong>Russell's paradox</strong>. Bertrand Russell was an influential mathematician and philosopher whose contributions greatly shaped the foundations of mathematics.</d-footnote>

</div>

{% details Proof %}
We will prove this by contradiction. Suppose such a set $R$ exists, i.e., the elements $X \in R$ are exactly the sets with $X \notin X$. Now ask whether $R$ is a member of itself. If $R \in R$, then $R$ fails the condition for membership, so $R \notin R$. If $R \notin R$, then $R$ satisfies the condition, so $R \in R$. Either way we have a contradiction, so no such set $R$ exists. $\square$
{% enddetails %}

Russell came across this in 1901 and published it in _The Principles of Mathematics_<d-cite key="russell1903principles"></d-cite>. Before you dismiss it as a cute word game, notice what actually went wrong. We wrote down a perfectly sensible-sounding property, "is not a member of itself", and assumed that the collection of everything with that property is a set. The naïve, vanilla version of set theory does nothing to stop us from doing that, because it never properly specifies what can and cannot be a set. And Russell's is far from the only paradox of this kind.

So it falls upon us to write down axioms that make sets _well-defined_. The first axiomatisation was given by Ernst Zermelo in 1908<d-cite key="zermelo1908untersuchungen"></d-cite>. Abraham Fraenkel's improvements in 1922<d-cite key="fraenkel1922grundlagen"></d-cite> led to what we now call **Zermelo–Fraenkel set theory**, or ZF. Add the axiom of choice and you get **ZFC**.

<div class="box-definition" markdown="1">

**Definition 2.4.** For a **set** to be _well-defined_, it must satisfy the **ZFC axioms** below.

**(Null Set)** There exists a set with no elements, called the **null set**<d-footnote>Also known as the <strong>empty set</strong>.</d-footnote> and denoted by $\varnothing$.

**(Extension)** Two sets are equal if and only if they have the same elements.

**(Foundation)** Every non-empty set $S$ contains an element that is disjoint from $S$.<d-footnote>If this one looks strange, you are paying attention. The remarks after this list explain it.</d-footnote>

**(Specification)** For any predicate $P$ and any set $S$, the elements $x \in S$ satisfying<d-footnote>Technically this is an <strong>axiom schema</strong>, because it is one axiom for every predicate $P$.</d-footnote> $P(x)$ form a set, denoted by<d-footnote>This is called <strong>set-builder</strong> notation.</d-footnote> $\lbrace x \in S : P(x) \rbrace$.

**(Pairing)** For any two sets $A$ and $B$, there exists a set that contains $A$ and $B$.

**(Union)** For any set $S$, there exists a set containing every element of every $x \in S$.

**(Power Set)** For any set $S$, there exists a set of all subsets of $S$, called the **power set** of $S$ and denoted by $\mathcal{P}(S)$.

**(Replacement)** The image<d-footnote>Images will be discussed properly when we get to relations and functions.</d-footnote> of a set under any definable mapping is also a set.

**(Infinity)** There exists at least one set containing infinitely many elements.

**(Choice)** For any set $S$ of non-empty sets, there exists a **choice function**<d-footnote>This is a can of worms that we will not open any further, but we will be using it implicitly in a bunch of places.</d-footnote> that assigns to each $X \in S$ an element of $X$ itself.

</div>

**Remark 2.2.** The **axiom of foundation** may seem strange at first glance, especially when we consider a set like $\lbrace 1, 2, 3 \rbrace$. What does it even mean for a _number_ to be disjoint from a set? To answer this, we must first construct numbers using sets and say exactly what they are. We will do this in the post on inductive sets, two posts from now.

**Remark 2.3.** The **axiom of foundation**<d-footnote>Also known as the <strong>axiom of regularity</strong>, in the sense that it regulates set membership.</d-footnote> rules out exactly the kind of self-membership that the Russell set $R$ of Theorem 2.2 trips over. In Theorem 2.6, in the next post, we show that it forbids self-membership ($x \in x$), membership loops ($x \in y \in x$) and infinite descending chains of membership ($\dots \in x_n \in \dots \in x_1 \in x_0$).

**Remark 2.4.** The **axiom of specification**<d-footnote>Also known as the <strong>axiom of restricted comprehension</strong>. It is <em>restricted</em> in the sense that the elements must be <em>comprehended</em> from an existing set and cannot simply be anything.</d-footnote> gives us the very useful **set-builder notation**. We read $S := \lbrace x \in A : P(x) \rbrace$ in plain English as:

_$S$ is defined to be_ ($S :=$) _the set of all_ ($\lbrace \dots \rbrace$) _elements $x$ in the set $A$_ ($x \in A$) _such that_ ($:$) _$P(x)$ is true._

This notation is very helpful when dealing with large sets. Notice also what it does _not_ let us do: we can only carve elements out of a set $A$ we already have. We cannot simply declare "the set of everything with property $P$", which is precisely the move that landed us in Russell's paradox.

**Example 2.8.** $S := \lbrace n \in \mathbb{Z} : 2 \mid n \rbrace$ is read as "_$S$ is defined to be the set of all elements $n$ in the set of integers such that $2$ divides $n$_". As a roster, $S = \lbrace \dots, -4, -2, 0, 2, 4, \dots \rbrace$.

With the axiom of extension in hand, we can sharpen our notion of a subset.

<div class="box-definition" markdown="1">

**Definition 2.5.** A subset $A$ of a set $B$, i.e., $A \subseteq B$, is called a **proper subset**<d-footnote>$B$ is then a <strong>proper superset</strong> of $A$, but this terminology is rarely used.</d-footnote> when $A \neq B$. This is denoted by $A \subset B$ or sometimes $A \subsetneq B$. A subset that is not proper is called an **improper subset**.

</div>

Fair warning: plenty of books use $\subset$ to mean $\subseteq$. Always check a book's conventions before trusting its symbols.

<div class="box-theorem" markdown="1">

**Theorem 2.3.** Every set has a unique **improper subset**, namely the set itself.

</div>

{% details Proof %}
Let $B$ be a set.

_Existence._ By Theorem 2.1, $B \subseteq B$. Since $B = B$, the subset $B$ of $B$ is not proper by Definition 2.5, so $B$ is an improper subset of itself.

_Uniqueness._ Let $A$ be any improper subset of $B$. Then $A \subseteq B$, and since $A$ is not proper, it is not the case that $A \neq B$, i.e., $A = B$. So if $A_1$ and $A_2$ are both improper subsets of $B$, then $A_1 = B$ and $A_2 = B$. By the axiom of extension, $A_1$ and $A_2$ have exactly the same elements as $B$, and hence as each other, so $A_1 = A_2$. Thus $B$ is the one and only improper subset of $B$. $\square$
{% enddetails %}

**Exercise 2.1.** Show that $A = B$ if and only if $A \subseteq B$ and $B \subseteq A$.

{% details Solution %}
We prove both directions.

($\implies$) Suppose $A = B$. By Theorem 2.1, $A \subseteq A$. Replacing $A$ by $B$ on either side of this gives $A \subseteq B$ and $B \subseteq A$.

($\impliedby$) Suppose $A \subseteq B$ and $B \subseteq A$. By Definition 2.2, $\forall x : (x \in A \implies x \in B)$ and $\forall x : (x \in B \implies x \in A)$. Together these give $\forall x : (x \in A \iff x \in B)$, so $A$ and $B$ have exactly the same elements. By the axiom of extension, $A = B$. $\square$

This is how equality of sets is proved in practice: show each set is a subset of the other.
{% enddetails %}

**Exercise 2.2.** Construct any $5$ **disjoint subsets** of the integers and express them using **set-builder notation**, **roster notation** and plain English.

{% details Solution %}
We read "disjoint" as _pairwise_ disjoint: no two of the five sets share an element. Sort the integers by their remainder on division by $5$. For each $r \in \lbrace 0, 1, 2, 3, 4 \rbrace$, let

$$
A_r := \lbrace n \in \mathbb{Z} : 5 \mid (n - r) \rbrace.
$$

Written out:

- $A_0 = \lbrace n \in \mathbb{Z} : 5 \mid n \rbrace = \lbrace \dots, -10, -5, 0, 5, 10, \dots \rbrace$, the integers divisible by $5$.
- $A_1 = \lbrace n \in \mathbb{Z} : 5 \mid (n - 1) \rbrace = \lbrace \dots, -9, -4, 1, 6, 11, \dots \rbrace$, the integers that leave remainder $1$ on division by $5$.
- $A_2 = \lbrace n \in \mathbb{Z} : 5 \mid (n - 2) \rbrace = \lbrace \dots, -8, -3, 2, 7, 12, \dots \rbrace$, the integers that leave remainder $2$ on division by $5$.
- $A_3 = \lbrace n \in \mathbb{Z} : 5 \mid (n - 3) \rbrace = \lbrace \dots, -7, -2, 3, 8, 13, \dots \rbrace$, the integers that leave remainder $3$ on division by $5$.
- $A_4 = \lbrace n \in \mathbb{Z} : 5 \mid (n - 4) \rbrace = \lbrace \dots, -6, -1, 4, 9, 14, \dots \rbrace$, the integers that leave remainder $4$ on division by $5$.

Here the remainder is always taken in $\lbrace 0, 1, 2, 3, 4 \rbrace$, so for example $-4 = 5 \cdot (-1) + 1$ leaves remainder $1$.

_Pairwise disjointness._ Suppose, for contradiction, that $n \in A_r$ and $n \in A_s$ for some $0 \le r \lt s \le 4$. Then $5 \mid (n - r)$ and $5 \mid (n - s)$, so $5$ divides their difference $(n - r) - (n - s) = s - r$. But $0 \lt s - r \le 4$, and no integer strictly between $0$ and $5$ is a multiple of $5$. This is a contradiction, so the five sets are pairwise disjoint. $\square$

Many other answers are equally valid. Five singletons such as $\lbrace 1 \rbrace, \dots, \lbrace 5 \rbrace$ technically work too, though that is a rather lazy way out.
{% enddetails %}

Now for a theorem that a lot of textbooks would rather you didn't hear about.

<div class="box-theorem" markdown="1">

**Theorem 2.4.** There exists no **universal set** $U$ that contains all possible sets.

</div>

{% details Proof %}
We will prove this by contradiction. Suppose such a set $U$ exists. By the **axiom of specification** with the predicate $P(x) :\iff x \notin x$, we have the set $R := \lbrace x \in U : x \notin x \rbrace$. Since $U$ contains every set, $R$ contains every set that is not a member of itself, and nothing else. But Theorem 2.2 says no such set exists. This is a contradiction, so $U$ cannot be a set. $\square$
{% enddetails %}

**Remark 2.5.** Many older texts, and some newer ones whose authors either do not know the subject or cannot do some basic research, suggest the existence of such a **universal set**. Theorem 2.4 settles that. What we can do instead is define something quite similar, relative to the sets we actually care about.

<div class="box-definition" markdown="1">

**Definition 2.6.** A set $U$ is a **universal set** for a given set $S$ if and only if every element of $S$ is a subset of $U$, i.e., $\forall X : (X \in S \implies X \subseteq U)$.

</div>

**Remark 2.6.** This definition presupposes that we already have a set of sets $S$, and the **axiom of union** guarantees that a universal set for it exists: the set containing every element of every $X \in S$ will do. In problems involving sets, we can intuitively imagine the universal set to be some set that simply includes all elements of the sets given to us. In principle, it can contain even more elements.

**Example 2.9.** For $S := \lbrace \lbrace 1, 2 \rbrace, \lbrace 2, 3 \rbrace, \lbrace 4, 5 \rbrace \rbrace$, the set $U = \lbrace 1, 2, 3, 4, 5 \rbrace$ is a universal set<d-footnote>For the given set $S$, that is, not a universal set for everything.</d-footnote>.

**Exercise 2.3.** Verify that the claim made in Example 2.9 satisfies our definition of a universal set.

{% details Solution %}
By Definition 2.6, we must check that every $X \in S$ satisfies $X \subseteq U$, where $U = \lbrace 1, 2, 3, 4, 5 \rbrace$. The set $S$ has exactly three elements, so we check each in turn using Definition 2.2.

- $X = \lbrace 1, 2 \rbrace$: both $1 \in U$ and $2 \in U$, so $X \subseteq U$.
- $X = \lbrace 2, 3 \rbrace$: both $2 \in U$ and $3 \in U$, so $X \subseteq U$.
- $X = \lbrace 4, 5 \rbrace$: both $4 \in U$ and $5 \in U$, so $X \subseteq U$.

Hence $\forall X : (X \in S \implies X \subseteq U)$, and $U$ is a universal set for $S$. $\square$

Note that $U$ is not the only choice. The same check shows that $\lbrace 1, 2, 3, 4, 5, 6 \rbrace$, or $\mathbb{Z}$, is also a universal set for $S$. The set $\lbrace 1, 2, 3, 4, 5 \rbrace$ is simply the smallest one, the one the axiom of union hands us.
{% enddetails %}

---

So we now know what sets are, how to compare them, and which rules stop them from swallowing themselves whole. Next time, we start actually doing things with sets: unions, intersections, complements and differences. We will also cash in the promised consequences of the axiom of foundation. Strange axiom, isn't it? Let's see whether it earns its place.
