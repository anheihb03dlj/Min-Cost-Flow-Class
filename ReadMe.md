# Min-Cost-Flow-Class
ReadMe for the "pure LGPL part" of MCFClass project, a set of C++ solvers for
(Linear or Convex Quadratic Separable) Min Cost Flow Problem solvers under the
same interface seriving from the base class MCFClass.

The aim of MCFClass is to provide an abstraction layer between practitioners
who need to solve MCF problems within complex applications and developers of
MCF software. The idea is to provide an interface which caters for all the
needs that a practitioner can have, thereby allowing him/her to use whichever
algorithm - among those that have an implementation conforming to this
interface - without bothering with the details of the implementation, and to
easily switch between different algorithms.

MCFClass defines and "exports" the types of "flows" (MCFClass::FNumber),
"costs" (MCFClass::CNumber) and so on, together with a set of comparison
operators (ETZ, GTZ, ...) which automatically detect whether or not the
underlying types are integers or floats, inserting appropriate "epsilons" in
the latter case and avoiding them (for speed) in the former; these things are
sorted out at compile time without user intervention.

This release comprises:

-  docs/: HTML doxygen documentation, also available at

    https://frangio68.github.io/Min-Cost-Flow-Class/

-  doxygen/: doxygen files to produce the documentation

-  Main/: contains two example Main files to use the library. One solves
   a given MCF instance with any one MCF solver, which can be chosen by
   just changing two lines of code. The other compares the results of two
   solvers in order to verify that they are correct

-  MCFClass/: definition of the base class

-  MCFClone/: implements a "fake" MCF solver that takes two "real" ones
   and does everything on both; useful for testing the solvers (either for
   correctness or for efficiency) when used within "complex" approaches

-  MCFCplex/: implements a MCF solver conforming to the MCFClass interface
   based on calls to the commercial (but now free for academic purposes)
   Cplex solver from IBM

-  MCFSimplex/: implements a MCF solver conforming to the MCFClass interface
   based on the primal and dual revised network simplex algorithm

-  SPTree/: implements a MCF solver partly conforming to the MCFClass
   interface, in the sense that is is only able to solve MCF instances that
   are in fact Shortest Path Tree ones (that is, only one source node and
   no arc capacities), but then does so using SPT algorithms (both
   label-setting and label-correcting variants can be used) that are much
   faster than complete MCF ones

-  pyMCFSimplex-0.9/: a Python-Wrapper for the MCFSimplex solver by Johannes
   from the G#.Blog, check the README.txt for details

To install the file, go into Main and type "make". If you want to use the
MCFCplex class, which comes commented out by default, uncomment it from
lib/makefile and edit extlib/makefile-libCPX to insert the right Cplex path
libraries.

This code is provided free of charge under the "GNU Lesser General Public 
License". There are actually three more complete solvers available under the
MCFClass interface, namely RelaxIV, CS2 and MCFZIB. These are, however,
distributed under a more restrictive academic license, which has to be
explicitly accepted before getting hold of the code. Request forms are available
at

  http://www.di.unipi.it/optimize/Software/MCF.html

More information about (some of) the implemented algorithms can be found at

  http://pages.di.unipi.it/frangio/abstracts.html#JOC06

A further solver, MCFIntPnt (based on Interior-Point algorithms) has been 
developed, but it has not yet reached a sufficient maturuty to be distributed;
its principles are discussed at

  http://pages.di.unipi.it/frangio/abstracts.html#SIOPT04
  http://pages.di.unipi.it/frangio/abstracts.html#COAP06
  http://pages.di.unipi.it/frangio/abstracts.html#OMS06

