---
title: Optimization methods for generating contrastive examples
author:
  name: Ian Howell
  link: https://github.com/ihowell
date: 2022-01-27 10:49:00 +0600
categories: [Contrastive Explanation, Optimization]
tags: [Technical]
math: true
---

In this blog post, I introduce two methods of generating contrastive
examples. These methods are primarily used to generate examples on
image data, but can be generalized to other data as well.


## Manifold-Guided Examples (xGEMs)

Joshi *et al.* {% cite joshi2018xgems -A %} introduce a
contrastive-generation method that finds an input $\tilde{x}$ that
optimizes the distance to the original $\textbf{x}^*$ the loss of the
classifier $f_\phi$ on the target class. This results in the
optimization:

$$
\begin{equation}
    \tilde{x} =
        \mathcal{G}_\theta(\arg\min_{\textbf{z}\in\mathbb{R}^d}
            \mathcal{L}(\textbf{x}^*,\mathcal{G}_\theta(\textbf{z}))
            +\lambda l(f_\phi(\mathcal{G}(\textbf{z})),y_{tar})
        ),
    \tag{1}
    \label{xgems-optimization}
\end{equation}
$$

where $\mathcal{L}$ is the distance in data space from the original
$\textbf{x}^*$, $l$ is the original loss of the classifier (usually
softmax cross-entropy), and $\lambda$ is a user-defined term that
controls the ratio of losses to consider.


## Contrastive Deep Explanations (CDeepEx)

{% bibliography --cited %}
