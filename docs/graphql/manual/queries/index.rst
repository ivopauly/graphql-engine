Queries
=======

.. contents:: Table of contents
  :backlinks: none
  :depth: 1
  :local:

GraphQL queries are used to fetch data from the server.

Hasura GraphQL engine auto-generates queries as part of the GraphQL schema from your Postgres schema model.
It generates a range of possible queries and operators that also work with relationships defined in your SQL
schema.

All tables of the database tracked by the GraphQL engine can be queried over the GraphQL endpoint.
If you have a tracked table in your database, its query field is added as a nested
field under the ``query_root`` root level type.

Auto-generated query schema
---------------------------

**For example**, the auto-generated query schema for an ``author`` table may look like this:

.. code-block:: graphql

    author (
      distinct_on: [author_select_column]
      where: author_bool_exp
      limit: Int
      offset: Int
      order_by:  [author_order_by!]
    ): [author]


.. note::

  If a table is not in the ``public`` Postgres schema, the query field will be of the format
  ``<schema_name>_<table_name>``.

Exploring queries
-----------------

You can explore the entire schema and the available queries using the ``GraphiQL`` interface in the Hasura console.

Let’s take a look at the different queries you can run using the Hasura GraphQL engine. We’ll use examples
based on a typical author/article schema for reference.

.. toctree::
  :maxdepth: 1

  simple-object-queries
  nested-object-queries
  aggregation-queries
  distinct-queries
  query-filters
  sorting
  pagination
  Using multiple arguments <multiple-arguments>
  multiple-queries
  derived-data
  control-access
