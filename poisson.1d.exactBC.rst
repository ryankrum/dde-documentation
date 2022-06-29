Poisson equation in 1D with hard boundary conditions
================

Problem Setup
--------------
We will solve a Poisson equation:

.. math:: -\Delta u = \sum{i=1}^{4}[i\sin(ix)] + 8\sin(8x), \qquad x \in [0, \pi]

With the Dirichlet boundary conditions:

.. math:: u(x = 0) = 0, u(x = \pi) = \pi

The exact solution is :math:`u(x) = x + \sum{i=1}^{4}[\frac{\sin(ix)}{i}] + \frac{\sin(8x)}{8}`
