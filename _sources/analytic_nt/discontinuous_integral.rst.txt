A Discontinuous Integral
=========================

Let :math:`f:\mathbb{C} \to \mathbb{C}`. For :math:`c > 0`, we abbreviate the integral 

.. math:: 
	\int_{c - i\infty}^{c + i\infty} f(s)\,ds = \int_{(c)} f(s)\,ds

and interpret it in the 'principal value' sense. That is, look at 
:math:`\lim_{R \to \infty} \int_{c - iR}^{c+iR}` 

.. admonition:: Theorem

	Define :math:`\delta(x)` to be the discontinous function 

	.. math::

		\delta(x) = 
		\begin{cases}
		0 & 0 < x < 1 \\
		\frac{1}{2} & x = 1 \\
		1 & x > 1.
		\end{cases}
	
	Then

	.. math::
		\delta(x) = \frac{1}{2\pi i} \int_{(c)} \frac{x^s}{s}\,ds.

The case :math:`x=1` is an easy exercise in contour integration and can be handled directly. We have

.. math::
	\int_{c-iR}^{c+iR} \frac{ds}{s} = 2ic \int_0^R \frac{dt}{c^2+t^2}

which can be handled with the arctangent formula and the fundamental theorem of calculus.

For the other two cases, one way to handle them is to integrate over semicircle contours centered
at :math:`c>0` which we briefly discuss here.

For :math:`0<x<1` consider the contour given by a semicircle of radius :math:`R` centred at :math:`c>0`, not containing the origin,
and positively oriented (clock-wise). It has the vertical line connected by :math:`c-iR` and :math:`c+iR`. 

By Cauchy's integral formula, integrating :math:`f(s)=\frac{x^s}{s}` over this contour yields
a result of 0. On the other hand, it is easy by direct computation that the arc part of the contribution is zero as well, hence the
vertical line also contributes zero. What follows is some details to verify this computation.

Let :math:`S_R` denote the semicircle part of this contour. It is parameterized by :math:`z(t) = c + Re^{-it}` for :math:`t \in [-\pi/2, \pi/2]`.
Computing directly, we can obtain

.. math::
	\big\lvert \int_{S_R} \frac{x^s}{s}\,ds \big\rvert \leq x^c \int_{-\pi/2}^{\pi/2} x^{R \cos t}\,dt.

The integral on the right hand side is equivalent to :math:`\int_{0}^{\pi} x^{R \sin t}\,dt`. Break this integral into three parts, for
small :math:`\epsilon>0`,

.. math::
	\big{(}\int_0^{\epsilon} + \int_{\epsilon}^{\pi - \epsilon} + \int_{\pi - \epsilon}^{\pi}\big{)} x^{R \sin t}\,dt

The middle integral is bounded by :math:`(\pi - 2\epsilon)x^{R \sin \epsilon}`, and the other two integrals are each bounded by :math:`\epsilon` since
the integrand is at most 1. Letting :math:`R` tend to infinity shows that the integral converges to :math:`2\epsilon`. Since :math:`\epsilon` is arbitrary,
we see that overall the integral converges to :math:`0`.


The case when :math:`x>1` is very similar. Integrate again over the positively oriented contour consisting of the vertical line joining :math:`c-iR` to :math:`c+iR` and
the semicircle radius :math:`R` centred at :math:`c` enclosing the origin. By Cauchy's integral formula, the integral of the contour is :math:`x^0=1`. The
semicircle part of this contour is paramterized by :math:`z(t) = c + Re^{it}` for :math:`t \in [\pi/2, 3\pi/2]`. We show the semicircle part of the contour vanishes
in the limit by direct computation, 

.. math::
	\big\lvert \int_{S_R} \frac{x^s}{s}\,ds \big\vert \leq x^c\int_{\pi/2}^{3\pi/2} x^{R \cos t}\,dt.

The integral on the right hand side is equivalent to :math:`\int_{0}^{\pi} x^{-R \sin t}\,dt` and we analyze in this form instead. Split this integral
into three parts, the same way as the previous case. The middle integral is bounded above by :math:`(\pi - 2\epsilon)x^{-R \sin \epsilon}`, and the
other two integrals at most :math:`\epsilon`. Letting :math:`\epsilon` and :math:`R` tend to zero shows that 
the entire integral vanishes in the limit :math:`\blacksquare`. 

Another approach of integrating this function involves rectangular contours instead of semi circle arcs. For example, when :math:`0 < x < 1` our contour is the positively oriented
rectangle with corners at :math:`c-iR, c+iR, \sigma+iR, \sigma-iR`, and we let :math:`\sigma` tend to :math:`\infty`. This approach we won't show, but it can
be found in a few classical texts (like the one by Davenport I think). The advantage of this approach is that it can be used to obtain some approximations that will be helpful later on.

.. admonition:: Theorem

	We have, for :math:`x,c,R>0`,

	.. math::

		|I(x,R) - \delta(x)| < 
		\begin{cases}
			x^c \min (1, \frac{1}{R | \log x |}) & x \neq 1\\
			c/R & x = 1
		\end{cases}

This discontinuous integral can be used to extract coefficients from a Dirichlet series in the following sense. It will be a key result in proving the Prime Number Theorem.

.. admonition:: Theorem

	Suppose that 

	.. math::
		f(s) = \sum_{n \geq 1} \frac{a_n}{n^s}

	is a Dirichlet series absolutely convergent in :math:`\sigma > c - \epsilon`. Then for non-integer :math:`x` we have

	.. math::
		\sum_{n < x} a_n = \frac{1}{2 \pi i} \int_{(c)} f(s) \frac{x^s}{s}\,ds.

.. hint::
	We often write :math:`s = \sigma + it`, denoting :math:`\sigma,t` as the real and imginary parts of :math:`s`.

The assumptions are enough to show that :math:`f(s)` converges uniformly on the half plane :math:`\sigma > c - \epsilon`, which
justifies term by term integration in the following,

.. math::

	\begin{align}
	\frac{1}{2 \pi i} \int_{c-iR}^{c+iR} f(s) \frac{x^s}{s}\,ds &= \frac{1}{2 \pi i} \int_{c-iR}^{c+iR} \sum_{n \geq 1} \frac{a_n}{n^s} \frac{x^s}{s} ds \\
	&= \frac{1}{2 \pi i} \sum_{n \geq 1} \frac{a_n}{n^s} \int_{c-iR}^{c+iR} \frac{x^s}{s}\,ds \\
	&= \sum_{n \geq 1} \frac{a_n}{n^s} I(x, R)
	\end{align}

where we use notation as in the previous theorem. Viewing the summands as a function of :math:`R`, notice that the summation converges uniformly 
on :math:`R \geq 0` (can use the previous theorem to bound :math:`I(x,R)` by :math:`x^c`) so that we may take the limit as :math:`R \to \infty` and move the limit inside the sum
(this can be justified in a few ways, one being the dominated convergence theorem, viewing :math:`R` as taking values in a sequence :math:`1,2,\ldots`). We then have

.. math::

	\begin{align}
	\sum_{n \geq 1} \frac{a_n}{n^s} \delta(x) &= \sum_{n \geq 1} a_n \delta(x/n) \\
	&= \sum_{n < x} a_n
	\end{align}

as required :math:`\blacksquare`.

