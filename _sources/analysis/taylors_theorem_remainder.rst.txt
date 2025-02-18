Taylor's Theorem with Remainder
================================


We discuss a version of Taylor's theorem that uses only first order partial derivatives.

.. admonition:: Theorem

	Let :math:`g:\mathbb{R}^n \to \mathbb{R}` be differentiable on an open set :math:`U \subset \mathbb{R}^n` starshaped with respect to a point :math:`a \in U`.
	There exists a :math:`t_0` with :math:`0 < t_0 < 1` such that 

	.. math::
		g(x) = g(a) + \sum _{i=1}^n \frac {\partial g}{\partial x_i} (a + t_0(x-a)) (x^i - a^i).

