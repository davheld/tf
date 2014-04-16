tf
==

A custom version of the ros/tf package, with small API changes. Used by some the our code, until we migrate to TF2.

Inserted a class in the class hierarchy between Transformer and
TransformListener. This class serves to decouple the 2 functions
of the original TransformListener class:
- a bunch of helper functions to apply a transform to some data structures
- listen to tf messages and update the buffer

With the new class hierarchy, TransformerHelper provides the helper functions,
and TransformListener updates the buffer.

The same decoupling was implemented in TF2, so as soon as we migrate our code 
to TF2 we don't need this custom implementation anymore.

I submitted the changes to the upstream TF package, but Tully Foote does not want
to modify the stable TF API at this point.
