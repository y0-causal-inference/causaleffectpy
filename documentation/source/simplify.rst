Simplify
========

This function algebraically simplifies probabilistic expressions given by the ID algorithm from :func:`causal.effect`. It always attempts to perform maximal simplification, meaning that as many variables of the set are removed as possible. If the simplification in terms of the entire set cannot be completed, the intermediate result with as many variables simplified as possible should be returned.

Run :func:`causal.effect` with the graph information first, then use the output of :func:`causal.effect` as the `P` in :func:`parse.expression`. Use the output from :func:`parse.expression` as the `P` in :func:`simplify`.

For further information, see Tikka & Karvanen (2017) "Simplifying Probabilistic Expressions in Causal Inference" Algorithm 1.

Parameters
----------
P : probability object
    The probabilistic expression that will be simplified, created with :func:`probability`.
topo : igraph list
    The topological ordering of the vertices in graph G, created with :func:`igraph.topological_sort` and :func:`igraph.get_vertex_attribute`.
G_unobs : object
    Separate graph that turns bidirected edges into explicit nodes for unobserved confounders, created with :func:`unobserved_graph`.
G : object
    Main graph G, includes bidirected edges, created with :func:`igraph.graph_formula`.
G_obs : object
    Separate graph that does not contain bidirected edges (only contains the directed edges with observed nodes), created with :func:`observed_graph`.

Details
-------
This function depends on several functions from the causaleffect package, including: :func:`irrelevant`, :func:`wrap.dSep`, :func:`dSep`, :func:`join`, :func:`ancestors`, :func:`factorize`, :func:`parents`, :func:`children`, and :func:`powerset`.

Returns
-------
list
    Returns the simplified atomic expression in a list structure. For example::

        {
            "var": [],
            "cond": [],
            "sumset": ["z"],
            "do": [],
            "product": [True],
            "fraction": [False],
            "sum": [False],
            "children": [],
            "den": [],
            "num": [],
            "domain": [0],
            "weight": [0],
            "class": ["probability"]
        }

This long list structure can be converted into a string formatted in LaTeX syntax by the :func:`get.expression` function. For example::

    string_expression = simplify(P, topo, G_unobs, G, G_obs)
    get_expression(string_expression)

The resulting string should look like: ``\\sum_{w}P(y|w,x)P(w)``.


See Also
--------
- :func:`causal.effect`
- :func:`parse.expression`
- :func:`get.expression`
- :func:`probability`

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
Tikka, S., & Karvanen, J. (2017). Simplifying probabilistic expressions in causal inference. *Journal of Machine Learning Research*, 18(36), 1-30.

Author
------
Haley Hummel,
Psychology PhD student at Oregon State University
