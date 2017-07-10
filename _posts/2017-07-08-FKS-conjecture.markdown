---
author: karthikabinav
comments: true
date: 2017-07-08
layout: post
published: false
slug: FKS conjecture
title: Hypergraph Matching and the FKS conjecture
categories:
- Research
tags:
- Hypergraph Mathching
- Algorithms
---


In this post, we will review a paper due to Furedi, Kahn and Symour on Hypergraph Matching [^fn1]. We will describe an important conjecture described in their work and some recent progress
made towards resolving them. We will first start off with defining formally the hypergraph matching problem.

> **Definition** (Hypergraph Matching)
> Given a hypergraph \\( H=(V, E) \\) and a weight function \\( w: V \rightarrow \mathbb{R}^+ \\), the goal is to find a subset of edges \\( M \subseteq E \\)
  such that for any two edges \\( e\_1, e\_2 \in M \\),
  \\( e\_1 \cap e\_2 = \phi \\). The maximum hypergraph matching problem seeks to find an \\( M \\) such that $ M = \max_{M' \subseteq E: M' \text{ is a matching }} w(M') $.

For every edge $e$ let $k_e$ denote the number of vertices present in $e$. Note that for every edge, if $k_e =2$ it is the well-studied maximum matching problem in graphs
which can be solved in polynomial time. Additionally, for $k_e>=3$, the problem becomes NP-hard (a reduction from 3-SAT) and we usually resort to approximations.
A standard approach to approximate NP-hard problems is to consider the linear programming relaxation of the problem and obtain 




  [^fn1]: On the Fractional Matching Polytope of a Hypergraph, Furedi, Kahn, Seymour, Combinatorica 1993


