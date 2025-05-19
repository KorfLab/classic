The KorfLab Classics
====================

Aspiring bioinformatics programmers often ask me how they can improve their
skills. Like many other discliplines, a good place to start is by studying the
classics. Since bioinformatics is generally performed in a command line
Unix/Linux environment, you should have some familiarity with the CLI before
you begin. You also need to be a competent programmer. These things should be
familiar to you.

- Nested data structures
- File I/O
- Libraries
- CLI

Historically, most bioinformatics software was written in C or Perl. Today,
Python is a popular choice. Although less common, you may see some software
written in C++, Go, Java, Julia, Rust, etc. The langauge you use it up to you.
Good programmers know multiple languages. To begin, fork the repo so you can
`git push` to your own copy.

- All programs should have a proper CLI (e.g. argparse in Python)
- Programs should not have hard-coded paths or values
- Programs should generally write to stdout
- Minimize external dependancies
- Follow the style guide for your language

## Contents ##

- randomseq - generate random DNA and protein sequences
- readfasta - function to read FASTA files
- seqstats - provide statistics on FASTA files
- skewer - compute GC-skew and GC-composition in windows
- dust - mask low-complexity sequences
- translate - translate DNA to protein
- blosum - read a scoring matrix and compute its lambda
- nw - global alignment
- sw - local alignment
- splice - align a spliced sequence to it's genomic source
- featureseq - extract sequences from FASTA + GFF
- kmers - count kmers in a FASTA file
- imeter - reimplement the IMEter
- pwm - generate a position weight matrix from a FASTA file
- xpwm - assess performance of pwm using cross-validation
- mm - create an n-th order Markov model from a FASTA file
- xmm - assess performance of mm using cross-validation
- rafasta - provide random access to a fasta file
- readblast - read a BLAST report into a tidy data structure
- readsam - read a SAM file into a tidy data structure
- readgenome - read a FASTA + GFF into a genome data structure
- viterbi -

## randomseq ##

Write a program that outputs random sequences. The user must specify the number
and length of sequences, and their type: nucleotide or amino acid.

For nucleotides, the default should be 25% each letter, but there should be an
option to specify the individual frequencies. The output format should be FASTA
by default but FASTQ optionally (with a way for the user to set the quality
values).

For amino acids, the default frequencies should be some well-known proteome,
such as E. coli, and there should be a way for the user to specify some other
organism or clade. The output should be FASTA.

The FASTA identifier should be unique for each sequence, and there should be
some user-definable string on each identifier. Line lengths should be 80 by
default but this can be overridden with an option.

- https://en.wikipedia.org/wiki/FASTA_format

The programming here is very easy. The point of this exercise is to write a
simple yet thorough CLI.

## readfasta ##

Make a library that includes a function to read FASTA files. Use it for all of
your programs.

Reading FASTA files isn't particularly hard, but it can be done poorly. You
should not read the entire file into memory as some FASTA files can be huge.
Instead, you should read only one record at a time.

Many FASTA files are stored compressed, so being able to read a compressed file
is required, as is the ability to read from stdin.

Random access to records within a FASTA file is often very useful. This
behavior requires some sort of indexing and possibly persistent storage. Note
that you cannot `seek()` with stdin and doing so with a gzipped file is not
efficient.

## seqstats ##

Write a program that reports various statistics about a FASTA file.

- Total number of sequences and letters
- Mean, median, and N50 of sequence lengths
- Frequencies of each letter
- An option to report codon usage (assuming the sequences are all CDS)

## skewer ##

Write a program the computes windowed GC-skew and GC composition along a genome
sequence. The program should input FASTA and output BED. The program should
have a variable window size, and the window should be computed efficiently (do
not recompute each window).

## dust ##

Write a low-complexity filter for nucleotide sequences. The output should be a
FASTA file. By default, low-complexity regions should be masked with Ns but you
should provide a command line switch for lowercase masking (often called
soft-masking).

## translate ##

Write a program that translates sequences. In `--rna` mode, it finds the
longest protein in each sequence and reports this as the encoded protein. By
default, the program should translate the top strand, but there should be a
switch that allows proteins to exist on either strand. In `--orf` mode, the
program reports all open reading frames greater than some threshold length.

## blosum ##

## nw ##

## sw ##

## splice ##

## featureseq ##

Write a program that reads a FASTA file and GFF file, and reports specific
features of the GFF in FASTA format. For example, if a user wants `exon`
features, then the program reports the sequences of all exons in FASTA format.
There should be an option `--plus` to convert all sequences to the plus strand.

## kmers ##

## imeter ##

## pwm ##

## xpwm ##

## mm ##

## xmm ##

## rafasta ##

## readblast ##

## readsam ##

## readgenome ##


-----------------------------------------------------------------------------




- Vector
- Dictionary
- Patterns
- Regex something
- PWM
- Markov model
- Smith-Waterman
- Viterbi
- genes from GFF
- SQL
- XML



- atg - build a pwm and assess its accuracy
- blast - run blast, parse the output, estimate lambda
- cds - translate the longest ORF in an mRNA
- concensus - make an optimal concensus sequence
- imeter - re-implement the imeter and historical studies
- sw - write Smith-Waterman and variants
- viterbi - write a Viterbi decoder for hidden Markov models

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


----

Position Weight Matrix
======================

Position weight matrices are a simple yet useful model for small sequences
patterns (usually nucleotides). In this unit, we'll make PWMs for the donor and
acceptor sites.

## Real Sites ##

The `class/imeter` unit has some intron data. Use that to get the sequences of
donor and acceptor sites. There are a couple issues to consider:

- length of each site
- duplicate sites (exact same sequence twice)
- non-canonical sites (i.e. do not follow the GT-AG rule)

At first, let's use a length of 5 for the donor site, 6 for the acceptor site.
Later, we will want to try other sizes. Some of the splice sites may be
non-caonical (i.e. do not follow the GA-AG rule). Skip those. Save these sites
as FASTA files.

- `acc.fa` splice acceptor sites, 6 nt long
- `don.fa` splice donor sites, 5 nt long

From these fasta files, make PWMs from each.

- `acc.pwm`
- `don.pwm`

You should end up with something like this. Your file might look a little
different (perhaps you prefer json).

Donor

```
   A     C     G     T
1 0.000 0.000 1.000 0.000
2 0.000 0.000 0.000 1.000
3 0.657 0.049 0.123 0.171
4 0.534 0.139 0.058 0.269
5 0.207 0.095 0.494 0.204
```

Acceptor

```
   A     C     G     T
1 0.195 0.139 0.148 0.517
2 0.166 0.112 0.105 0.617
3 0.261 0.088 0.375 0.276
4 0.073 0.634 0.008 0.285
5 1.000 0.000 0.000 0.000
6 0.000 0.000 1.000 0.000
```

How well do these PWMs work for discriminating splice sites? To answer that
question, we need to apply it to real and fake examples and determine how well
it does on each.

## Fake Sites ##

What exactly is a fake splice site? Is it any place in a genome that is not a
known splice site? But what about alternative splicing? For the purposes of
this study, let's use GTs and AGs from the opposite strand as fake sites. They
have the same intron-like composition of normal introns but are unlikely to be
used as real splice sites.

Create a fasta file of fake sites. Make the number of fake sequences equal to
the number of true sequences.

- `fake-acc.fa`
- `fake-don.fa`

## Training and Testing Sets ##

In order to evaluate how well a PWM works, we are not allowed to train and test
on the same data: we need to separate all of the data into disjoint training
and testing sets. Make a program that splits FASTA files.

You should end up with the following files.

- `acc+.fa` true acceptor sites
- `acc-.fa` fake acceptor sites
- `don+.fa` true donor sites
- `don-.fa` fake donor sites

# Evaluation ##




Build PWMs from the true sites.






## Cross-Validation ##

To test how well you PWM works, you have to train it on some data and test it
on some other data. The simplest is to train your PWM on half the data and test
it on the other half of the data. If you do that twice, swapping which one is
the training set and testing set, you are doing a 2-fold cross-validation.

