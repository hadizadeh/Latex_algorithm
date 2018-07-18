# LATEX Tips and Tricks
**PROBLEM 1:** How one can remove the algorithm number in the caption of an algorithm?

**SOLUTION:** Add \renewcommand{\thealgorithm}{} after \begin{algorithm}

**PROBLEM 2:** How one can remove the line number in the body of an algorithm?

**SOLUTION:**
- Define a new command:
\def\NoNumber#1{{\def\alglinenumber##1{}\State #1}\addtocounter{ALG@line}{-1}}
- Put the content of the line, desiring no line number, in the \NoNumber{}



**SEE THE SAMPLE LATEX FILES**
