maxClique
=========

Algorithms for the maximum Clique Problem

(at present) There are 3 directories

 (1) java-* this is the java code for my maximum clique programs along
     with jobs to run DIMACS experiments
 (2) DIMACS_cliques is the 66 DIMACS clique benchmarks
 (3) DIMACS_results is the results of running my programs on my machine

What algorithms are there?
--------------------------
MCQ  is Tomita's 2003 algorithm
MCSa is a half-way-house between Tomita's MCR and MCS
MCSb is MCSa with colour repair and that is Tomita's MCS
BBMC is a BitSet encoding of San Segundo's 2011 algorithm

What variants do we have?
-------------------------
For MCQ, MCSa, MCSb and BBMC we have 3 different orderings at the top of search

  1: non-increasing degree
  2: minimum width order ("smallest-last")
  3: non-increasing degree tie-breaking on sum of 
     neighbouring degree (as in Tomita's MCR)

Therefore we have: MCQ1, MCQ2, MCQ3, MCSa1, MCSa2, MCSa3, 
MCSb1, MCSb2, MCSb3, BBMC1, BBMC2 and BBMC3

NOTE: MCQ3 is Tomita's MCR

How do I compile the code?
-------------------------
In the java-* directory

  > javac *.java

How do I run the code?
----------------------
 
  > java MaxClique MCQ1 ../DIMACS_cliques/brock200_1.clq 100

will run MCQ with non-decreasing degree ordering on the DIMACS instance, limiting cpu time to 100 seconds

  > java MaxClique MCQ1 ../DIMACS_cliques/brock200_1.clq

will run MCQ with non-decreasing degree ordering on the DIMACS instance, with no cpu time limit

  > java MaxClique MCSa2 ../DIMACS_cliques/brock200_2.clq

will run MCSa with a minimum width ordering on another DIMACS instance, no cpu limit

Generally

  > java MaxClique alg fname limit

where alg is one of {MCQ1, MCQ2, MCQ3, MCSa1, MCSa2, MCSa3, MCSb1, MCSb2, MCSb3, BBMC1, BBMC2, BBMC3}
fname is the name of a problem in DIMACS format and limit is an optional cpu time limit in seconds

What is the output?
------------------

  > java MaxClique MCSa2 ../DIMACS_cliques/brock200_1.clq
    21 301726 3211
    18 20 39 68 73 81 85 87 90 92 93 94 102 108 134 135 136 142 150 178 186 

The first line is size of clique (21), number of nodes (301726), cpu time in milliseconds (3211), and
on the next line a largest clique found (18 20 39 ... 178 186) .... and a "node" is the number of recursive
calls made during search.

What are the files dimacsJob*?
------------------------------
These will run the algorithms against the 66 problems in the DIMACS suite producing results in 
the DIMACS_results directory. All runs are limited to 4 hours cpu.

Tell me about the DIMACS_results
--------------------------------
There is one file for each algorithm applied to each problem (66).
The algorithms were compiled and run using java 1.6.0_07 and the experiments run on a machine 
with two Intel E5620 2.4GHz quad-core processors with 48 GB of memory, running linux centos 5.3. 
Algorithims were run with a 4 hour cpu time limit

What are the files 10-50-00 and 70-90-00?
-----------------------------------------
These are random graphs. 10-50-00 has 10 vertices and edge probability 0.5 and 70-90-00
has 70 vertices and edge probability 0.9. These were produced using the program RandomGraph

  > java RandomGraph 100 0.9 > 100-90-00

will produce a random graph with 100 vertices, edge probability 0.9  

What is MC and MC0?
-------------------
These are the simplest and slowest algorithms, akin to those givin in Fahle's paper of 2003.
MC0 is a faster version of MC, just to illustrate how Java can lead us to inefficient code.
You can run these as above (using MaxClique)

Are there any warning etc?
--------------------------
Yes. There is no guarantee with this code. Please do not distribute this code.
If someone else wants to use it ask them to contact me



Patrick Prosser (pat@dcs.gla.ac.uk)
10/07/2012

