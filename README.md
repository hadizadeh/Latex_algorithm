# LATEX Tips and Tricks
**PROBLEM 1:** How one can remove the algorithm number in the caption of an algorithm?

**SOLUTION:** Add `\renewcommand{\thealgorithm}{}` after `\begin{algorithm}`

> ##### See the sample Latex file [algorithm_caption_no_number.tex](Latex/algorithm_caption_no_number.tex) and [its PDF output](Latex/algorithm_caption_no_number.pdf)

``` 
\documentclass[11pt]{article}
\usepackage{algorithmicx}
\usepackage{algorithm}
\usepackage{algpseudocode}

\begin{document}

\begin{algorithm}
\renewcommand{\thealgorithm}{}
\caption{Test Algorithm}\label{euclid}
\begin{algorithmic}[1]
\Procedure{Euclid}{$a,b$}\Comment{The g.c.d. of a and b}
  \State $r\gets a\bmod b$
    \While{$r\not=0$}\Comment{We have the answer if r is 0}
      \State $a\gets b$
      \State $b\gets r$
       \State $r\gets a\bmod b$
       \EndWhile\label{euclidendwhile}
       \State \textbf{return} $b$\Comment{The gcd is b}
       \EndProcedure
\end{algorithmic}
\end{algorithm}

\end{document}
```



**PROBLEM 2:** How one can remove the line number in the body of an algorithm?

**SOLUTION:**
1. Define a new command:
`\def\NoNumber#1{{\def\alglinenumber##1{}\State #1}\addtocounter{ALG@line}{-1}}`
2. Put the content of the line, desiring no line number, in the `\NoNumber{}`

> ##### See the sample Latex file [algorithm_line_no_number.tex](Latex/algorithm_caption_no_number.tex) and [its PDF output](Latex/algorithm_caption_no_number.pdf)

```
\documentclass[11pt]{article}
\usepackage{algorithmicx}
\usepackage{algorithm}
\usepackage{algpseudocode}
\usepackage{color}

\def\NoNumber#1{{\def\alglinenumber##1{}\State #1}\addtocounter{ALG@line}{-1}}

\begin{document}

\begin{algorithm}
\caption{Test Algorithm}\label{euclid}
\begin{algorithmic}[1]
\Procedure{Euclid}{$a,b$}\Comment{The g.c.d. of a and b}
  \State $r\gets a\bmod b$
    \While{$r\not=0$}\Comment{We have the answer if r is 0}
      \State $a\gets b$
      \State $b\gets r$
       \State $r\gets a\bmod b$
       \EndWhile\label{euclidendwhile}
       \State \textbf{return} $b$\Comment{The gcd is b}
        \NoNumber{\color{red} This line will not have a number!}
       \EndProcedure
\end{algorithmic}
\end{algorithm}

\end{document}
```


