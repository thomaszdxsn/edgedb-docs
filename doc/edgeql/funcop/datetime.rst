.. _ref_eql_functions_datetime:


Date/time
=========

.. eql:function:: std::current_date() -> date

    :return: current server date
    :returntype: date

    Return the current server date.

    .. code-block:: edgeql-repl

        db> SELECT std::current_date();
        {'2018-05-14'}

.. eql:function:: std::current_datetime() -> datetime

    :return: current server date and time
    :returntype: datetime

    Return the current server date and time.

    .. code-block:: edgeql-repl

        db> SELECT std::current_datetime();
        {'2018-05-14T20:07:11.755827+00:00'}

.. eql:function:: std::current_time() -> time

    :return: current server time
    :returntype: time

    Return the current server time.

    .. code-block:: edgeql-repl

        db> SELECT std::current_time();
        {'20:07:48.365534+00'}
