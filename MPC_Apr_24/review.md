# PEPit: computer-assisted worst-case analyses of first-order optimization methods in Python
## Technical Editor Report

### Summary
The revised manuscript addresses the concerns I had in my previous review. I thank the authors for their willingness to make these changes which (in my opinion at least) improve the package and the accompanying paper.

### Minor Comments

Section 3 does a good job of summarizing how the SDP is constructed from various aspects of the PEP. However, this section has numerous awkward phrasings. I recommend that the authors give one final careful review of the grammar of this manuscript, so that the important concepts presented are not obscured by awkward phrasing. What follows are some of the issues that I found in new Section 3.

- p10, 1st paragraph of section 3: remove "precisely"

- p11, "That is, PEPit parses more naturally... " This sentence is missing something. Perhaps, "That is, PEPit parses mathematical objects in a format which is more natural to the user."

- p11, "For doing that, ..." This is an awkward phrasing which occurs multiple times. "To achieve this goal, ..." is a better alternative.

- p11, "... is as follows, which we detail in the next lines:". "is as follows" and "which we detail in the next lines" say the same thing. Remove one of them.

- p12, "For formulating the objective", Change to "To formulate the objective..."

- p12, "together for forming PEPit.Constraint ...". Change to "together to form PEPit.Constraint ..."

- p13, "those structures were thought for being able ". Change to "those structures were motivated by being able to "

- p13, "Function are also featured ...". Change to "Functions also feature a number of aliases ..."

- p14, "However, for simplifying the usage of ...". Change to "However, to simplify the use of PEPit,"

- p14, "Once the functions are features with the appropriate list of points corresponding to the sample versions". I don't understand what this means. Could you clarify?

- p18, "For doing that ...". Change to "To do that "

- p18, "For modeling (11) ... " Change to "To model (11) ..."

- p18, "... index sets for framing the problem ... ". Change "... index sets to model the problem ... "

- p19, I think the word, "autonomously" implies that PEPit has some sort of intelligence. I think "automatically" would be more appropriate here.

- p19, "Besides, each dual value ...". Please remove "Besides" here. It's not clear what it's references.

- p19, "Points'names". You're missing a space.

- p22, "as badly as possible". Change to "as poorly as possible with respect to the given performance metrics".


