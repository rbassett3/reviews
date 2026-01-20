# Algorithms for Projection onto the Top-$k$-sum Constraint
## Technical Editor Report

### Summary
This manuscript proposes two new algorithms to compute the projection onto the Top-$k$-sum constraint, i.e. a constraint of the form
$$\sum_{i=1}^{k} \overleftarrow{x}_{i} \leq r$$
where $\overleftarrow{x}$ denotes the vector $x$ sorted so that its elements are nonincreasing. The first of these algorithms is a parametric linear complementary problem method and the second is a modification of the grid search proposed in the paper's reference [33] which refines the grid search strategy presented there. Theoretically, the benefit of these algorithms is that they are both O(n) complexity, where $n$ is the size of the vector $x$. Notably, the constant in this complexity bound is independent of $k$, which is not the case for the grid search method in [33]. Computationally, both of the proposed method outperform the reference in [33]. As technical editor, I focused my efforts on reviewing the software provided and the numerical experiments conducted. I did not read the proofs of the theorems and cannot attest to their accuracy.

### Recommendation

I found this paper well-written, the code high-quality, and the experiments honestly conducted. For these reasons, I recommend this paper be accepted. The improvements that I recommend are minor, and do not affect the paper's correctness.

### Details

I reviewed the code and reproduced the numerical experiments conducted by the authors. The code is well-written and I thank the authors for providing clean and well-documented methods to reproduce the experiments.

One possible issue that concerned me is that the authors implemented the method in [33], their primary competitor, themselves. In projection.jl, the implementation for the GRID search method from [33] includes some redundant code (lines 697-714) which does add unnecessary computational load to the method. The performance difference was relatively inconsequential given the extent of the enhancement in the ESGS method. Otherwise, the implementation matches the algorithm described in [33] and has many of the same performance enhancements (i.e. the @simd and @inbounds julia macros) as in the implementation of the authors own methods, so my impression is that this comparison is an honest one.

For the sake of this review, I focused my efforts on reproducing the $n=10^{5}$ column of experiments 1-6 in table 1. On the virtual machine provided by MPC, each method was ~50% slower than the numbers provided by the authors **except** for GRBS, which was ~25% faster on the virtual machine. These differences are mostly attributable to hardware differences; they are relatively minor and do not change the overall narrative presented by the authors. The primary difference between my implementation and the authors analysis' is that I conducted each experiment in serial, whereas the authors ran 2 experiments in parallel as they looped through the experiments. The VM provided by MPC has 16 *virtual* cores and 8 *physical* cores, and for the Gurobi experiments each run is allowed 8 virtual cores. I suspect the explanation for the different trend in GRBS is that Gurobi is highly optimized and does not benefit from hyperthreading for the sorted problem formulated in GRBS.

### Minor Comments

- The optimization problem in (2) introduces a lot of new notation packed into a single paragraph. This notation is never referenced again in the paper. Is it possible to slim down this paragraph to permit the literature review without burdening the reader with introducing a bunch of new, briefly used, notation?

- In Notation and preliminaries: The sentence before expression (3) needs a $\forall k$ quantifier. Would you also please clarify why two strict inequalities are possible in (3)? For example, what if $x$ is the ones vector?

- It's more clear to say that the algorithm is O(n) with respect to floating point operations (in contrast to say, memory usage). Suggest clarifying this point at least once in the paper.
