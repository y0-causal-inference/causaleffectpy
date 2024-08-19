Insert
======

The `Insert` function inserts a missing variable into a joint distribution :math:`P(J|D)` using d-separation criteria in a given graph `G`. It is called when there are variables without corresponding terms in the expression.

Parameters
----------
joint_dist_variables : list of str
    Equivalent to `J` in Tikka's `causaleffect` R package.
    Existing joint set :math:`P(J|D)`; already processed and included in the joint distribution
    from previous `simplify` iteration. Initially, may be empty for the starting point of
    the joint distribution. `new_variable` is added to expand it using `insert` if d-separation conditions are met.
joint_conditioning_set : list of str
    Equivalent to `D` in Tikka's `causaleffect` R package. Represented by the term :math:`P(V|C) := P(V_k|C_k)` in Tikka & Karvanen (2017). 
     Conditioning set for the already existing joint distribution :math:`P(J|D)`, used to condition the joint distribution over the set `joint_dist_variables`. 
     As `join` iterates, `conditioning_set` is modified to determine how the joint distribution :math:`P(J|D)` can be updated to 
     include the new variable `new_variable`, while preserving the required conditional independencies.
inserted_variables : str
     Equivalent to `M` in Tikka's `causaleffect` R package.
    Missing variables (variables not contained within the expression).
prob_conditioning_set : list of str
    Equivalent to `cond` in Tikka's `causaleffect` R package.
    Conditioning set for the current probabilistic term P(vari|cond); the set of variables that condition the current variable `new_variable`. 
    `join` uses `prob_conditioning_set` to evaluate conditional independence and determine if `new_variable` can be added to `joint_dist_variables`.
summation_variables : list of str
    Equivalent to `S` in Tikka's `causaleffect` R package.
    Not used directly in `join`. Current summation variable.
observed_variables : list of str
    Equivalent to `O` in Tikka's `causaleffect` R package.
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
Section in-progress


Examples
--------
Section in-progress
.. code-block:: python


See Also
--------
- :func:`join`
- :func:`simplify`
- :func:`is_d_separated`
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