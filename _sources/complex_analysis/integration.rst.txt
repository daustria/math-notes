Contour Integration
====================

A quick discussion on contour integrals and their light on holomorphic functions. 

.. note:: A domain :math:`D` will refer to an open connected subset of the complex plane. Functions will usually have the form
   :math:`f: D \to \mathbb{C}` for some domain D.

Our first theorem will connect the presence of an antiderivative with path independence and vanishing loop integrals.
In fact these are equivalent in some sense.

.. _antiderivative-path-ind-loop-vanish:

.. admonition:: Theorem

   Let :math:`f`  be continuous in a domain D. The following are equivalent:

   #. :math:`f` has an antiderivative :math:`F` in D
   #. If :math:`\Gamma` is a loop contour, :math:`\int_{\Gamma} f(z)\,dz=0`.
   #. Contour integrals of :math:`f` are path independent.

We will prove (sketch) :math:`1 \implies 2 \implies 3 \implies 1`.

:math:`1 \implies 2`


We can use a version of the fundamental theorem of calculus. For the sake of presentation
assume that :math:`\Gamma` is a directed smooth curve (if not, run the proof on each of its components). Hence its 
parameterization :math:`z(t) : [a,b] \to \mathbb{C}` is continuously differentiable. By the chain rule we have 

.. math::
   \frac{d}{dt} F(z(t)) = f(z(t))z'(t)

and so 

.. math::

   \int_{\Gamma}f(z)\,dz = \int_a^b f(z(t))z'(t)\,dt = F(z(b)) - F(z(a)).

where the last equation is just a small extension to the fundamental theorem of calculus for real valued functions, 
easily proven. Since :math:`z(b)=z(a)` the above equation is 0, which is what we needed to show.

:math:`2 \implies 3` 


Let :math:`z,w` be two points in our domain. Let :math:`\gamma_1, \gamma_2` be two distinct paths (contours) from :math:`z` to :math:`w`, entirely contained in :math:`D`.
Let :math:`\Gamma` be the contour formed by appending :math:`-\gamma_2` to :math:`\gamma_1`. Then by hypothesis the integral of :math:`f` over :math:`\Gamma` vanishes. This is 
exactly what we want since

.. math::

   0 = \int_{\Gamma} f = \int_{\gamma_1}f - \int_{\gamma_2}f

:math:`3 \implies 1` 


Fix a point :math:`x` in :math:`D` and define :math:`F(z) = \int_x^z f(s)\,ds` where the notation indicates
integrating over a straight line from :math:`x` to :math:`z`. We must show that :math:`F` is differentiable and its derivative is :math:`f`, which can
be done directly. By path independence, we have

.. math::

   F(z+w) - F(z) = \int_x^{z+w} f - \int_x^z f  = \int_{z}^{z+w} f


So the proof is done if we can show

.. math::

   \frac{1}{w} \int_{z}^{z+w} f(s)\,ds \to f(z)

as :math:`w \to 0`. Parameterize the contour as :math:`z+wt` for :math:`0 \leq t \leq 1`. Then the integral becomes

.. math::
   \frac{1}{w} \int_0^1 f(z+wt)w\,dt = \int_0^1 f(z+wt)\,dt.


Finally we have

.. math::
   \int_0^1 f(z+wt)\,dt - f(z) = \int_0^1 f(z+wt)-f(z)\,dt

which tends to :math:`0` as :math:`w \to 0` by continuity of :math:`f` :math:`\blacksquare`.


How do we check if all loop integrals vanish? One tool we can use is the deformation invariance theorem.

.. admonition:: Theorem (Deformation Invariance)

	Let :math:`f` be analytic in a domain D. If :math:`\Gamma_0, \Gamma_1 \subset D` are two loops such that
	:math:`\Gamma_0` can be continuously deformed into :math:`\Gamma_1` then 

	.. math::
		\int_{\Gamma_0} f(z)\,dz = \int_{\Gamma_1}f(z)\,dz.

	.. hint::
		By continuously deformed, we mean that there is a continuous function :math:`z(s,t):[0,1] \times [0,1]` such that
		:math:`z(0,t)` parameterizes :math:`\Gamma_0` and :math:`z(1,t)` parameterizes :math:`\Gamma_1`.

For ease of presentation we assume that :math:`f'` is continuous, and :math:`z(s,t)` is :math:`C^2`. Define 

.. math::

	I(s) = \int_{\Gamma_s} f(z)\,dz = \int_0^1 f(z(s,t)) \frac{\partial z(s,t)}{\partial t}\,dt.

We differentiate :math:`I` with respect to :math:`s` using Leibniz rule, justified by the fact that the integrand
is :math:`C^1` as a function of :math:`s`. We have, by chain rule,

.. math::
	
	\frac{dI(s)}{ds} = \int_0^1 f'(z(s,t)) \frac{\partial z}{\partial s} \frac{\partial z}{\partial t} + f(z(s,t)) \frac{\partial^2 z}{\partial s \partial t}\,dt.

Notice that because :math:`z` is :math:`C^2` the integrand above is also the same expression as if we differentiated with respect to t. Thus

.. math::

	\frac{dI(s)}{ds} = \int_0^1 \frac{\partial}{\partial t} f(z(s,t))\frac{\partial z}{\partial s}\,dt.

Now invoke the fundamental theorem of calculus, and note that the resulting expression vanishes because :math:`z(s,1) = z(s,0)`. In particular :math:`I` is constant,
and so :math:`I(0) = I(1)` as required :math:`\blacksquare`.


If a domain :math:`D` is such that every loop integral can be continuously deformed to a point, then all loop integrals of :math:`f` vanish. This we know now is equivalent to the
existance of an an antiderivative for :math:`f` and path independence of its contour integrals. Such a domain :math:`D` is 
called simply connected if this is true, and is usually the case when :math:`D` has no holes.
The loop integrals vanishing is the content of Cauchy's integral theorem, but keep in mind the other two conditions as well.

.. admonition:: Cauchy's Integral Theorem


	If :math:`f` is analytic in a simply connected domain :math:`D` and :math:`\Gamma` is a loop then :math:`\int_{\Gamma}f = 0`.


Now consider when :math:`f` is analytic on a simply connected domain :math:`D`, and we want to integrate :math:`f` over some closed contour, but it 
has a singularity inside the contour, like :math:`\frac{1}{z}` on :math:`|z|<1`. In this setting, the above conditions do not apply. 
Also, many texts establish early on that when :math:`C` is a circle centred at :math:`a` of some radius we have
:math:`\int_C \frac{dz}{z-a}` is :math:`2 \pi i` when :math:`a` lies inside :math:`C` and :math:`0` otherwise.


We can handle such cases with Cauchy's integral formula. 

.. _cauchy-integral-formula:
.. admonition:: Cauchy's integral formula.

	Let :math:`f` be analytic in a simply connected domain :math:`D` containing a simple, closed, positively oriented contour :math:`\Gamma`.
	If :math:`a` is any point inside :math:`\Gamma` then

	.. math::

		f(a) = \frac{1}{2\pi i} \int_{\Gamma} \frac{f(z)}{z-a}\,dz.


Using the deformation invariance theorem, we may shrink the contour :math:`\Gamma` to a positively oriented circle :math:`C_r` centred at :math:`a` with 
a radius :math:`r` small enough so that the circle stays inside :math:`D`. We rewrite the integral on the right hand side to be 

.. math::

	\oint \frac{f(z)}{z-a}\,dz = \oint \frac{f(a)}{z-a}\,dz + \oint \frac{f(z) - f(a)}{z-a}\,dz.

The first integral is known to be :math:`2 \pi i f(a)`, so the proof is done if we can show that the second integral approaches :math:`0` as 
:math:`r \to 0`. By analyticity, we have that

.. math::

	\frac{f(z) - f(a)}{z-a} = f'(a) + \phi(z)

where :math:`\phi(z)` is a function satisfying :math:`\lim_{z \to a} \phi(z) = \phi(a) = 0`. Choose :math:`r` so small so that
:math:`|\phi(z)| < 1` for each :math:`z` inside and on :math:`C_r`. Then we have

.. math::

	\bigg| \oint \frac{f(z)-f(a)}{z-a}\,dz \bigg| \leq 2 \pi r (|f'(a)| + 1).


which tends to :math:`0` as :math:`r` does, completing the proof :math:`\blacksquare`.

Note that this theorem is also true if our contour is a loop with self intersections. Just separate the contour into multiple loops with winding number one.
Also this result generalizes further to higher derivatives. The formula formally obtained from differentiating under the integral sign turns
out to be correct.

.. _cauchy-integral-formula-general:

.. admonition:: Cauchy's Integral Formula

	Let :math:`f` be analytic in a simply connected domain :math:`D` containing a simple, closed, positively oriented contour :math:`\Gamma`.
	If :math:`a` is any point inside :math:`\Gamma` then 

	.. math::
		f^{(n)}(a) = \frac{n!}{2 \pi i}\int_{\Gamma} \frac{f(s)}{(s-a)^{n+1}}ds 

	for each :math:`n \geq 1`.

We will prove a more general result. Notice in the statement that :math:`g` is just continuous
and our contour :math:`\Gamma` is just a contour, not necessarily closed or positively oriented.

.. admonition:: Lemma

	Let :math:`g` be continuous on some contour :math:`\Gamma`. For :math:`a` not on :math:`\Gamma` define

	.. math:: 
	
		G(z) := \int_{\Gamma} \frac{g(z)}{z-a}\,dz

	Then :math:`G(z)` is analytic at each point not on :math:`\Gamma`. Its derivative is given by 

	.. math::

		G'(z) = \int_{\Gamma} \frac{g(z)}{(z-a)^2}\,dz.


Define :math:`J = J(z)` to be the quantity

.. math::
	J(z) = \frac{G(z) - G(a)}{z-a} - \int_{\Gamma} \frac{g(\zeta)}{(\zeta - a)^2}\,d\zeta.

The proof is done if we can show that :math:`J \to 0` as :math:`z \to a`. Using some algebra we have

.. math::

	\begin{align}
		J(z) &= \int_{\Gamma} \frac{g(\zeta)}{(\zeta - z)(\zeta - a)}\,d\zeta - \int_{\Gamma} \frac{g(\zeta)}{(\zeta - a)^2}\,d\zeta \\
		&= (z-a) \int_{\Gamma} \frac{g(\zeta)}{(\zeta - z)(\zeta - a)^2}\,d\zeta
	\end{align}

where we assume that :math:`z` is in a small enough neighbourhood of :math:`a` so that :math:`z` does not lie on :math:`\Gamma`. The integrand is continuous
on the image of :math:`\Gamma` which is a compact set. Hence it achieves its maximum value there, call it :math:`M`. This lets us bound :math:`|J(z)|` by
:math:`|z-a| M \ell(\Gamma)` which tends to :math:`0` as :math:`z \to a`. :math:`\blacksquare`. 


The technique applied here can be generalized, to prove the validity
of computing :math:`G^{(n+1)}(z)` from :math:`G^{(n)}(z)` by differentiating under the integral sign, but we will not show those details here. 


This result is enough to prove the general version of Cauchy's integral formula. Just choose :math:`\Gamma` to be a circle centred at :math:`a` of small enough radius so that
:math:`f` is analytic inside and on the circle. This also proves that if :math:`f` is analytic on :math:`D`, then so is :math:`f^{(n)}` for each :math:`n \geq 1` :math:`\blacksquare`.

Thus :math:`f` being differentiable once implies differentiability of all orders. So if :math:`f` has an antiderivative then :math:`f` itself is analytic. Recall from the :ref:`first theorem <antiderivative-path-ind-loop-vanish>` that the existance of an antiderivative is equivalent to two other conditions relating to contour integrals of :math:`f`. This is basically the content of Morera's Theorem which we now state.

.. _morera:
.. admonition:: Morera's Theorem

	Let :math:`f` be continuous in a domain :math:`D`. Suppose that all loop integrals vanish. Then :math:`f` is analytic on :math:`D`.


Note we also could have also used path independence of contour integrals of :math:`f` :math:`\blacksquare`.
