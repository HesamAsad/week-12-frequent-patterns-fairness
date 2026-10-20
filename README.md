# COMP90073 Workshop Week 12: Frequent Patterns and Fairness

An interactive workbook for the Week 12 tutorial of COMP90073 Trustworthy Machine Learning. It covers the contrast data mining lecture (Apriori, FP-growth, emerging patterns), Lecture 22 on bias and fairness, and the four questions of `w12-tutorial-answers.pdf`.

Live site: [hesamasad.github.io/week-12-frequent-patterns-fairness](https://hesamasad.github.io/week-12-frequent-patterns-fairness/). You can also open [`index.html`](index.html) locally in a browser. The only external requests are Google Fonts, KaTeX and highlight.js. A Light / Dark / Auto switch sits in the sidebar.

## What's inside

The four questions form the main sections. Each has the problem statement; a background section that explains the problem in plain words, why it matters, how the question fits (given, asked, not needed) and a step-by-step roadmap linked to the sections below; then inline prerequisites, a self-checking warm-up, a guided live activity, and one answer reveal.

| Question | Prerequisites | Live activity |
|---|---|---|
| 1 · Apriori and FP-growth on MONKEY, DONKEY, MAKE, MUCKY, COOKIE | support; the Apriori principle on the itemset lattice | Apriori level by level; the FP-tree built one transaction at a time; conditional pattern bases with prefix paths highlighted; candidates against min sup on a larger random database |
| 2 · "One free item may trigger $200" | anti-monotone and monotone constraints | the lattice split into a frequent region and a price region; what Apriori loses if it filters by price as it goes; the four-step rule mining on a small shop |
| 3 · Annotating and balancing subgroups | representation bias; Gender Shades | subgroup explosion as attributes are added, with label cost, rarest subgroup and an unannotated attribute; DBVAE resampling with an α slider |
| 4 · Adversarial debiasing code | predictor and adversary; the projection term | draggable gradient geometry; a predictor and adversary trained live, with and without the projection; working PyTorch code with its output |

**Additional material:**
- emerging patterns, on the network flows of the lecture;
- harms and the three families of fairness;
- the four group metrics on the toy loan example, with presets showing that they conflict;
- the Aequitas decision tree for choosing a metric;
- where to intervene.

It ends with cheat notes per question, a summary table and 16 references (DOIs checked on Crossref and DataCite, arXiv IDs on arXiv).

## Warm-up exercises

| Before | Warm-up | Answer |
|---|---|---|
| Question 1 | minimum count at 60%; count of {o}; support of {k, e} | 3; 3; 0.8 |
| Question 2 | supersets of a $270 itemset; one-item extensions of $150 | fraction 1; 1 |
| Question 3 | subgroups for 6 × 2 × 2 × 2; labels for 100 000 images × 4 | 48; 400 000 |
| Question 4 | one projected step for ∇L_P = (3, 1), ∇L_A = (1, 0), α = 1 | proj (3, 0); bracket (−1, 1); step · ∇L_A = 1 |

## Notes for the tutorial

- **Question 1.** The answer sheet lists {k, e, y} in C3 with its count, 2. Apriori's prune step removes it before counting, because {e, y} is infrequent; the final result is the same.
- **Question 1, efficiency.** The answer sheet says FP-growth builds the FP-tree "with a single scan". The tree needs two scans: one to count and order items, one to insert transactions (lecture, page 48). The page says two.
- **Question 4, our PyTorch run** on synthetic loan data (labels depend on a proxy for the group): accuracy 0.908 → 0.760 and approval-rate gap 0.559 → 0.098 when the adversary is added with α = 1. The adversary falls to chance (0.507).
