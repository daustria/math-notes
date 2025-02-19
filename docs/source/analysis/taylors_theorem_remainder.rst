Taylor's Theorem with Remainder
================================


We discuss a multivariable version of Taylor's theorem that uses only first order partial derivatives.

.. admonition:: Theorem

	Let :math:`g:\mathbb{R}^n \to \mathbb{R}` be differentiable on an open set :math:`U \subset \mathbb{R}^n` star shaped with respect to a point :math:`a \in U`.
	There exists a :math:`t_0` with :math:`0 < t_0 < 1` such that 

	.. math::
		g(x) = g(a) + \sum _{i=1}^n \frac {\partial g}{\partial x_i} (a + t_0(x-a)) (x^i - a^i).

Since :math:`U` is star shaped about :math:`a` then
then :math:`g` is differentiable on the line :math:`X(t) = a + t(x-a)` for any :math:`x` in :math:`U`. In other words the function
:math:`g(X(t))` is differentiable on :math:`(0,1)`. Apply the mean value theorem (single variable) and chain rule (multivariable) to :math:`g(X(t))` 
and we obtain the equality stated in the theorem :math:`\blacksquare`.

An immediate corollary is some bounds given in the following form

.. admonition:: Corollary

	Let :math:`g,a,U` be as before. If :math:`\frac{\partial g}{\partial x_i} < K` on :math:`U` then

	.. math::
		|g(x) - g(a)| < K \sqrt{n} ||x-a||,\quad x \in U.
	
	More generally if :math:`G(x) = (g_1(x), \ldots g_m(x))` is differentiable on :math:`U` starshaped with respect to a point :math:`a` 
	and :math:`\frac{\partial g_i}{\partial x_j} < K` on :math:`U` then 

	.. math::
		||G(x) - G(a)|| < K \sqrt{nm} ||x-a||, \quad x \in U.

The proof is simple, uses the triangle inequality applied to our version of Taylor's theorem :math:`\blacksquare`.

Also, supposedly there is a way to use this theorem to prove the interchangability of partial derivatives, but I don't know
how to show it yet.

.. admonition:: Corollary

	If :math:`g` is :math:`C^r` on :math:`U` then partial derivatives of :math:`g` of up to order :math:`r` is independent
	of the order. Namely if :math:`(i_1,\ldots,i_k)` and :math:`(j_1,\ldots,j_k)` are permutations with :math:`k \leq r` then

	.. math::
		\frac{\partial^k g}{\partial x_{i_1} \ldots x_{i_k}} = \frac{\partial^k g}{\partial x_{j_1} \ldots x_{j_k}}.

There is another version of this theorem that deals with smooth functions.

.. admonition:: Theorem

	Let :math:`g,U,a` be as before. Then there are :math:`C^{\infty}` functions :math:`g_i` on :math:`U` such that

	.. math::		
		g(x) = g(a) + \sum _{i=1}^n g_i(x)(x^i - a^i).

	The :math:`g_i` satisfy :math:`g_i(p) = \frac{\partial g}{\partial x_i}(p)`. In fact,
	the :math:`g_i` have the form

	.. math::
		g_i(x) = \int_0^1 \frac{\partial g}{\partial x_i}(a + t(x-a))\,dt

The smoothness of the :math:`g_i` can be shown directly from the smoothness of :math:`\frac{\partial g}{\partial x_i}`. 
The partial derivatives of :math:`g_i` can be computed using Leibniz rule. For example, view the integrand
in the right hand side of :math:`g_i` as a smooth function :math:`F(x,t)` on :math:`U \times [0,1]`. Then

.. math::
	\frac{\partial g_i}{\partial x_j} = \frac{\partial}{\partial x_j} \int_0^1 F(x,t)\,dt = \int_0^1 \frac{\partial}{\partial x_j} F(x,t)\,dt.

Furthermore the integrand on the right hand side is smooth, from smoothness of :math:`g`. In general, we can compute partial derivatives of 
:math:`g_i` of arbitrary order by repeatedly applying Leibniz rule, to obtain a function of the form :math:`\int_0^1 F(x,t)\,dt` where :math:`F` 
is smooth on its domain. Leibniz rule also guarantees that such a function has continuous partial derivaties of the first order. So 
:math:`g_i` has continuous partial derivatives of all orders and is therefore smooth (also need to show :math:`g` itself is continuous, probably).

To obtain the existence of the :math:`g_i`, we perform a similar computation as the previous theorem. 

.. math::
	g(x) - g(a) = \int_0^1 \frac{d}{dt} g(a + t(x-a)) = \sum_{i=1}^n (x^i - a^i) \int_0^1 \frac{\partial g}{\partial x_i}(a + t(x-a))\,dt

which completes the proof :math:`\blacksquare`.

A connection between these two theorems lies in the mean value theorem for integrals. Since :math:`f_i = \frac{\partial g}{\partial x_i}(a + t(x-a))` is differentiable
as a function of :math:`t`, there is a point :math:`0<t_0<1` such that :math:`\frac{1}{1-0} \int_0^1 f_i(t) = f_i(t_0)`

This theorem is quite helpful in the study of differential topology. For example, it can be used to show that the vector space of tangent vectors of an :math:`n` dimensional
smooth manifold :math:`M` is isomorphic to :math:`\mathbb{R}^n` when the tangent vectors are defined as germs acting on :math:`C^{\infty}(M)`,
the space of smooth real valued functions :math:`f: M \to \mathbb{R}` on :math:`M`.
