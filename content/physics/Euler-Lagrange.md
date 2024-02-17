---
title: 'Euler-Lagrange equations: A derivation'
author: 'Diptanuj Sarkar'
date: '2024-01-13'
tags: ['test']
math: true
description: 'This is me trying out KaTeX on the site'
---

# Introduction

We start off by taking as a prototype the simple Newtonian scheme of a point particle of mass $m$ moving along the x-axis under a potential field $V(x)$.

According to Newton's Second Law of motion,
$$
m \frac{d^2 x}{dt^2} = - \frac{dV}{dx}
$$

If we are given the position and the velocity of this particle at some initial time, i.e. $x(t_i)$ and $\dot{x}(t_i)$, then it is possible for us to compute the classical trajectory of the particle $x_{cl}(t)$ as follows
$$
x_{cl}(t+\Delta t) = x(t_i) + \dot{x}(t_i) \Delta t
$$

We can keep following the same iteration scheme to calculate the position at $t+2\Delta t$, $t+3\Delta t$, and so on.

Since the equation of motion is second order in time, there are two pieces of data (namely, $x(t_i)$ and $\dot{x}(t_i)$) that are required to specify a unique $x_{cl}(t)$. An equivalent way to doing the same thing is to specify an initial point $(x_i,t_i)$ and a final point $(x_f,t_f)$ (Why?).

In the Lagrangian formalism, the same problem is posed in this way: **Given the initial and the final point, what is it that distinguishes the actual classical trajectory joining these point from the infinite other trajectories that join these two points?**
The answer to this lies in the following points:

- Define a function $\mathbf{L}$, called the **Lagrangian** which is given by,
$$
\mathbf{L} = T - V
$$
$T$ and $V$ being the kinetic and potential energies of the particle.
Thus, $\mathbf{L} = \mathbf{L}(x,\dot{x})$. Note that we assume the absence of $t$ dependence by considering a potential field that is not time-dependent.

- For each path $x(t)$ connecting $(x_i,t_i)$ and $(x_f,t_f)$, calculate the **action**, defined by,
$$
S[x(t)] = \int_{t_i}^{t_f} \mathbf{L}(x,\dot{x}) dt
$$
There are square brackets because we want to remember that the argument of S is the **entire path** or the **entire function** $x(t)$, not just the value of the function at some time. $S$ is thus also called a **functional**.

- **Principle of Least Action**: The classical path is the one on which $S$ is a _minimum_ (Actually, it is only required that it be an extremum. The name is merely customary).

Now, we verify whether this principle gives us back Newton's Second Law.

## A multivariable detour

Since $S$ is a function of some other function $x(t)$, it is really just a multivariable function of $n$ variables as $n\rightarrow \infty$.
This is due to the fact that the function $x(t)$ actually specifies an infinite number of values $x(t_i), \dots , x(t) , \dots , x(t_f)$ - one for each instant in time $t$ in the specified interval.
We will deal with the entire minimum (actually, extremum) situation of the action by generalising how we deal with it in n variables.
Let us define a function,
$$
f = f(x_1, \dots , x_n) = f(\vec{x})
$$
The minimum of this function, say, $\vec{x^0}$ is characterised by the fact that if we move away from it by a small amount $\vec{\eta}$ in any direction, the first order change in $f$ vanishes.
Using the Taylor expansion,
$$
f(\vec{x^0}+\vec{\eta}) = f(\vec{x^0}) + \sum_{i=1}^{n} \frac{\partial f}{\partial x_i} \bigg\rvert_{\vec{x^0}} \eta_i + \text{ higher order terms in } \eta
$$
then, we get,
$$
\delta f^{(1)} = \sum_{i=1}^{n} \frac{\partial f}{\partial x_i} \bigg\rvert_{\vec{x^0}} \eta_i = 0
$$
as **the first order change vanishes**.
From this, we can see that if we choose $\vec{\eta}$ such that it is along the ith direction, **every first order partial derivative of the function vanishes at** $\vec{x^0}$.
$$
\frac{\partial f}{\partial x_i} \bigg\rvert_{\vec{x^0}} = 0 \quad , i = 1,\dots , n
$$

## Coming back to the action
We now use the property that we deduced to arrive at the extremum of $S$. We assume that $x_{cl}(t)$ is the path of least action (as per the principle), and that $x_{cl}(t) + \eta(t)$ is a "nearby" path.
As all the paths have to coincide at the initial and the final points, we get the condition,
$$
\eta(t_i) = \eta(t_f) = 0
$$
So now we get to the main attraction,
$$
S[x_{cl}(t) + \eta(t)] = \int_{t_i}^{t_f} \mathbf{L} (x_{cl}(t) + \eta(t),\dot{x}_{cl}(t) + \dot{\eta}(t)) dt
$$

Now, expanding the Lagrangian to its Taylor series expression,

$$
\Rightarrow S[x_{cl}(t) + \eta(t)] = \int_{t_i}^{t_f} \bigg[ \mathbf{L} ( x_{cl}(t), \dot{x}_{cl}(t) ) + \frac{\partial \mathbf{L}}{\partial x(t)} \bigg \vert _{x _{cl} } \cdot \eta(t) + \frac{\partial \mathbf{L}}{\partial \dot{x}(t)} \bigg \vert _{x _{cl} } \cdot \dot{\eta}(t) + \cdots \bigg] dt
$$

$$
\Rightarrow S[x_{cl}(t) + \eta(t)] = S[x_{cl}(t)] + \delta S^{(1)} + \text{ higher order terms }
$$
Since this is the case with infinite variables, the sum involving the first order partial derivatives of the action has been converted into an integral.
Using the fact that we deduced earlier regarding the first order change going to zero, we can say,
$$
0 = \delta S^{(1)} = \bigg[ \frac{\partial \mathbf{L}}{\partial x(t)} \bigg \vert _{x _{cl} } \cdot \eta(t) + \frac{\partial \mathbf{L}}{\partial \dot{x}(t)} \bigg \vert _{x _{cl} } \cdot \dot{\eta}(t) \bigg] dt
$$
If we integrate the second term by parts with the partial derivative as the first function and the $\dot{\eta}$ term as the second function (Why? It has $\dot{\eta}(t)$, and we know that $\eta$ cancels out at the ends) we get:
$$
\frac{\partial \mathbf{L}}{\partial \dot{x}(t)} \bigg \vert _{x _{cl} } \cdot \eta(t) \bigg \vert _{t_i}^{t_f} - \int _{t_i} ^{t_f} \bigg[ \frac{d}{dt} \frac{\partial \mathbf{L}}{\partial \dot{x}(t)} \bigg] _{x _{cl} } \cdot \eta(t) dt
$$
As mentioned before, the first term here vanishes.
So, we get:
$$
0 = \delta S^{(1)} = \int _{t_i} ^{t_f} \bigg[ \frac{\partial \mathbf{L}}{\partial x(t)} - \frac{d}{dt} \frac{\partial \mathbf{L}}{\partial \dot{x}(t)} \bigg] _{ x _{cl} } \cdot \eta(t) dt
$$
Here, the integral and the stuff inside the bracket acts like the infinite analogue of the sum of all the first order partial derivatives of the multivariable function, i.e. the discrete variable $\eta$ is replaced by $\eta(t)$, the sum over $i$ is replaced by the integral over &t&, and $\frac{\partial f}{\partial x_i}$ is replaced by $\frac{\partial \mathbf{L}}{\partial x(t)} - \frac{d}{dt} \frac{\partial \mathbf{L}}{\partial \dot{x}(t)}$.
Since $\eta(t)$ is arbitrary, we may extract the analogue of the finite case:
$$
\bigg[ \frac{\partial \mathbf{L}}{\partial x(t)} - \frac{d}{dt} \frac{\partial \mathbf{L}}{\partial \dot{x}(t)} \bigg] _{x _{cl} (t) } = 0 \quad \text{ for } t_i \leq t \leq t_f
$$
This is the famous **Euler Lagrange equation**.

## Does this give back NLM?
If we feed into the equation,
$$
\mathbf{L} = T - V
$$

$$
T = \frac{1}{2} m \dot{x} ^2
$$

$$
V = V(x)
$$

Then we get,
$$
\frac{\partial \mathbf{L}}{\partial \dot{x}} = \frac{\partial T}{\partial \dot{x}} = m \dot{x}
$$
and
$$
\frac{\partial \mathbf{L}}{\partial x} = - \frac{\partial V}{\partial x}
$$
and so the Euler-Lagrange equation becomes Newton's Second Law for this case,
$$
\frac{d}{dt} (m \dot{x}) = - \frac{\partial V}{\partial x}
$$
_and we are done!_

![doggo](/images/doggo.png)
