---
layout: distill
title: Closure on Sets
description: Exercises on Set Theory and Further Reading
tags: mathematics education
giscus_comments: false
date: 2026-04-27
featured: true

authors:
  - name: Sangeet. S
    url: "https://songofphysics.github.io/bio/"
    affiliations:
      name: Rishi Valley School

bibliography: closure-on-sets.bib

toc:
  - name: Final Remarks
  - name: Further Reading
  - name: Exercises

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

This is the last post in our series on elementary set theory. Over the previous four, we met [sets and the axioms that tame them](/blog/2026/sets-and-axioms/), learnt to [operate on them](/blog/2026/operations-on-sets/), [built the natural numbers out of nothing](/blog/2026/inductive-sets/), and [paired things up into products](/blog/2026/products-of-sets/). Before moving on, let us step back and take stock, point you to some good books, and leave you with plenty to chew on.

---

## Final Remarks

We have now spoken about what the building blocks of mathematics are, namely sets, and we have seen how to play with them and deduce the [natural numbers](/blog/2026/inductive-sets/#def-2-13) from them. From this point onwards, it will be more than handy to treat the natural numbers as we know them intuitively, because our focus now shifts to _counting things_. We will revisit these foundations every time we are ready to define a new set of numbers.

One should bear in mind that almost none of what we discussed in this series has any truly direct practical application. I know, I know: "then why did we just spend four posts on it?" The real motivation is that mathematics, as we alluded to at the start, needs consistent logic underneath it to hold up in practical applications. If the framework itself is not sound, practical models may predict a lot of nonsense that will never hold up to evidence.

Thankfully, the foundational crisis began and came to a head around the time when extensive real-world applications of mathematics, mainly in physics and computer science, were still in their infancy. The acceptance of the [ZFC axioms](/blog/2026/sets-and-axioms/#def-2-4) seemed, on the surface, to resolve the issues, but it raised further philosophical questions. Those would take yet another book to outline and discuss, and they lie well outside the realm of "pure" mathematics.

We must also emphasise that this axiomatic approach to doing mathematics, also called _formalism_, is by no means the only or the "correct" way to do it. There are many other schools of thought, both historical and modern. That being said, formalism makes it much easier for us to check the internal consistency of mathematical statements. This is now being revolutionised by **proof assistants**,<d-footnote>Lean and Isabelle are two widely used examples.</d-footnote> which help mathematicians write ultra-formal statements and prove them from the statements of some axiomatic system, checked line by line by a computer. They can also help pinpoint problems in the axiomatic systems themselves, if any exist.

In what follows, we will keep up the formal theme, particularly when it comes to defining things carefully and proving results that enable efficient problem solving. But as we saw throughout this series, we will also blend it with good old-fashioned intuition, and try to build mental pictures that make sense of the definitions rather than playing some game of abstract nonsense. One of the main ways we will do this is by letting problems from the sciences act as guiding principles.

---

## Further Reading

If you want to go further than these posts, here are two books worth your time. They pull in rather different directions.

- **Richard Hammack, _Book of Proof_, third edition.**<d-cite key="hammack2018bookofproof"></d-cite> An introduction to the language and standard proof methods of mathematics, covering sets, logic, counting, induction, relations, functions and infinite cardinality. If the proofs in this series felt like a new language, this is the phrasebook, and it is the natural companion for the proof-by-contrapositive and induction exercises below. It is also free: Hammack makes it available [on his website](https://www.people.vcu.edu/~rhammack/BookOfProof/) under a Creative Commons licence.
- **Derek Goldrei, _Classic Set Theory: For Guided Independent Study_.**<d-cite key="goldrei1996classic"></d-cite> Written for students working on their own, this goes properly into the territory we only waved at: the natural numbers built from sets, the Zermelo–Fraenkel axioms, the axiom of choice (yes, that can of worms), cardinals and ordinal numbers. If $\omega$ and $\omega + 1$ from [Remark 2.10](/blog/2026/inductive-sets/#rem-2-10) left you curious, this is where to go next.

---

## Exercises

No solutions this time. You are on your own, and that is the point.

1. Write the power set of $S = \lbrace \pi, e, \varphi, 0 \rbrace$ in roster form. What would be an obvious and convenient universal set for $S$? Verify that it satisfies the [definition of a universal set](/blog/2026/sets-and-axioms/#def-2-6).

2. Let $A := \lbrace x \in \mathbb{Q} : (x \lt 0) \lor (x^2 \lt 2) \rbrace$. Construct a set $B \neq \varnothing$, disjoint from $A$, such that $A \cup B = \mathbb{Q}$ and $[(a \in A) \land (b \in B)] \implies a \lt b$. Determine the unique irrational real number $r$ that is greater than every element of $A$ and less than every element of $B$.

3. Show that $\forall n \in \mathbb{Z} : (n^2 \in 2\mathbb{Z} \implies n \in 2\mathbb{Z})$, where $2\mathbb{Z} := \lbrace m \in \mathbb{Z} : 2 \mid m \rbrace$. You may find it useful to start by verifying that $(p \implies q) \iff (\neg q \implies \neg p)$, and to use this in the proof. This is called a _proof by contrapositive_.

4. Show that the [symmetric difference](/blog/2026/operations-on-sets/#def-2-11) of sets is commutative and associative.

5. Using [induction](/blog/2026/inductive-sets/#thm-2-10), show that $\forall n \in \mathbb{N} : (m - 1) \mid (m^n - 1)$, where $m \in \mathbb{N}^{\ast} \setminus \lbrace 1 \rbrace$.

6. Using induction, show that $\forall n \in \mathbb{N} : 1^3 + 2^3 + \dots + n^3 = (1 + 2 + \dots + n)^2$.

7. Define the set of lines on a plane. Construct the Cartesian product of two such sets, and specify a condition (in accordance with the [axiom of specification](/blog/2026/sets-and-axioms/#def-2-4)) that restricts the product to ordered pairs of parallel straight lines.

8. Define the set of triangles on a plane. To do this, first consider the set $(\mathbb{R}^2)^3$ (see [Definition 2.23](/blog/2026/products-of-sets/#def-2-23)), and specify the condition under which a point of this set forms a triangle.

9. Define the set of co-prime integers in two equivalent ways.

10. Construct the set of all ordered pairs of elements of $F = \lbrace (a, b) \in \mathbb{Z}^2 : b \neq 0 \rbrace$ that represent the same rational number.

11. It is quite common to see [Definition 2.14](/blog/2026/inductive-sets/#def-2-14) stated in the following manner:

    $$
    \forall m, n \in \mathbb{N} : [m + 0 = m] \land [m + S(n) = S(m + n)]. \tag{2.1}
    $$
    - **(i)** Verify that $(2.1)$ satisfies [Definition 2.14](/blog/2026/inductive-sets/#def-2-14).
    - **(ii)** Show that $0 + m = m = m + 0$ and $S(m) + n = S(m + n) = m + S(n)$.
    - **(iii)** Using the above results, show that $m + n = n + m$. **(Commutativity)**
    - **(iv)** Show that if $k \in \mathbb{N}$, then $(m + n) + k = m + (n + k)$. **(Associativity)**
    - **(v)** Show that if $k \in \mathbb{N}$, then $m + k = n + k \implies m = n$. **(Right-Cancellation)**

    Parts (ii) and (iii) were done in [Exercise 2.5](/blog/2026/inductive-sets/#ex-2-5). Try them again without peeking, using $(2.1)$ alone.

12. Similarly to the previous problem, we can define the multiplication of naturals as:

    $$
    \forall m, n \in \mathbb{N} : [m \times 0 = 0] \land [m \times S(n) = (m \times n) + m]. \tag{2.2}
    $$

    Verify that this definition matches the intuitive idea of multiplication by a natural number as repeated addition. Furthermore, construct and prove the multiplicative analogues of the results in the previous problem. Careful: not every analogue holds without an extra condition.

---

That wraps up set theory, at least for now. Next up, we put all this machinery to work and start counting things properly. How many ways can you arrange a bookshelf, deal a hand of cards, or choose a cricket team? More than you'd think, and fewer than you'd fear.
