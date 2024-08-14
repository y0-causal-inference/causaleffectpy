Simplify
========

This function algebraically simplifies probabilistic expressions given by the ID algorithm from :func:`identify`. It always attempts to perform maximal simplification, meaning that as many variables of the set are removed as possible. If the simplification in terms of the entire set cannot be completed, the intermediate result with as many variables simplified as possible should be returned.

Run :func:`identify` with the graph information first, then use the output of :func:`identify` as the `P` in :func:`parse_causaleffect`. Use the output from :func:`parse_causaleffect` as the `P` in :func:`simplify`.

For further information, see Tikka & Karvanen (2017) "Simplifying Probabilistic Expressions in Causal Inference" Algorithm 1.


Parameters
----------
P : `sympy` expression or `y0` `Probability` object
    The probabilistic expression that will be simplified, typically created using symbolic expressions in `sympy` or using `y0`'s Probability class.
topo : list of nodes
    The topological ordering of the vertices in graph `G`, which can be obtained using `networkx.topological_sort`.
G_unobs : networkx.DiGraph object
    A separate directed acyclic graph (DAG) that includes explicit nodes for unobserved confounders, created using `networkx.DiGraph`.
G : networkx.DiGraph object
    Main graph G, which includes bidirected edges, and is created with :func:`igraph.graph_formula`.
G_obs : networkx.DiGraph object
    A DAG that only includes directed edges, representing observed variables, created using `networkx.DiGraph`.

Details
-------
This function depends on several other functions and classes, including: :func:`parents`, :func:`ancestors`, :func:`parse_causaleffect`, :func:`is_d_separated`, and :class:`probability`.

Returns
-------
list
    Section in-progress 

References
----------
Tikka, S., & Karvanen, J. (2017). Simplifying probabilistic expressions in causal inference. Journal of Machine Learning Research, 18(36), 1-30.


See Also
--------
:func:`identify`, :func:`parse_causaleffect`, :func:`get.expression`, :class:`probability`

Examples
--------
Section in-progress

.. code-block:: python

   
Keywords
--------
models, manip, math, utilities
Concepts
--------
probabilistic expressions, graph theory, causal inference

Author
------
Haley Hummel,
Psychology PhD student at Oregon State University
