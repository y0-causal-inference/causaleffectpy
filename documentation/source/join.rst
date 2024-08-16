Join
====

The `join` function determines whether the terms of the atomic expression actually represent a joint distribution.
It attempts to combine two terms: the joint term `P(J|D)` obtained from `simplify()` and the
term `P(V|C) := P(Vk|Ck)` of the current iteration step. The goal is to
determine if these terms can be combined based on the d-separation criteria in the graph `G`.

Parameters
----------
J : list of str
    Joint set `P(J|D)`; already processed and included in the joint distribution
    from previous `simplify` iteration. Initially, may be empty for the starting point of
    the joint distribution. `vari` is added to expand it if d-separation conditions are met.
D : list of str
    Term `P(V|C) := P(Vk|Ck)`; set of variables that condition the joint distribution.
    `join` checks and updates `D` as necessary to maintain the validity of the joint distribution
    when combined with `vari`.
vari : str
    Current variable being considered for inclusion in the joint distribution.
cond : list of str
    Set of variables that condition the current variable `vari`. `join` uses `cond`
    to evaluate conditional independence and determine if `vari` can be added to `J`.
S : list of str
    Not used directly in `join`. Current summation variable.
M : list of str
    Missing variables (variables not contained within the expression).
O : list of str
    Observed variables (variables contained within the expression).
G_unobs : y0.Graph
    Separate graph that turns bidirected edges into explicit nodes for unobserved confounders.
G : y0.Graph
    Main graph `G`. Includes bidirected edges.
G_obs : y0.Graph
    Separate graph that does not contain bidirected edges (only contains the directed edges with observed nodes).
topo : list of str
    The topological ordering of the vertices in graph `G`.

Returns
-------
list of str
    The joint result, or the original result if none of the conditions for joining were met.

Dependencies
-------
This function depends on several functions from the causaleffect package, including: :func:`powerset`, :func:`is_d_separated`, and :func:`insert`.

See Also
--------
- :func:`simplify`
- :func:`is_d_separated`
- :func:`insert`

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

References
----------
Tikka, S., & Karvanen, J. (2017). Simplifying probabilistic expressions in causal inference. Journal of Machine Learning Research, 18(36), 1-30.

Author
------
Haley Hummel,
Psychology PhD student at Oregon State University

