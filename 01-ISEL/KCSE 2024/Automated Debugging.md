### Paper 1
[APR from Fuzzing Perspective](http://www.jooyongyi.com/papers/ISSTA23.pdf), ISSTA '23

Problem:
APR: the # of patches between generation & validation is too large
The ranks of the correct patches needs tremendous time (executions till the correct patch)

comparing to fuzzing.. fuzzing's inputs are updated for every input execution result

deterministic vs stochastic

applying the fuzzing input selection algorithm (levitating execution results), to the patch validation selection of APR tools

interesting patch: passes at least one test case (importance of test cases + fixes direction)

increases the patch tree nodes that go toward the interesting patches

so how is the initial patch selected?
left-most vs random
* may contain info
* loses purpose when traversing rightwise
used epsilon-greedy algorithm

RQ1: AMAP, ASAP
compares its results with GenProg
* genprog uses random

RQ2: valid-ness
use DiffTGen with ground-truth to find acceptable patches

RQ3: generalizability
tests on a different benchmark

#### Related works
SeAPR: [Towards Boosting Patch Execution On-the-Fly](https://dl.acm.org/doi/pdf/10.1145/3510003.3510117), ICSE '22, Samuel Benton & Lingming Zhang
GenProg: [GenProg: A generic method for automatic software repair](https://web.eecs.umich.edu/~weimerw/p/weimer-tse2011-genprog-preprint.pdf), ICSE '12, Claire Le Goues
* [Automatically Finding Patches Using Genetic Programming](http://fricke.co.uk/Teaching/CS523_2013Spring/Presentations/GenProg.pdf)
* [A Systematic Study of Automated Program Repair: Fixing 55 out of 105 Bugs for $8 Each](https://engineering.purdue.edu/dcsl/reading/2013/pwood_genprog_DCSL.pdf)

### Paper 2
Bayesian **framework** (theoretical) for automated debugging

Axiomatic approach, builds up on assumptions
* shows its approach is compelling by comparing to one of the state-of-the-art SBFL techniques, Op1 & SeAPR
* Reason why it is a framework

#### Related works
unified debugging: SeAPR, Samuel Benton & Lingming Zhang

### Paper 3
Poracle

Dealing with overfitting in APR using testing

Among the generated numerous **plausible** patches, **filter out** incorrect patches

How to filter out?
1. ML, Dynamic analysis (compare execution path)
	1. how to determine threshold
2. evidence-based, give new input on patched program (can use fuzzing)
	1. what about non-crash-inducing incorrect patches?
