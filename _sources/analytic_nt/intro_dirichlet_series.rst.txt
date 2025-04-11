Primer on Dirichlet Series
===========================

++++++++++++++++++++++++
Arithmetic Functions
++++++++++++++++++++++++

Arithmetic functions have the form :math:`f: \mathbb{N} \to \mathbb{C}`. 
They are additive if :math:`f(m+n)=f(m)+f(n)` for coprime :math:`m,n` and
completely additive if the rule holds for all :math:`m,n`. Same rule for
multiplicative but for the product :math:`mn`.


:math:`\nu(n)` is the distinct number of prime divisors. This is completely multiplicative.


:math:`\Omega(n)` is the number of prime divisors not necessarily distinct. Also multiplicative.


:math:`d(n) = \sum_{d|n} n` is the divisor function. This is multiplicative, since
any divisor of :math:`mn` can be split into two relatively prime parts that are divisors for 
:math:`m` and :math:`n` alone. An interesting approximation is this that,

.. admonition:: Proposition

	for any :math:`\epsilon>0` we have :math:`d(n) = O(n^{\epsilon})`.

This result can be improved, but we don't want to go too far.

The case that :math:`d(n) = O(\sqrt{n})` is pretty easy, just notice that for any
pair whose product is :math:`n`, one of the partners is at most :math:`\sqrt{n}`.


To tackle the general case we can 'localize' the problem to the prime divisors of :math:`n = p_1^{a_1}\ldots p_k^{a_k}`.
We fix an :math:`\epsilon>0` and a prime :math:`p=p_j` dividing :math:`n` with power :math:`a=a_j`. We will find a
constant :math:`C>0` such that

.. math::

	\frac{d(p)}{p^{a \epsilon}} = \frac{a+1}{p^{a \epsilon}} \leq C

where the constant :math:`C` depends only on :math:`\epsilon`. It suffices to do this since :math:`d` is multiplicative,
we can later take the product of all such :math:`C` to bound :math:`d(n)/n^{\epsilon}`.

We split our work into cases. If :math:`p > e^{1/\epsilon}` then :math:`p^{\epsilon} > e`, so

.. math::

	\frac{a+1}{p^{a \epsilon}} \leq \bigg( \frac{e}{p^\epsilon} \bigg)^a  \leq 1

where we used that :math:`e^a \geq a+1` using the Taylor series expansion of :math:`e^x`. For all the other,
smaller primes, we have 

.. math::

	\frac{a+1}{p^{a \epsilon}} \leq \frac{a+1}{2^{a \epsilon}} \to 0

as :math:`a \to \infty`. Thus we may find a positive constant that bounds this expression uniformly for all :math:`a \geq 0`. We set our
constant :math:`C` to be the maximum of this number and 1 :math:`\blacksquare`. 

:math:`\mu(n)` is the Mobius function. It has :math:`\mu(1)=1` and 

.. math::
	
	\mu(n) = \begin{cases} 
		(-1)^{\nu(n)} & \text{n squarefree} \\
		0 & \text{otherwise.}
	\end{cases}


It can be shown rather easily that :math:`\sum_{d|n} \mu(d) = 0` with the exception that
:math:`\mu(1)=1`. This can be applied to show the Mobius inversion formula,

.. admonition:: Theorem

	If :math:`f,g` are arithmetic functions then 

	.. math::
		f(n) = \sum_{d|n} g(n) \quad \forall n  \iff g(n) = \sum_{d|n}\mu(d)f(n/d) \quad \forall n.


Euler phi :math:`\phi(n)` is defined by 

.. math::

	\phi(n) = n \prod_{p|n}\bigg( 1 - \frac{1}{p} \bigg) = |\mathbb{Z}_n^*|

where the product is over distinct prime divisors. I like the probabilistic 
interpretation of this function gained by writing

.. math::
	
	\frac{\phi(n)}{n} = \prod_{p|n} \bigg( 1 - \frac{1}{p} \bigg)


so that probability of an integer in :math:`1,\ldots,n` being prime to :math:`n` is the same probability that
it was not divisible by any prime :math:`p` in the factorization of :math:`n`.

The von Mangoldt function :math:`\Lambda(p^a) = \log p` for prime powers, and :math:`0` otherwise.
It is not additive or multiplicative but will be important in the Prime Number Theorem.

Partial summation is a useful technique when dealing with arithmetic functions and series.

.. _abel-partial-summation:

.. admonition:: Theorem

	
	Let :math:`a_n` be a sequence of complex numbers and :math:`f` be :math:`C^1` on :math:`[1,x]`. 
	Define :math:`A(x) = \sum_{n \leq x} a_n`. Then we have

	.. math::

		\sum_{n \leq x} a_n f(n) = A(x)f(x) + \int_1^x A(t)f'(t)\,dt.


++++++++++++++++++++++++
Formal Dirichlet Series
++++++++++++++++++++++++
The formal Dirichlet series for an arithmetic function :math:`f` is given by 

.. math::

	D(f,s) = \sum_{n \geq 1} f(n)n^{-s}.

Sum is defined in usual way. Product is defined as

.. math::

	D(f,s)D(g,s) = \sum_{n \geq 1} h(n)n^{-s} = \sum_{n \geq 1}\sum_{de=n}f(d)g(e)n^{-s}.


When :math:`f` is multiplicative notice that unique prime factorization yields

.. math::
	
	D(f,s) = \prod_p \sum_{\nu \geq 0} \bigg( f(p^{\nu}) p^{-\nu s} \bigg).


An important series is the Riemann-zeta function,

.. math::

	\zeta(s) = \sum_{n \geq 1} n^{-s} = D(1,s) = \prod_p \frac{1}{1 - p^{-s}}

Then 

.. math::


	D(\mu, s) = \frac{1}{\zeta(s)}.


This can be proved from that identity involving :math:`\sum_{d|n} \mu(d)` we saw earlier. 

Now we discuss analyticity of Dirichlet functions. Note that in this context 
we use :math:`s` to denote complex variables and often write :math:`s = \sigma + it`.

.. _abel-partial-summation-series:

.. admonition:: Theorem 

	In the setting of partial summation, suppose that for :math:`A(x) = O(x^{\delta})`,	

	For :math:`\Re(s)> \delta` we have

	.. math::

		\sum_{n \geq 1} \frac{a_n}{n^s} = s \int_1^\infty \frac{A(t)}{t^{s+1}}\,dt.

Simply apply the partial summation theorem with :math:`f(x) = x^{-s}` and we get

.. math::

	\sum_{n \leq x} \frac{a_n}{n^s} = A(x)x^{-s} + s \int_1^x \frac{A(t)}{t^{s+1}}\,dt.

Taking :math:`x \to \infty` yields the desired result. Note that the :math:`A(x)x^{-s}=O(x^{\delta - \Re(s)})` 
which will vanish in the limit. Here we have :math:`f: \mathbb{R} \to \mathbb{C}`, so
one might wonder how we got the above identity. Simply write :math:`f(s) = u(s) + i v(s)`, 
apply partial summation for :math:`u,v` separately, and then add them up :math:`\blacksquare`.



