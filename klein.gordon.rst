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
This description goes through the implementation of a solver for the above described Klein-Gordon equation step-by-step.

First, the DeepXDE, NumPy (``np``), and TensorFlow (``tf``) modules are imported.

.. code-block:: python

    import deepxde as dde
    import numpy as np
    from deepxde.backend import tf
    
We begin by defining computational geometries. We can use a built-in class ``Interval`` and ``TimeDomain`` and we combine both the domains using ``GeometryXTime`` as follows

.. code-block:: python

    geom = dde.geometry.Interval(-1, 1)
    timedomain = dde.geometry.TimeDomain(0, 10)
    geomtime = dde.geometry.GeometryXTime(geom, timedomain)
    
Next, we express the PDE residual of the Klein-Gordon equation.

.. code-block:: python

    alpha, beta, gamma, k = -1, 0, 1, 2
    def pde(x, y):
        dy_tt = dde.grad.hessian(y, x, i=1, j=1)
        dy_xx = dde.grad.hessian(y, x, i=0, j=0)
        x, t = x[:, 0:1], x[:, 1:2]
        return dy_tt + alpha * dy_xx + beta * y + gamma * (y**k) + x * tf.cos(t) - (x**2) * (tf.cos(t)**2)
        
The first argument to ``pde`` is 2-dimensional vector where the first component(``x[:,0:1]``) is :math:`x`-coordinate and the second component (``x[:,1:2]``) is the :math:`t`-coordinate. The second argument is the network output, i.e., the solution :math:`y(x, t)`.

Start here.
