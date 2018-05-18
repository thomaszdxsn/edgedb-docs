.. _ref_eql_functions_setagg:

===================
Aggregate Functions
===================

:index: set aggregate

.. eql:function:: std::count(SET OF any) -> int64

    :param $0: input set
    :paramtype $0: SET OF any

    :return: number of elements in the input set
    :returntype: int64

    :index: aggregate

    Return the number of elements in a set.

    .. code-block:: edgeql-repl

        db> SELECT count({2, 3, 5});
        {3}

        db> SELECT count(User);  # number of User objects in db
        {4}

.. eql:function:: std::sum(SET OF anyreal) -> anyreal

    :param $0: input set
    :paramtype $0: SET OF anyreal

    :return: sum of the input set of numbers
    :returntype: anyreal

    :index: aggregate

    Return the sum of the set of numbers.

    The numbers have to be either :eql:type:`anyreal` or any type that
    can be cast into it, such as :eql:type:`float64` or
    :eql:type:`int64`.

    .. code-block:: edgeql-repl

        db> SELECT sum({2, 3, 5});
        {10}

        db> SELECT sum({0.2, 0.3, 0.5});
        {1.0}

Here's a list of aggregate functions covered in other sections:

* :eql:func:`array_agg`
