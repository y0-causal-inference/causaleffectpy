Insert
======

The `Insert` function inserts a missing variable into a joint distribution `P(J|D)` using d-separation criteria in a given graph `G`. It is called when there are variables without corresponding terms in the expression.

Parameters
----------
J : list of str
    The set of variables representing the joint distribution.
D : list of str
    The set of variables representing the conditioning set of the joint distribution.
M : str
    The variable to be inserted.
cond : list of str
    The set of conditioning variables.
S : list of str
    The current summation variable.
O : list of str
    The set of observed variables.
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
dict
    A dictionary with the following keys:
    - `J_new`: list of str. An updated set of joint distribution variables.
    - `D_new`: list of str. An updated set of conditioning variables.
    - `M`: str. The inserted variable.
    - `ds_i`: list of str. The subset from the power set used in the insertion.
    
    If no conditions were met, `insert` will return the original `J` and `D`.


Examples
--------
Section in-progress
.. code-block:: python


See Also
--------
- :func:`join`
- :func:`simplify`
- :func:`wrap_dSep`
- :func:`powerset`

Keywords
--------
models, manip, math, utilities, graphs, methods, multivariate, distribution, probability

Concepts
--------
probabilistic expressions, graph theory, joint distribution, causal inference, d-separation

References
----------
Tikka, S., & Karvanen, J. (2017). Simplifying probabilistic expressions in causal inference. *Journal of Machine Learning Research*, 18(36), 1-30.

Author
------
Haley Hummel,
Psychology PhD student at Oregon State University