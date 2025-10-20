---
layout: post
title: Precalculus and Intro to Calculus
description: A Pre-University Course in Mathematics.
img: assets/img/precalc.png
importance: 2
tags: teaching
category: Courses
related_posts: false
related_publications: false
giscus_comments: false
toc:
  beginning: true
---

{% include figure.liquid loading="eager" path="assets/img/precalc.png" title="precalculus" class="img-fluid rounded z-depth-1" %}

---

## About

This is a **pre-University course** and is one part of a standard mathematics curriculum which also includes elementary algebra, combinatorial probability, statistics and co-ordinate geometry. The current offering is tailored to the **Indian School Certificate Mathematics Curriculum for students of Rishi Valley School**. However, depending on time and interests **there may be occasional deeper dives** or tangents to related topics which are indicated by the asterisk (\*) in the syllabus we have covered, sometimes using video content. Some topics may have been covered via exercises or homework and are indicated by (\*\*). Topics which we have not covered but I consider essential are also listed _italicised_ for interested students.

---

### Syllabus

<!-- prettier-ignore -->
<table>
  <tr>
    <td style="vertical-align:top; padding:8px;">
      <ol>
        <li><strong>Naive Set Theory</strong>
          <ol>
            <li>Defining Sets: Roster and Set-Builder</li>
            <li>Cardinality of Finite Sets</li>
            <li>Equal and Equivalent Sets</li>
            <li>Unions and Intersections of Sets</li>
            <li>Set Difference and **Symmetric Difference</li>
            <li>**Algebraic Properties of Sets</li>
            <li>Proper and Improper Subsets</li>
            <li>**The Power Set</li>
            <li>Cartesian Product of Sets</li>
            <li>Relations on Sets</li>
            <li>Equivalence Relations</li>
            <li><em>Equivalence Classes</em></li>
          </ol>
        </li>
      </ol>
    </td>

    <td style="vertical-align:top; padding:8px;">
      <ol start="2">
        <li><strong>Logic and Proofs</strong>
          <ol>
            <li>Propositions and Truth Tables</li>
            <li>Negations, Disjunctions and Conjunctions</li>
            <li>Conditionals and Implications</li>
            <li>*Principle of Explosion and **Vacuous Truth</li>
            <li>Existential and Universal Quantifiers</li>
            <li>*Informal Introduction to Axiomatic Systems</li>
            <li>Direct Proof and Proof by Contradiction</li>
            <li>Proof by Contrapositive</li>
            <li>Proof by Induction</li>
            <li>*Consistency and Completeness</li>
            <li><em>Boolean Algebra and Universality</em></li>
            <li><em>Gödel's Incompleteness Theorems</em></li>
          </ol>
        </li>
      </ol>
    </td>

  </tr>

  <tr>
    <td style="vertical-align:top; padding:8px;">
      <ol start="3">
        <li><strong>Functions</strong>
          <ol>
            <li>Functions as Relations</li>
            <li>Domain and Co-domain</li>
            <li>Algebraic Functions</li>
            <li>*Comment on Singularities</li>
            <li>Logarithms and Exponents</li>
            <li>Trigonometric Functions</li>
            <li>Step Functions, Square Root and Modulus</li>
            <li>Image and Preimage</li>
            <li>Injectivity and Surjectivity</li>
            <li>Invertible Functions</li>
            <li>**Composition of Functions</li>
            <li>*Infinite Sets and Countability</li>
            <li><em>Binary Operations as Functions</em></li>
          </ol>
        </li>
      </ol>
    </td>

    <td style="vertical-align:top; padding:8px;">
      <ol start="4">
        <li><strong>Sequences and Series</strong>
          <ol>
            <li>Sequences as Functions</li>
            <li>Summation and Product Notation</li>
            <li>The Telescoping Property</li>
            <li>Arithmetic Progressions (AP)</li>
            <li>Partial Sum of an AP</li>
            <li>Sum of the first N Naturals</li>
            <li>Geometric Progressions (GP)</li>
            <li>Partial Sum of a GP and Geometric Series</li>
            <li>Sum of the first N squared/cubed Naturals</li>
            <li>**Inequality of Arithmetic and Geometric Means</li>
            <li>**Arithmetico-Geometric Progressions and Series</li>
            <li>*Informal and visual notion of convergence</li>
            <li><em>Rigorous definition of convergent sequences</em></li>
          </ol>
        </li>
      </ol>
    </td>

  </tr>

  <tr>
    <td style="vertical-align:top; padding:8px;">
      <ol start="5">
        <li><strong>Limits</strong> 
          <ol>
            <li>The meaning of <em>tends to</em></li> 
            <li>Limits from graphs of functions</li>
            <li>Left-Hand and Right-Hand limits</li>  
            <li>Rigorous definition of a Limit</li>
            <li>Algebraic properties of limits</li>  
            <li>Sandwich Theorem</li> 
            <li>Continuity of functions</li> 
            <li>Differentiable functions</li> 
            <li>Standard derivatives</li>
            <li>Properties of derivatives</li> 
            <li>*L'Hospital's Rule for limits</li> 
          </ol>
        </li>
      </ol>
    </td>

    <td style="vertical-align:top; padding:8px;"></td>

  </tr>
</table>

### Resources

<style>
  .pdf-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
    align-items: start;
    max-width: 1200px;
    margin: 0 auto;
    padding: 12px;
  }

  .pdf-card {
    display: flex;
    flex-direction: column;
  }

  .pdf-container {
    position: relative;
    width: 100%;
    aspect-ratio: 3 / 4;      /* portrait */
    min-height: 520px;        /* fallback for old browsers */
    background: #fafafa;
    border: 1px solid #ddd;
    border-radius: 6px;
    overflow: hidden;
  }

  .pdf-container iframe {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    border: 0;
    display: block;
  }

  /* caption + actions */
  figure {
    margin: 10px 0 0;
  }
  figcaption {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
    font-size: 14px;
    color: #111;
  }
  .caption-text { flex: 1; }

  .actions {
    display: flex;
    gap: 8px;
  }
  .btn {
    display: inline-block;
    padding: 6px 10px;
    border-radius: 6px;
    border: 1px solid #bdbdbd;
    background: #fff;
    text-decoration: none;
    color: #111;
    font-size: 13px;
  }
  .btn:hover { box-shadow: 0 1px 3px rgba(0,0,0,0.08); }

  @media (max-width: 800px) {
    .pdf-grid { grid-template-columns: 1fr; }
    figcaption { flex-direction: column; align-items: flex-start; gap: 8px; }
  }
</style>

<div class="pdf-grid">
  <!-- Card 1 -->
  <div class="pdf-card" aria-label="PDF 1 card">
    <div class="pdf-container">
      <iframe
        src="https://www.stitz-zeager.com/szprecalculus07042013.pdf#page=1&zoom=page-width"
        title="Precalculus — Stitz & Zeager"
        loading="lazy"></iframe>
    </div>

    <figure>
      <figcaption>
        <div class="caption-text">Stitz & Zeager — Precalculus</div>
        <div class="actions">
          <a class="btn" href="https://www.stitz-zeager.com/szprecalculus07042013.pdf#page=1&zoom=page-width"
             target="_blank" rel="noopener" aria-label="Open Precalculus PDF in new tab">Open</a>
        </div>
      </figcaption>
    </figure>

  </div>

  <!-- Card 2 -->
  <div class="pdf-card" aria-label="PDF 2 card">
    <div class="pdf-container">
      <iframe
        src="https://ocw.mit.edu/courses/res-18-001-calculus-fall-2023/mitres_18_001_f17_full_book.pdf#page=1&zoom=page-width"
        title="Calculus — MIT OCW"
        loading="lazy"></iframe>
    </div>

    <figure>
      <figcaption>
        <div class="caption-text">MIT OCW — Calculus</div>
        <div class="actions">
          <a class="btn" href="https://ocw.mit.edu/courses/res-18-001-calculus-fall-2023/mitres_18_001_f17_full_book.pdf#page=1&zoom=page-width"
             target="_blank" rel="noopener" aria-label="Open Calculus PDF in new tab">Open</a>
        </div>
      </figcaption>
    </figure>

  </div>
</div>

<div class="caption">
    Recommended external literature for self-study and deeper dives.
</div>

<div class="row g-3 mt-3">
  <div class="col-12 col-md-6">
    <div class="ratio ratio-16x9">
      {% include video.liquid
         path="https://www.youtube.com/embed/videoseries?list=PLBh2i93oe2qu-1dodE4LzI0a_Mxlvdsbk"
         class="img-fluid rounded z-depth-1"
         title="TBSOM Start Learning Logic" %}
    </div>
  </div>

  <div class="col-12 col-md-6">
    <div class="ratio ratio-16x9">
      {% include video.liquid
         path="https://www.youtube.com/embed/videoseries?list=PLBh2i93oe2qsO_p91ei-eYTQ9-HKQ5i30"
         class="img-fluid rounded z-depth-1"
         title="TBSOM Start Learning Sets" %}
    </div>
  </div>

  <div class="col-12 col-md-6">
    <div class="ratio ratio-16x9">
      {% include video.liquid
         path="https://www.youtube.com/embed/videoseries?list=PLBE9407EA64E2C318"
         class="img-fluid rounded z-depth-1"
         title="MIT OCW Calculus (Strang)" %}
    </div>
  </div>

  <div class="col-12 col-md-6">
    <div class="ratio ratio-16x9">
      {% include video.liquid
         path="https://www.youtube.com/embed/videoseries?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr"
         class="img-fluid rounded z-depth-1"
         title="3B1B Essence of Calculus" %}
    </div>
  </div>
</div>

<div class="caption">
    Helpful playlists from <a href="https://thebrightsideofmathematics.com/">The Bright Side of Mathematics</a> by Dr. Julian Grossmann and <a href="https://ocw.mit.edu/">MIT OpenCourseWare</a> featuring Professor Gilbert Strang and <a href="https://www.3blue1brown.com/lessons/essence-of-calculus#title">3B1B's Essence of Calculus</a> courtesy of Grant Sanderson.
</div>
---

## Exercises and Tests

All previous assignments, soft homework and test papers will be available here shortly. If there are any errors, please do not hesitate to contact me. If any students wish to contribute to official solutions to the problems, they may contact me and I will host their solutions on the website if satisfactory.

---

## General Updates

Any and all general updates will be made on the Google Classroom for the course or over email until we are back from the term break. Homework for the term break has already been informed to you. Besides this, we will only have projects to discuss and work on.

### Projects

All **students are required to share** a Google Document or an [Overleaf](https://www.overleaf.com/learn) file with me **for their respective projects**. For those who are yet to get started and those whose projects aim to be more explanatory involving fewer equations, I recommend sharing a Google Document. For those who are working on far more analytical topics which may require multiple definitions and proofs, I recommend sharing an Overleaf link by email. This needs to be done by $$\mathbf{25^{th}}$$ **October 2025**. More details on the project rubrik and evaluation will be here shortly. **Upto four selected projects may get featured on my** [blog](/blog/) :)

---
