Bliss 0.73 with CMake
===

Bliss 0.73 from http://www.tcs.hut.fi/Software/bliss/ (downloaded on 28/01/19)  with the following changes:
- replaced the logical operators 'and', 'or' and 'not' with '&&', '||' and '!' because MSVC doesn't support the former syntax
- comment out the uses of the Timer class because it depends on UNIX specific headers but it's "Not essential if you are using bliss as a library." according to timer.hh
- add a CMake build script

See the commit history for a complete list of changes!
