Contour Integration
====================

We will have a quick, simple discussion on contour integrals and how they throw light on the behaviour of holomorphic functions.
Not intended to be a complete discussion, reader is expected to have acquaintance with contour integration already.

.. note:: A domain :math:`D` will refer to an open connected subset of the complex plane. Functions will usually have the form
   :math:`f: D \to \mathbb{C}` for some domain D.

Our first theorem will connect the presence of an antiderivative with path independence and vanishing loop integrals.
In fact these are equivalent in some sense.

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
be done directly. Notice that :math:`x \to z+w \to z \to x` is a loop integral. So by our hypothesis we have

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


In this case, we will want to appeal to Cauchy's integral formula.

.. admonition:: Theorem

	Let :math:`f` be analytic in a simply connected domain :math:`D` containing a simple, closed, positively oriented contour :math:`\Gamma`.
	If :math:`a` is any point inside :math:`\Gamma` then

	.. math::

		f(a) = \frac{1}{2\pi i} \int_{\Gamma} \frac{f(z)}{z-a}\,dz.

	
