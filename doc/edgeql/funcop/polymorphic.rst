.. _ref_eql_functions_polymorphic:

===========
Polymorphic
===========

.. eql:type:: any

    :index: any

    Generic type.


.. eql:function:: std::len(any) -> int64

    :param $0: input
    :paramtype $0: str or bytes or array

    :return: "length" of input
    :returntype: int64

    A polymorphic function to calculate a "length" of its first
    argument.

    Return the number of characters in a :eql:type:`str`, or the
    number of bytes in :eql:type:`bytes`, or the number of elements in
    an :eql:type:`array`.

    .. code-block:: edgeql-repl

        db> SELECT len('foo');
        {3}

        db> SELECT len([2, 5, 7]);
        {3}
