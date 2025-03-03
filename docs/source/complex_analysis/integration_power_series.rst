Integration and Differentiability
===================================

.. warning::

	still largely a work in progress

Holomorphic or complex-differentiable functions are expressible as their Taylor series.

.. admonition:: Theorem
	
	Let :math:`f` be analytic in a disk :math:`|z-a|<R` centred at :math:`a`. Then the Taylor series :math:`T_a(z)` for :math:`f` centred at :math:`a`
	converges pointwise on this disk to :math:`f`. Namely, for each :math:`z` in this disk we have 

	.. math::

		T_a(z) := \sum_{n \geq 0} \frac{f^{(n)}(a)}{n!} (z-a)^n = f(z).

We will start from the Taylor series :math:`T_a(z)` and show it is equal to :math:`f(z)`. We will integrate over a circle centred
at :math:`a`, properly containing :math:`z`. By :ref:`Cauchy's integral formula <cauchy-integral-formula-general>`,

.. math::
	\begin{align}
	T_a(z) &=  \sum_{n \geq 0} \frac{f^{(n)}(a)}{n!} (z-a)^n \\
	&= \sum_{n \geq 0} \frac{1}{2 \pi i} \oint \frac{f(s)}{(s-a)^{n+1}} (z-a)^n ds \\
	&= \frac{1}{2 \pi i} \sum_{n \geq 0} \oint \frac{f(s)}{s-a} \bigg(\frac{z-a}{s-a}\bigg)^n ds.
	\end{align}

Notice that the series obtained from interchanging summation and integration is a geometric series, which converges uniformly
on the circle (:math:`|z-a|/|s-a| < 1` for :math:`s` in the circle). This justifies the interchange of operations. Continuing, we have

.. math::
	\begin{align}
	\frac{1}{2 \pi i} \oint \sum_{n \geq 0} \frac{f(s)}{s-a} \bigg(\frac{z-a}{s-a}\bigg)^n ds &= \frac{1}{2 \pi i} \oint \frac{f(s)}{s-a} \frac{1}{1 - \frac{z-a}{s-a}}ds  \\
	&= \frac{1}{2 \pi i} \oint \frac{f(s)}{s-z}\,dz \\
	&= f(z)
	\end{align}

as required :math:`\blacksquare`.
