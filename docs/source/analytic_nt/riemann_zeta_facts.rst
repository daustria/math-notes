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
:math:`\zeta(s)` has a simple pole at :math:`s=1` of residue :math:`\lim_{s\to 1^+}(s-1)\zeta(s) = 1`. 
Also with this formula one may see that :math:`\zeta(s) \neq 0` on :math:`\sigma = 1`, for example by 
noting that the real part is positive. 

Apply :ref:`this formula <abel-partial-summation-series>` with :math:`a_n=1` to obtain that, 
for :math:`\sigma > 1`, we have

.. math::

	\begin{align}
		\zeta(s) &= s \int_1^\infty \frac{[x]}{x^{s+1}}\,dx \\
		&= s \int_1^\infty x^{-s}\,dx - s \int_1^\infty \frac{\{x\}}{x^{s+1}}\,dx \\
		&= \frac{s}{s-1} - s \int_1^\infty \frac{\{x\}}{x^{s+1}}\,dx .
	\end{align}

where we used that :math:`[x] = x - \{ x \}`. To see that the integral is analytic on :math:`\sigma > 0` one may apply 
the Cauchy-Riemann equations, applying Leibniz rule to differentiate the real and imaginary parts
with respect to :math:`\sigma` and :math:`t`. Notice that the integrand is discontinuous only on integers, so Riemann integrability applies.
One might also apply :ref:`Morera's Theorem <morera>` with Fubini :math:`\blacksquare`. 

.. admonition:: Proposition

	:math:`\zeta(s) \neq 0` for :math:`\sigma = \Re(s) \geq 1`.

The proof for :math:`\sigma > 1` is an easy application of the triangle inequality, so we discuss only :math:`\sigma = 1, s \neq 1`.

.. admonition:: Lemma

	For :math:`\sigma > 1, t \in \mathbb{R}`, we have

	.. math::

		\Re \log \zeta(\sigma + it) = \sum_{n \geq 2} \frac{\Lambda(n)}{n^\sigma \log n} \cos (t \log n).


We have, for :math:`s = \sigma + it`,

.. math::

	\log \zeta(s) = \log \prod_p ( 1 - p^{-s} )^{-1} = \sum_p -\log (1-p^{-s})

Where the index is over unique primes. Now we apply the Taylor series identity 

.. math::

	-\log(1-x) = \sum_{n \geq 1} \frac{x^n}{n}

to obtain

.. math::

	\log \zeta(s) = \sum_p \sum_{n \geq 1} \frac{1}{np^{ns}}.

Notice this summation is absolutely convergent because :math:`|\log \zeta(s)| \leq \log \zeta(\sigma) < \infty`.
So instead we can write the summation over prime powers,

.. math::

	\log \zeta(s) = \sum_{x=p^n, n \geq 1} \frac{\log p}{\log x} \frac{1}{x^{ns}} = \sum_{n \geq 2} \frac{\Lambda(n)}{n^s \log n}.

Note the von Mangoldt function :math:`\Lambda(n)` vanishes on non-prime powers, allowing us to write the summation over all :math:`n \geq 2`.
Comparing real parts of this identity completes the proof :math:`\blacksquare`.

.. admonition:: Lemma

	For :math:`\sigma > 1, t \in \mathbb{R}` we have

	.. math::

		|\zeta(\sigma)^3 \zeta(\sigma + it)^4 \zeta(\sigma + 2it)| \geq 1.

	
	Consequently, :math:`\zeta(1+it) \neq 0` for any :math:`t` by a simple continuity argument.

Taking the logarithm of both sides, it suffices to prove

.. math::

	\Re (3 \log \zeta(\sigma) + 4 \log \zeta(\sigma + it) + \log \zeta(\sigma + 2it)) \geq 0.

Using the previous lemma, this reads as

.. math::

	\sum_{n \geq 2} \frac{\Lambda(n)}{n^s \log n} (3 + 4 \cos (t \log n) + \cos (2t \log n)) \geq 0.

Notice that the term on the left is positive, so we would be done if the function :math:`3 + 4 \cos x + \cos 2x`
is non-negative. This can be proven easily with calculus. We find the minimum by
looking at where the derivative vanishes, 

.. math::

	-4 \sin x - 2 \sin 2x = 0 \iff -\sin x = \sin x \cos x \iff x = \pi + 2\pi \mathbb{Z}.

But at :math:`x = \pi`, we have :math:`4 \cos x + \cos 2x = -3`. Hence :math:`3 + 4 \cos x + \cos 2x \geq 0`.
This completes the proof of this lemma and also the proposition :math:`\blacksquare`.

.. admonition:: Proposition

	:math:`-\frac{\zeta'}{\zeta}(s)` is analytic on :math:`\sigma \geq 1` except for a simple pole at :math:`s=1` with residue :math:`1`.

By analytic continuation, both :math:`\zeta` and :math:`\zeta'` can be taken to be analytic on :math:`\sigma > 0, s \neq 1`.
Because :math:`\zeta(s) \neq 0` for :math:`\sigma \geq 1`, :math:`-\frac{\zeta'}{\zeta}(s)` is analytic on :math:`\sigma \geq 1, s \neq 1`.

Write :math:`\zeta(s)(s-1) = sf(s)` for :math:`f` analytic on :math:`\sigma > 0`. Differentiating both sides and 
rearranging yields

.. math::

	-(s-1)\frac{\zeta'}{\zeta}(s) = -\frac{f'(s)}{\zeta(s)} - \frac{f(s)}{\zeta(s)} + 1.

Now take :math:`\lim_{s \to 1^+}`, the right hand side resolves to 1 because :math:`\zeta(s)` blows up :math:`\blacksquare`.


.. admonition:: Proposition

	On :math:`\sigma > 1`, we have the following Dirichlet series representation,

	.. math::

		-\frac{\zeta '}{\zeta}(s) = D(\Lambda, s) = \sum_{n \geq 1} \frac{\Lambda(n)}{n^s}.

	where :math:`-\zeta'(s) = \sum_{n \geq 1} (\log n) n^{-s}`. 

We write the proposition in the form

.. math::

	D(\Lambda, s) D(1, s) = -\zeta'(s)


By absolute convergence on :math:`\sigma > 1`, the product on the left hand side converges to the Cauchy product,

.. math::

	\sum_{n \geq 1}\sum_{d|n} \frac{\Lambda(d)}{n^s}

It suffices to show that the coefficients of this Dirichlet series evalutes to :math:`\log n` 
for each :math:`n \geq 1`. This is straightforward,

.. math::
	\sum_{d|n} \Lambda (d) = \sum_{p^a|n} \log p = \sum_{p|n} e \log p = \log p_1^{e_1} \ldots p_n^{e_n} = \log n

where summations are over prime powers or distinct primes dividing :math:`n` :math:`\blacksquare`.
