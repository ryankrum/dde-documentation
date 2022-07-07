Klein-Gordon equation
================

Problem setup
--------------
We will solve a Klein-Gordon equation:

.. math:: \frac{\partial^2y}{\partial t^2} + \Alpha \frac{\partial^2y}{\partial x^2} + \Beta y + \Gamma y^k = -x\cos(t) + x^2\cos^2(t), \qquad x \in [-1, 1], \quad t \in [0, 10]

with initial conditions

.. math:: y(x, 0) = x, \frac{\partial y}{\partial t}(x, 0) = 0

and the Dirichlet boundary conditions

.. math:: y(-1, t) = -\cos(t), y(1, t) = \cos(t).

The reference solution is :math:`y(x, t) = x\cos(t)`.

Implementation
--------------

