On the Riemann-Zeta function
==============================

The zeta function is defined as 

.. math::

	\zeta(s) = \sum_{n \geq 1} n^{-s},\quad \sigma = \Re(s) > 1.


.. admonition:: Proposition

	On :math:`\sigma` > 1 we have

	.. math::

		\zeta(s) = \frac{s}{s-1} + s\int_1^{\infty} \frac{\{x\}}{x^{s+1}}\,dx

	where the integral on the right hand side is an analytic function for :math:`\sigma > 0`.

This yields an analytic continuation for :math:`\zeta(s)` for the region :math:`\sigma > 0,\, s \neq 1`. This also shows
:math:`\zeta(s)` has a simple pole at :math:`s=1` of residue :math:`\lim_{s\to 1^+}\zeta(s) = 1`.

Apply :ref:`this formula <abel-partial-summation-series>` with :math:`a_n=1` to obtain that, 
for :math:`\sigma > 1`, we have

.. math::

	\begin{align}
		\zeta(s) &= s \int_1^\infty \frac{[x]}{x^{s+1}}\,dx \\
		&= s \int_1^\infty x^{-s}\,dx - s \int_1^\infty \frac{\{x\}}{x^{s+1}}\,dx \\
		&= \frac{s}{s-1} - s \int_1^\infty \frac{\{x\}}{x^{s+1}}\,dx .
	\end{align}

where we used that :math:`[x] = x - \{ x \}`. To see that the integral is analytic on :math:`\sigma > 0` one may apply 
the Cauchy-Riemann equations, applying Leibniz rule to differentiate with respect to :math:`\sigma` and :math:`t`.
Notice that the integrand is discontinuous only on integers, so Riemann integrability applies.
One might also apply :ref:`Morera's Theorem <morera>` with Fubini.

.. admonition:: Proposition

	.. math::

		D(\Lambda, s) = \sum_{n \geq 1} \frac{\Lambda(n)}{n^s} = -\frac{\zeta '}{\zeta}(s)\,ds

	where :math:`-\zeta'(s) = \sum_{n \geq 1} (\log n) n^{-s}`. 

We write the proposition in the form

.. math::

	D(\Lambda, s) D(1, s) = -\zeta'(s)

and proving this identity amounts to showing that :math:`\log n = \sum_{d|n} \Lambda (d)` for 
each :math:`n`. This is straightforward,

.. math::
	\sum_{d|n} \Lambda (d) = \sum_{p^a|n} \log p = \sum_{p|n} e \log p = \log p_1^{e_1} \ldots p_n^{e_n} = \log n

where summations are over prime powers or distinct primes dividing :math:`n` :math:`\blacksquare`.
