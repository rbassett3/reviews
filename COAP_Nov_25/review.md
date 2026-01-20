# On the Convergence and Complexity of Proximal Gradient and Accelerated Proximal Gradient Methods under Adaptive Gradient Estimation
 
## Referee Report

### Summary

This manuscript considers the problem of minimizing an objective function which is the sum of two functions. One of these functions has an easy-to-compute proximal operator; the other is smooth and is an expected loss of a function with varying degrees of "nice" structure. In order to solve this problem, the authors consider a proximal gradient descent method and an accelerated variant. In this reviewer's opinion, the primary contribution of this paper is Lemma 2.2, where the authors show that the estimated gradient of the expected loss term satisfies a so-called norm condition (Condition 2.1) when the gradient estimate is formed as a sample average approximation from enough samples. In this result, having "enough samples" requires the sample size to depend inversely on the squared Euclidean norm of the reduced gradient, a quantity that approximates the step size in proximal gradient descent. This property motivates the author's use of the term "adaptive gradient estimation" in the manuscript's title, since the sample size depends on the iteration sequence. The authors spend the bulk of the paper showing that the sampling method proposed achieves the optimal number of proximal operator evaluations when the smooth term is nonconvex, convex, or strongly convex, and that when the gradient estimates are unbiased the methods also achieve optimal complexity with respect to the number of stochastic gradient evaluations required. The paper concludes with a small numerical experiment where the methods are applied to a strongly convex quadratic objective with a unit ball constraint.

### Recommendation

This paper provides a nice theoretical contribution to stochastic proximal gradient methods, and it is relevant to COAP's special issue on Machine Learning. However, many aspects of the paper should be streamlined to maximize their relevance to COAP readers. In particular, the numerical experiments are sparse and under-emphasized, while the bulk of the paper contains details complexity proofs for 12 slightly different  problem assumptions (2 for the type of expectation considered in (1.3) and (1.4), 2 for the variant of proximal gradient descent considered, and 3 for the nonconvex/convex/strong convex assumption on the smooth term). This is hard to get through as a reader. With respect to the mathematical content, I have no major concerns. For these reasons, I recommend **Major Revision**, so that the authors can improve the presentation of the paper and emphasize content appropriately for a COAP audience.

### Major Concerns

- Throughout, I find the dual consideration of (1.3) and (1.4) redundant. (1.3) is just a special case of (1.4) with a discrete uniform distribution on the data. The authors acknowledge this fact that at the end of section 2, writing that *some* of the results for (1.3) are suppressed. The entire manuscript would read more clearly if you instead focused on (1.4) and only considered (1.3) as a special case, or provided corollaries to important theorems that are specialized to this case. I am sympathetic to the idea that a Machine Learning audience cares about (1.3) instead of the general problem in (1.4), but this can be remedied by discussing (1.3) as a special case of (1.4) in the introduction and providing specialized corollaries as necessary.

- The option 1/option 2 language is less descriptive than it could be. Why not just call them the accelerated and non-accelerated variants?

- Put assumptions first for readability and transparency, as opposed to the current structure where assumptions are spread throughout section 2, requiring the reader to hunt for them.

- I found it difficult to parse Algorithm 2.1 when Step 2 (Compute a gradient estimate) has not yet been introduced. Am I supposed to know how to do this at this point? Algorithm 2.1 depends on Lemma 2.2. Recommend restructuring the presentation of Section 2 so that required aspects (e.g. gradient estimation and sampling) have been introduced before they are utilized in Algorithm 2.1.

- Theorem 3.3's consideration of both (1.3) and (1.4) is redundant.

- p 12. You say you are "using a definition of an $\epsilon$-accurate solution similar to that in [18]", but then don't provide it. What is this similar definition? Is is exactly the same as [18] or approximately the same? Is this related to the definition at the bottom of p 18? Same comment applies to "along with a definition of an $\epsilon$-accurate solution similar to that in [17]" on p 30. Are these the same "similar" definition?

- Theorem 3.8, with all its duplication, clearly demonstrates the awkwardness of the cases considered and the issue with considering (1.3) and (1.4) separately. The same comment applied to Theorem 3.15, where it takes an entire page to state the theorem because of all the duplicate text. This presentation needs to be streamlined.

- In Section 4, how does the sample size $|S_{k}|$ change throughout iterations? Place these data in a line graph for all the methods considered, to address the concern that you've just proposed a method and selected constants that lead to larger sample sizes. For self-containment of this paper, describe the "sample size selected using sampled estimates as described in [44]" instead of just outsourcing to [44].

- In Section 4, are there sources for these competing methods, that describe their implementation and/or theoretical properties with respect to number of proximal operator evaluations or stochastic gradient evaluations?

- For COAP readers, put Appendix C in the main body and streamline theory to deduplicate presentation and/or put more supporting Lemmas in the appendix. For the experiment in Appendix C, include a sample size line graph similar to the one requested for Section 4.
 
### Minor Concerns

- On p 6, the $\sigma$-algebra discussion is too informal. "A nested sequence of $\sigma$-algebras" is a common object to consider and is called a filtration, so it is better to refer to the sequence by this name than to re-invent it. Similarly, writing $\mathcal{G}_{k} = \{x_{0}, ..., g_{k-1}\}$ suggests that the $\sigma$-algebra is a set of random variables, when you mean to say that the $\sigma$-algebra is generated by a (set of) random variable(s). Clarify.

- Readers who are not familiar with this particular subfield's conventions may reasonably assume that $\mathrm{Var}[\nabla F]$ denotes a covariance matrix, since it's the variance of a random vector. That's not what you mean here, so make sure that you define this term.

- p 4, bottom. You say you denote norm with $|\cdot|$, but actually denote it with $\|\cdot\|$.

- p 7, top. Condition 2.1 has right-hand side**s** of the inequality, so this should be plural.

- p 7. double object "components gradients"

- p 7, Lemma 2.2. What does it mean for samples to be "independent of" a $\sigma$-algebra? Also, a *sample* from a random variable is typically a set of *observations* from a random variable.

- Capitalize Young in Young's inequality, throughout.

- Section 5 and throughout. I find the air-quoted "norm" condition too informal. Call it the norm condition and provide it with an \textbackslash eqref.

- Improper capitalization in bibliography (e.g. [15] and [17]).


