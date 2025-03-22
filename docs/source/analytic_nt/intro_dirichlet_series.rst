Primer on Dirichlet Series
===========================

++++++++++++++++++++++++
Arithmetic Functions
++++++++++++++++++++++++

Arithmetic functions have the form :math:`f: \mathbb{N} \to \mathbb{C}`. 
They are additive if :math:`f(m+n)=f(m)+f(n)` for coprime :math:`m,n` and
completely additive if the rule holds for all :math:`m,n`. Same rule for
multiplicative but for the product :math:`mn`.


:math:`\nu(n)` is the distinct number of prime divisors. 
:math:`\Omega(n)` is the number of prime divisors not necessarily distinct.


:math:`d(n) = \sum_{d|n} n` is the divisor function.
can be shown that :math:`d(n) = O(n^{\epsilon})` for any :math:`\epsilon>0`. 
Showing :math:`d(n) = O(\sqrt{n})` is easier, just notice that for any pair of divisors
of :math:`n`, one of the partners is at most :math:`\sqrt{n}`.

Mobius function :math:`\mu(n)` has the rule :math:`\mu(1)=1` and 

.. math::
	
	\mu(n) = \begin{cases} 
		(-1)^{\nu(n)} & \text{n squarefree} \\
		0 & \text{otherwise.}
	\end{cases}

It can be shown rather easily that :math:`\sum_{d|n} \mu(d) = 0` with the exception that
:math:`\mu(1)=1`. This can be applied to show the Mobius inversion formula,

.. math::
	f(n) = \sum_{d|n} g(n) \quad \forall n  \iff g(n) = \sum_{d|n}\mu(d)f(n/d) \quad \forall n.


Euler phi :math:`\phi(n)` is defined by 

.. math::

	\phi(n) = n \prod_{p|n}\bigg( 1 - \frac{1}{p} \bigg) = |\mathbb{Z}_n^*|

where the product is over distinct prime divisors.I like the probabilistic 
interpretation of this function gained by writing

.. math::
	
	\frac{\phi(n)}{n} = \prod_{p|n} \bigg( 1 - \frac{1}{p} \bigg)


so that probability of an integer in :math:`1,\ldots,n` being prime to :math:`n` is the same probability that
it was not divisible by any prime :math:`p` in the factorization of :math:`n`.

The von Mangoldt function :math:`\Lambda(p^a) = \log p` for prime powers, and :math:`0` otherwise.
It is not additive or multiplicative but will be important in the Prime Number Theorem.



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
	
	D(f,s) = \prod_p \sum_{\nu >= 0} \bigg( f(p^{\nu}) p^{-\nu s} \bigg).

We also have some identities to handle explicitly. Define the Riemann-zeta function as
:math:`\zeta(s) = \sum_{n \geq 1} n^{-s} = D(1,s)`. Then

.. math::

	\zeta(s) = D(1,s) \sum_{n \geq 1} = \frac{1}{n^s}.


This can be proved from that identity involving :math:`\sum_{d|n} \mu(d)` we saw earlier. Another
identity of interest is this proposition.

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

