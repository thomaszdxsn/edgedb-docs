.. _ref_eql_funcop_comparison:

====================
Comparison Operators
====================

EdgeDB supports the following comparison operators:

.. eql:operator:: EQ: A = B

    :optype A: any
    :optype B: any
    :resulttype: bool

    Compare two values for equality.

    .. code-block:: edgeql-repl

        db> SELECT 3 = 3.0;
        {True}


.. eql:operator:: NEQ: A != B

    :optype A: any
    :optype B: any
    :resulttype: bool

    Compare two values for inequality.

    .. code-block:: edgeql-repl

        db> SELECT 3 != 3.14;
        {True}


.. eql:operator:: COALEQ: A ?= B

    :optype A: OPTIONAL any
    :optype B: OPTIONAL any
    :resulttype: bool

    Compare two values for equality.

    Works the same as regular :eql:op:`=<EQ>`, but also allows
    comparing ``{}``.  Two ``{}`` are considered equal.

    .. code-block:: edgeql-repl

        db> SELECT {1} ?= {1.0};
        {True}

    .. code-block:: edgeql-repl

        db> SELECT {1} ?= {};
        {False}

    .. code-block:: edgeql-repl

        db> SELECT <int64>{} ?= {};  # the type of the empty set requires disambiguation here
        {True}


.. eql:operator:: COALNEQ: A ?!= B

    :optype A: OPTIONAL any
    :optype B: OPTIONAL any
    :resulttype: bool

    Compare two values for inequality.

    Works the same as regular :eql:op:`\!=<NEQ>`, but also allows
    comparing ``{}``.  Two ``{}`` are considered equal.

    .. code-block:: edgeql-repl

        db> SELECT {2} ?!= {2};
        {False}

    .. code-block:: edgeql-repl

        db> SELECT {1} ?!= {};
        {True}

    .. code-block:: edgeql-repl

        db> SELECT <int64>{} ?!= {};
        {False}


.. eql:operator:: LT: A < B

    :optype A: any
    :optype B: any
    :resulttype: bool

    ``TRUE`` if ``A`` is less than ``B``.

    .. code-block:: edgeql-repl

        db> SELECT 1 < 2;
        {True}


.. eql:operator:: GT: A > B

    :optype A: any
    :optype B: any
    :resulttype: bool

    ``TRUE`` if ``A`` is greater than ``B``.

    .. code-block:: edgeql-repl

        db> SELECT 1 > 2;
        {False}


.. eql:operator:: LTEQ: A <= B

    :optype A: any
    :optype B: any
    :resulttype: bool

    ``TRUE`` if ``A`` is less than or equal to ``B``.

    .. code-block:: edgeql-repl

        db> SELECT 1 <= 2;
        {True}


.. eql:operator:: GTEQ: A >= B

    :optype A: any
    :optype B: any
    :resulttype: bool

    ``TRUE`` if ``A`` is greater than or equal to ``B``.

    .. code-block:: edgeql-repl

        db> SELECT 1 >= 2;
        {False}


.. eql:operator:: EXISTS: EXISTS A

    :optype A: SET OF any
    :resulttype: bool

    Test whether a set is not empty.

    ``EXISTS`` is an aggregate operator that returns a singleton set
    ``{true}`` if the input set is not empty and returns ``{false}``
    otherwise.

    .. code-block:: edgeql-repl

        db> SELECT EXISTS {1, 2};
        {True}
