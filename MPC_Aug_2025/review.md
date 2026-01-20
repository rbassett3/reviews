# CALCULATION OF THE MAXIMUM PROBABILITY FIXED MARGINAL SUMS OF $r \times c$ CONTINGENCY TABLES
 
## Technical Editor Report

### Summary

This manuscript proposes a method to calculate maximum probability $r \times c$ contingency tables where the row and column sums of these tables are specified in advance. The primary motivation for this work is Fisher's Exact Test, a tool for conducting hypothesis tests on contingency table data. The *exact* nature of Fisher's Exact Test means that it computes the probabilities of receiving a given contingency table exactly. In large sample size settings, tests which rely on asymptotic approximations, such as Pearson's $\chi^2$ test, are often used instead. Therefore the motivating setting for this work is the case where the sample size is not large enough that asymptotic results are appropriate, but large enough so that Fisher's Exact Test is computationally burdensome. The authors connect Fisher's Exact Test to maximum probability tables through the network algorithm of Mehta and Patel. They then provide an algorithm for computing maximum probability tables. The first three sections of the paper provide background on maximum probability tables. The fourth introduces the proposed algorithm for computing maximum probability tables. The paper concludes with an Example section, a section on computing all maximum probability tables, and a short conclusion section. The authors provide accompanying Fortran code that implements the proposed algorithm to generate maximum probability table(s). The first program calculates one (of potentially many) maximum probability table after the row and column sums are given. The second calculates all maximum probability tables from an input of a maximum probability table.

### Recommendation

I agree that this paper is addressing an important problem in statistics by attempting to overcome computational limitations in Fisher's Exact Test. However, I believe this paper is a poor fit for MPC and should be rejected. My reasons for this decision are the following:

- The paper has an extremely limited set of computational experiments. These are in Section 7, the Conclusion section, and are anecdotal in nature. The code provided by the authors to the technical editor does not contain these experiments; it just provide a Fortran program that operates on an existing text file. I do not see where the competitor mentioned (Joe) has been implemented. The experimental results stated in the paper are not reproducible based on what the authors have provided.

- This paper is clearly written for an audience of Statisticians. There is no mention of any concepts in mathematical programming anywhere throughout the paper. They may be able to do so (for example, finding a Maximum Probability Table can obviously be viewed as an optimization problem), but any relevant optimization has been outsourced to references. So, despite the importance of the problem being addressed I think this manuscript will have very limited readership at MPC. 

- The code quality leaves a lot of be desired. The provided programs are written in Fortran 77 as opposed to a modern variant. They are poorly commented, use cryptic variable names, and are saturated with hard-to-read line jumps and gotos. I have used Fortran myself and I like the language, but these programs are ~1500 lines of code that embody many of the criticisms that are leveraged against legacy Fortran 77 code.

### Details

- The source code was not written in standard Fortran; I was not able to compile the Fortran source code with gfortran because there was a long list of errors. I was able to reverse engineer a vfproj file to find that the authors used Intel's ifxcompiler on Windows. Not everyone uses visual studio on Windows. I was able to compile and run the programs with ifx on my operating system. The first program (MPT) prompts users for row/column sums and writes a maximum probability table to a file. The second program (MPTs) prompts the user for a maximum probability table and writes all maximum probability tables with the row/column sums of the provided table to a file. I was able to run both programs. As input data, I plugged in small contingency tables that I found on Wikipedia, since the authors did not provide any test data. The programs gave the correct answers on the extremely small test problems I gave it.

- The Fortran program requires that $r \leq 11$ and $c \leq 30$. It's unclear where these restrictions come from.

- The authors say in Step 2 of Algorithm 1 that, in the context of rounding the values in the U table to a nearby contingency table, "If $u_{ij}$ is not an integer number, $x_{ij}$ could be $u_{ij}$ or $u_{ij} - 1$, in which case we will take the one which allows the column $j$ marginal of $X$ to be as close as possible to the proposed column $j$ marginal." The code provided doesn't do this--it just takes $x_{ij}$ to be the integer part of $u_{ij}$.

- In my assessment the code provided by the authors performs the algorithms defined in the paper. I do have some reservations though, because these programs are large Fortran 77 programs and it is possible I missed something minor. I would feel much more comfortable in my assertion if the details of how the authors used the competitor (Joe) mentioned in the paper were available, but the authors did not provide these details.
