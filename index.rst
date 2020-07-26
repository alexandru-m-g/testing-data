INFORMATION ABOUT THE SEARCH ENGINE IN HDX
==========================================

The search engine in HDX / CKAN is based on `Apache Solr <https://lucene.apache.org/solr/>`_

By default the search queries in HDX are processed by using
`the DisMax Query Parser <https://lucene.apache.org/solr/guide/6_6/the-dismax-query-parser.html>`_



There are 2 types of fields that we are searching through:

*  **string** - These fields are not split into terms when indexed in solr. So a query term must match them exactly in order for
   solr to be able to find the term in a 'string' field. Query terms that should match such fields should be
   double-quoted to ensure that they are not split into separate terms.
   See the *name* field below as an example for that.
*  **text** - These fields are split into terms and stemmed before being indexed.
   Ex: 'population affected' would be indexed as 'popul' and 'affect'
   So a query term of "populated" would match the above example.

The list of dataset fields that are used for searching in descending order of their importance (weight):

*  **name** (string) - this is the string that appears at the end of the URL, as in */dataset/dataset-name*.
   Please note that in order to match this field an exact match needs to exist in the query. Also, the
   query term needs to be quoted so that the name is not split into separate terms. Example: "dataset-name"
*  **title** (text) - this is the title of a dataset. When stored
