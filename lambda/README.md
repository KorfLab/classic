Lambda
======

## Nucleotides ##

Write a program that estimates lambda for nucleotide scoring schemes. The
parameters of the program should include:

- match score
- mismatch score
- probabilities of nucleotides
- precision (e.g. 1e-6) of lambda estimate

Now that you have lambda, you can make other calculations:

- calculate H (Sum Qij * e ^ (lambda * Sij))
- calculate percent identity (Sum Pi * Pj * e ^ (lambda * Sij) match-only)

## Amino Acids ##

Do the same as above, but for amino acids. For this problem use the BLOSUM62
scoring matrix (or another if you prefer). Here, the parameters are:

- scoring matrix
- probabilities of amino acids
- precision

Post-lambda calculations:

- H
- percent identity
- percent similarity (count positive scores)
