.. _ref_eql_functions_string:


String Functions and Operators
==============================


.. eql:operator:: STRPLUS: A + B

    :optype A: str
    :optype B: str
    :resulttype: str

    String concatenation.

    .. code-block:: edgeql-repl

        db> SELECT 'some' + ' text';
        {'some text'}


.. eql:operator:: LIKE: A LIKE B

    :optype A: str or bytes
    :optype B: str or bytes
    :resulttype: bool

    Case-sensitive simple string matching.

    .. code-block:: edgeql-repl

        db> SELECT 'abc' LIKE 'abc';
        {True}
        db> SELECT 'abc' LIKE 'a%';
        {True}
        db> SELECT 'abc' LIKE '_b_';
        {True}
        db> SELECT 'abc' LIKE 'c';
        {False}


.. eql:operator:: ILIKE: A ILIKE B

    :optype A: str or bytes
    :optype B: str or bytes
    :resulttype: bool

    Case-insensitive simple string matching.

    .. code-block:: edgeql-repl

        db> SELECT 'Abc' ILIKE 'a%';
        {True}


.. eql:function:: std::lower(str) -> str

    :param $0: input string
    :paramtype $0: str

    :return: lowercase copy of the input string
    :returntype: str

    Return a lowercase copy of the input string.

    .. code-block:: edgeql-repl

        db> SELECT lower('Some Fancy Title');
        {'some fancy title'}

.. eql:function:: std::re_match(str, str) -> array<str>

    :param $0: input string
    :paramtype $0: str
    :param $1: regular expression
    :paramtype $1: str

    :return: first matched groups as :eql:type:`array\<str\>`
    :returntype: array<str>

    :index: regex regexp regular

    Find the first regular expression match in a string.

    Given an input string and a regular expression string find the
    first match for the regular expression within the string. Return
    the match, each match represented by an :eql:type:`array\<str\>`
    of matched groups.

    .. code-block:: edgeql-repl

        db> SELECT std::re_match('I ❤️ edgeql', '\w{4}ql');
        {['edgeql']}

.. eql:function:: std::re_match_all(str, str) -> SET OF array<str>

    :param $0: input string
    :paramtype $0: str
    :param $1: regular expression
    :paramtype $1: str

    :return: set of all matched groups as :eql:type:`array\<str\>`
    :returntype: SET OF array<str>

    :index: regex regexp regular

    Find all regular expression matches in a string.

    Given an input string and a regular expression string repeatedly
    match the regular expression within the string. Return the set of
    all matches, each match represented by an :eql:type:`array\<str\>`
    of matched groups.

    .. code-block:: edgeql-repl

        db> SELECT std::re_match_all('an abstract concept', 'a\w+');
        {['an'], ['abstract']}

.. eql:function:: std::re_test(str, str) -> bool

    :param $0: input string
    :paramtype $0: str
    :param $1: regular expression
    :paramtype $1: str

    :return: ``True`` if there is a match, ``False`` otherwise
    :returntype: bool

    :index: regex regexp regular match

    Test if a regular expression has a match in a string.

    Given an input string and a regular expression string test whether
    there is a match for the regular expression within the string.
    Return ``True`` if there is a match, ``False`` otherwise.

    .. code-block:: edgeql-repl

        db> SELECT std::re_test('abc', 'a');
        {True}
