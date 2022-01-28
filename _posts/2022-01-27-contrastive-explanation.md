---
title: Contrastive Explanation
author:
  name: Ian Howell
  link: https://github.com/ihowell
date: 2022-01-27 8:11:00 +0600
categories: [Contrastive Explanation]
tags: [Nontechnical]
---

This post provides a brief description of contrastive questions and
explanations. It further delves into properties of good contrastive
explanations as proposed in the survey by Verma *et al.* {% cite
verma2020counterfactual -A %}.

# What is contrastive explanation?

If I were to ask you why the image below is of a five, what
would you say? How would you explain why this image contains a five?

![MNIST Digits](/assets/img/mnist_5.png){: width="300"}

One way to explain why it is a five is to explain why it is
different from the other digits. It is not a six, because the
bottom-left corner is not connected to the midsection to form a loop;
it is not a nine because there is no complete loop on the top half;
etc. However, these types of explanations are not directly answering
the question, but are instead answering why this is not another digit.

Contrastive questions are questions of the form "Why is *P* the case
and not *Q*?" or simply "Why *P* and not *Q*?" These types of
questions are natural to people and are sometimes even implicitly
desired, even if only "Why *P*?" is asked. A contrastive explanation
to such a question is one that provides a change to the circumstances
such that *Q* would be the case. *Q* is usually called the foil.

For example, suppose Alice is denied a loan. Alice asks the banker
"Why was my loan denied?"  Here, the foil is implicit and if it was
included, Alice would have asked "Why was my loan denied and not
accepted?" Likewise, it would be natural for the banker to give a
contrastive explanation as to why the loan was denied. The banker
might say:
> "If you made $10,000 more per year, your loan would be accepted,"

or they might say something like:

> "If you were at your job for three years instead of two, then your
> loan would be accepted."

Each of these explanations may be valid, i.e. truthful, however each
of them may be harder for Alice to act on.

# Properties of good contrastive examples

The above example motivates a discussion of the goodness of individual
contrastive examples. Verma *et al.* {% cite verma2020counterfactual
-A %} conducted a survey of contrastive examples and found five properties
that good contrastive examples exhibit.

## 1. Validity

A contrastive example should be truthful, or valid. If Alice goes to
her boss and asks for a raise of $10,000 and they give it to her, she
should now qualify for the loan. If she would not qualify for the loan
(and the bank's policies hadn't changed), then the banker would have
lied to her. We need valid contrastive examples to empower those
receiving them and not waste their time.

## 2. Actionability

In the above example, each of the actions that Alice can take, either
getting a raise of $10,000 or staying at her job for another year, may
be more or less doable for her. If Alice is currently making $200,000
per year, it would be easier for her to get a raise of $10,000 than if
she were making $20,000 per year. Further, some explanations (albeit
illegal ones) may even ask that she change her race or gender. These
would clearly be in-actionable for Alice. Good contrastive examples
provide feasible paths to changing the situation, while better ones
take into account an individual's preferences on actionability.

## 3. Sparsity

Suppose Alice is given two contrastive examples:

> Make $10,000 more per year

> Make $3,000 more per year, live in this neighborhood, be at your job
> for six more months, serve in the military, ...

As humans, it is difficult to handle more than a set number of things
at a time and so a contrastive example that changes a smaller number
of features will be easier to create a mental model around.

## 4. Data (Manifold) closeness

Up until this point, I have been succesful in my goal of not
introducing an automated system into this discussion. However, I
struggle to come up with a good human-centered explanation for this
property. I now break from using purely human actors in the
explanation and start to use an automated system.

Suppose now the banker has gotten tired of accepting and rejecting all
of these loan applications and wants to automate the process. They
decide to build an automated system and use their past accepted and
rejected applications in the training process.  The banker uses 90% of
their previous applications to train the system and the remaining 10%
of their previous applications to evaluate it.  After training, the
system performs relatively well on the test set with 99% accuracy.

Now comes the problem. Suppose Alice is in a peculiar financial
situation, such that none of the data in the training set comes close
to her situation. How can we expect the system to correctly decide if
her loan should be accepted? Simply put, we can't without knowing more
about the system, especially because machine learning models
inherently do not extrapolate well. In the same way, if a contrastive
explanation would result in features outside of the scope of the
training data, then we can't really know whether the contrastive
example is itself valid.

## 5. Causality

Finally, features of a person's financial situation are rarely
independent. Your salary dictates where you can live, what types of
bank accounts you have open, etc. These causal relations need to be
accounted for when providing an explanation. For example, suppose
Alice got the raise, but she moved positions within her company to do
so. Clearly her salary is directly causally related to her position in
the company, and so we would hope that achieving a higher position in
the company would not invalidate the banker's explanation.

# Wrapup

Thank you for reading my first post! I hope that this blog post has
been helpful in explaining what contrastive explanations are and what
are some properties that good contrastive examples exhibit.

{% bibliography --cited %}
