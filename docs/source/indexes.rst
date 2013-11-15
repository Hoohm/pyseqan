
Indexes
=======

.. testsetup:: *

   import seqan

An index is the result of pre-processing a text to allow fast look-up
and search operations. The enhanced suffix array (ESA) is an index that allows
retrieval of strings based on their content. We can build an ESA from a string
set easily.

..  doctest::

    >>> seqs = seqan.StringDNASet(('ACGT', 'AAAA', 'GGGG', 'AC'))
    >>> index = seqan.IndexStringDNASetESA(seqs)

Once we have the index we can find strings in it using a top down iterator.

..  doctest::

    >>> iterator = index.topdown()
    >>> if iterator.goDownStr('AC'):
    ...     for occ in iterator.occurrences:
    ...         print 'Found "AC" in sequence %d at position %d' % (occ.i1, occ.i2)
    Found "AC" in sequence 3 at position 0
    Found "AC" in sequence 0 at position 0

Here we used the occurrences property of the top down iterator to locate all the
occurrences of the string AC in the original string set.
