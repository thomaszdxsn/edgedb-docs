.. _ref_eql_functions_uuid:

==============
UUID Functions
==============

.. eql:function:: std::uuid_generate_v1mc() -> uuid

    :return: version 1 UUID
    :returntype: uuid

    Return a version 1 UUID.

    The algorithm uses a random multicast MAC address instead of the
    real MAC address of the computer.

    .. code-block:: edgeql-repl

        db> SELECT std::uuid_generate_v1mc();
        {'1893e2b6-57ce-11e8-8005-13d4be166783'}
