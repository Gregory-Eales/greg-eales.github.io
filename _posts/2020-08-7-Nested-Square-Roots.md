---
layout: post
mathjax: true
comments: true
title:  "Nested Square Roots"
date:   2020-08-6 23:41:54 +0000
categories: github jekyll
---

### Introduction

This problem gives us equation below of nested square roots. We are tasked with finding the number pairs for which this equations can be denested such that it is equal to the sum of individual roots.


$$ \sqrt{x + \sqrt{y} + \sqrt{z}} $$


Here we have three integers such that $x \in  \mathbb{N}$ and $ y, z \in M$ where $  \{M \mid M \in \mathbb{N}, \sqrt{M} \notin\mathbb{N} \}$



$$\sqrt{x + \sqrt{y} + \sqrt{z}} = \sum_{i=1}^{k} s_{i} \sqrt{a_{i}}$$


Let $F(n)$ be the number of unique sets of $a_{i}$ that can represent the denested sum and/or difference of the nested square root where $0 < x \leq n $, $s_{i} = \pm 1$, $a_{i} \in \mathbb{N}$, and $k < \infty$



### Analysis

In order to solve this problem algorithmicly in a feasable amount of time we have to define the upper bound of search values for z, y, and the denested terms.


$$ x + \sqrt{y} + \sqrt{z} = (\sum_{i=1}^{k} s_{i} \sqrt{a_{i}})^{2} $$


We first start by squaring both sides and attempting to simplify the summation term. This can be done by a simple foiling and manipulation of the s term to allow for seperation.


$$ x + \sqrt{y} + \sqrt{z} = \sum_{i=1}^{k} a_{i} + 2\sum_{j=1}^{k}\sum_{i=1}^{k} s_{ij} \sqrt{a_{i}a_{j}} $$

This is where $s_{ij} = 0$ if $i=j$. We know that both radicals on the left side of the equations must be irrational due the fact that they cannot be perfect squares and we also know that any term $a_{i}$ is a rational positive integer. Because of these two facts we know that a possible class of solutions is when $x =  \sum_{i=1}^{k} a_{i}$ because they represent the rational portion of each side of the equation.


$$ x =  \sum_{i=1}^{k} a_{i} $$


The sum of each term in the unested form must be equal to x. This gives us an upper bound on the possible terms that can be used in the unested term and thus for y and z, decreasing our search space drasticly. Because both are positive integers and $ 0 < x < n < \infty$ we can find the finite set of terms $a_{i}$ such that y and z are non-perfect squares.



$$ 0 < k \leq x $$
\end{equation}


$$ 0 < a_{i} \leq x $$



we also know that $a_{i}  \ne a_{j}$ and we also know that no more than one $a_{i}$ can be a perfect square otherwise we will end up with irrational terms. removing the x term we have



$$ \sqrt{y} + \sqrt{z} = 2\sum_{j=1}^{k}\sum_{i=1}^{k} s_{ij} \sqrt{a_{i}a_{j}} $$


This tells us that both y and z must either be both factors of 4 or be factors of eachother such that when combined result in a number proportional to 4 because the right hand side of the quation is a multiple of 2. Lets also make a further assumption that the set of $ a_{i} $ is seprable such that



$$ \sqrt{y} = 2\sum_{j=1}^{k}\sum_{i=1}^{k} s_{ij} \sqrt{a_{i}a_{j}} $$


 $$ \sqrt{z} = 2\sum_{j=1}^{k}\sum_{i=1}^{k} s_{ij} \sqrt{a_{i}a_{j}} $$


This pair of equation tells us something interesting about the nature and relationship of y and z. In order for there to be a solution under the given assumptions the terms that add up to z and the terms that add up to y must have common multiples of eachother. If the terms that multiply are not multiples of either y or z they then must be cancelled out by an equal negative term that when summed results in a zero.


$$ y = 4\sum_{j=1}^{k}\sum_{i=1}^{k} a_{i}a_{j} + 4\sum_{j=1}^{k}\sum_{i=1}^{k}\sum_{l=1}^{k}\sum_{m=1}^{k} s_{ijlm} \sqrt{a_{i}a_{j}a_{l}a_{m}} $$

$$ z = 4\sum_{j=1}^{k}\sum_{i=1}^{k} a_{i}a_{j} + 4\sum_{j=1}^{k}\sum_{i=1}^{k}\sum_{l=1}^{k}\sum_{m=1}^{k} s_{ijlm} \sqrt{a_{i}a_{j}a_{l}a_{m}} $$

where $s_{ijlm} = 0$ when $i=j=l=m$
