Join
====

The `join` function determines whether the terms of the atomic expression actually represent a joint distribution.
It attempts to combine two terms: the joint term :math:`P(J|D)` obtained from `simplify()` and the term :math:`P(V|C) := P(V_k|C_k)` 
of the current iteration step. `join` iterates over potential subsets to find a valid set where the variable `new_variable` 
can be added to the joint distribution `joint_dist_variables`. During this process, `join` checks conditional 
independencies using both `joint_conditioning_set` and `prob_conditioning_set`. The goal is to determine if these 
terms can be combined based on the d-separation criteria in the graph `G`.

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
new_variable : str
    Equivalent to `vari` in Tikka's `causaleffect` R package.
    New variable being considered for inclusion in the joint distribution (the new variable that we may want to add to the joint distribution `joint_dist_variables`).
    `join` attempts to update the joint distribution `joint_dist_variables` by adding `new_variable` to define a new probabilistic term if the term still 
    satisfies the required conditional independencies. `insert` adds `new_variable` to `joint_dist_variables`.
prob_conditioning_set : list of str
    Equivalent to `cond` in Tikka's `causaleffect` R package.
    Conditioning set for the current probabilistic term P(vari|cond); the set of variables that condition the current variable `new_variable`. 
    `join` uses `prob_conditioning_set` to evaluate conditional independence and determine if `new_variable` can be added to `joint_dist_variables`.
summation_variables : list of str
    Equivalent to `S` in Tikka's `causaleffect` R package.
    Not used directly in `join`. Current summation variable.
inserted_variables : list of str
    Equivalent to `M` in Tikka's `causaleffect` R package.
    Missing variables (variables not contained within the expression).
observed_variables : list of str
    Equivalent to `O` in Tikka's `causaleffect` R package.
    Observed variables (variables contained within the expression).
G_unobs : `networkx.DiGraph` object
    A separate directed acyclic graph (DAG) that includes explicit nodes for unobserved confounders, created using :func:`networkx.DiGraph`.
G : `networkx.DiGraph` object
    Main graph G, which includes bidirected edges, and is created with :func:`networkx.DiGraph`.
G_obs : `networkx.DiGraph` object
    A DAG that only includes directed edges, representing observed variables, created using :func:`networkx.DiGraph`.
topo : list of nodes
    The topological ordering of the vertices in graph `G`, which can be obtained using :func:`networkx.topological_sort`.

Returns
-------
Section in-progress

Dependencies
-------
This function depends on several other functions and classes, including: 
- :func:`powerset`
- :func:`is_d_separated`
- :func:`insert`. `insert` adds `new_variable` to `joint_dist_variables`.

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
Tikka, S. (2022). `causaleffect`: Deriving Expressions of Joint Interventional Distributions and Transport Formulas in Causal Models (1.3.15) [R package]. https://github.com/santikka/causaleffect/.
Tikka, S., & Karvanen, J. (2017). Simplifying probabilistic expressions in causal inference. Journal of Machine Learning Research, 18(36), 1-30.
Tikka, S., & Karvanen, J. (2018). Identifying causal effects with the R package causaleffect. arXiv preprint arXiv:1806.07161.

Author
------
Haley Hummel,
Psychology PhD student at Oregon State University

