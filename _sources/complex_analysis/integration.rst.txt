Contour Integration
====================

We will have a quick, simple discussion on contour integrals and how they throw light on the behaviour of holomorphic functions.
Not intended to be a complete discussion, reader is expected to have acquaintance with contour integration already.

.. note:: A domain :math:`D` will refer to an open connected subset of the complex plane. Functions will usually have the form
   :math:`f: D \to \mathbb{C}` for some domain D.

.. admonition:: Theorem

   Let :math:`f`  be continuous in a domain D. The following are equivalent:

   #. :math:`f` has an antiderivative :math:`F` in D
   #. If :math:`\Gamma` is a loop contour, :math:`\int_{\Gamma} f(z)\,dz=0`.
   #. Contour integrals of :math:`f` are path independent.

We will prove (sketch) :math:`1 \implies 2 \implies 3 \implies 1`.

:math:`1 \implies 2` is a version of the fundamental theorem of calculus. For the sake of presentation
assume that :math:`\Gamma` is a directed smooth curve (if not, run the proof on each of its components). Hence its 
parameterization :math:`z(t) : [a,b] \to \mathbb{C}` is continuously differentiable. By the chain rule we have 

.. math::
   \frac{d}{dt} F(z(t)) = f(z(t))z'(t)

and so 

.. math::

   \int_{\Gamma}f(z)\,dz = \int_a^b f(z(t))z'(t)\,dt = F(b) - F(a).

where the last equation is just an invocation of a small extension to the fundamental theorem of calculus for real variables. 

For :math:`2 \implies 3` let :math:`z,w` be two points in our domain. Let :math:`\gamma_1, \gamma_2` be two distinct paths (contours) from :math:`z` to :math:`w`, entirely contained in :math:`D`.
Let :math:`\Gamma` be the contour formed by appending :math:`-\gamma_2` to :math:`\gamma_1`. Then by hypothesis the integral of :math:`f` over :math:`\Gamma` vanishes. This is 
exactly what we want since

.. math::

   0 = \int_{\Gamma} f = \int_{\gamma_1}f - \int_{\gamma_2}f

For :math:`3 \implies 1` fix a point :math:`x` in :math:`D` and define :math:`F(z) = \int_x^z f(s)\,ds` where the notation indicates
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


Fianlly we have

.. math::
   \int_0^1 f(z+wt)\,dt - f(z) = \int_0^1 f(z+wt)-f(z)\,dt \to 0

as :math:`w \to 0` :math:`\blacksquare`.
