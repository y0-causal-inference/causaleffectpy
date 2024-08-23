Powerset
========

The `Powerset` function generates the power set of a given set. The power set is the set of all possible subsets of the original set, including the empty set and the set itself.

Parameters
----------
set : list
    A list representing the original set for which the power set will be generated. The set can contain any type of elements (e.g., numeric, string, or boolean).

Details
-------
The function computes all possible combinations of the elements of the input set. This includes the empty subset, individual elements, and all larger subsets up to and including the full set. The number of subsets in the power set of a set of size `n` is `2^n`.

Returns
-------
list of lists
    A list of lists, where each inner list is a subset of the original input set. The list contains `2^n` subsets, where `n` is the length of the input set. If the input set is empty, the function returns a list containing only the empty set.

Examples
--------
Section in-progress
.. code-block:: python


See Also
--------
- `join`: for using :func:`powerset` with conditional independence in probabilistic graphical models.

Keywords
--------
set theory, combinatorics

Concepts
--------
power set, subsets

References
----------
Tikka, S., & Karvanen, J. (2017). Simplifying probabilistic expressions in causal inference. Journal of Machine Learning Research, 18(36), 1-30.

Author
------
Haley Hummel,
Psychology PhD student at Oregon State University
