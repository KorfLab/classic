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

Here are some typical values:

| Match | Mismatch | Lambda | H      | Percent |
|-------|----------|--------|--------|---------|
| +1    | -1       | 1.0986 | 0.5493 | 75.00   |
| +1    | -2       | 1.3327 | 1.1241 | 94.78   |
| +1    | -3       | 1.3741 | 1.3072 | 98.78   |
| +5    | -4       | 0.1915 | 0.3567 | 65.14   |

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

Here are some values for common scoring matrices:

| Matrix   | Lambda | H      | Ident | Simil |
|----------|--------|--------|-------|-------|
| BLOSUM45 | 0.2248 | 0.2357 | 23.85 | 41.88 |
| BLOSUM62 | 0.3174 | 0.3905 | 30.08 | 48.80 |
| BLOSUM80 | 0.2268 | 0.6219 | 39.51 | 57.93 |