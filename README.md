The KorfLab Classics
====================

Suppose you've got some programming skills and want to practice those in a
bioinformatics setting. What should you do? Learn from the classics! Here are a
bunch of problems that are sort of the sequel to MCB185. If you haven't
completed the MCB185 course, you might want to do that first.

To begin, fork the repo so you can `git push` to your own copy. See the
`REAMDE.md` in each project directory. Here are some suggestions.

- Work with others, but you should be able to do these on your own
- All programs should have a proper CLI
- Programs should not have hard-coded paths or values
- Programs should write to stdout mostly
- Try to limit imports to the essentials
- Follow the style guide

## Contents ##

- 01-randomseq
- 02-fasta
- 03-seqstats
- 04-dust
- 05-transmembrane
- 06-translate

## 01-randomseq ##

Write a program that writes random sequence files in FASTA format. There should
be command line options for type of sequence (nucleotide or protein), number of
sequences, and lengths of sequences. Lines should wrap at 80 characters by
default. For nucleotide sequences, the default should be 25% each, but users
should be able to override these with their own values. For proteins, the
default should be 5% each amino acid, but users should be able to specify a
custom value such as `--ecoli` for E. coli values.

## 02-fasta ##

Make a function that reads FASTA files. You'll need this in just about every
program, so make a good function.

- The function should be imported by other programs, not copy-pasted
- The function should read multi-sequence files
- The function should be able to read compressed files and stdin
- Ideally, the function should not read all of the sequences into memory

For practice, see the following files in the `data` directory.

- E. coli...
- Something else...


## 03-seqstats ##

Write a function that reports various statistics about a FASTA file.

- Total number of sequences and letters
- Mean, median, and N50 of sequence lengths
- Frequencies of each letter
- When given the `codon` option, it reports codon usage

## 04-dust ##

Write a low-complexity filter for nucleotide sequences. The output should be a
FASTA file. By default, low-complexity regions should be masked with Ns but you
should provide a command line switch for lowercase masking (often called
soft-masking).

## 05-transmembrane ##

Write a program that finds transmembrane proteins.

## 06-translate ##

Write a program that translates sequences. In `--rna` mode, it finds the
longest protein in each sequence and reports this as the encoded protein. By
default, the program should translate the top strand, but there should be a
switch that allows proteins to exist on either strand. In `--orf` mode, the
program reports all open reading frames greater than some threshold length.f

## 07-featureseq ##

Write a program that reads a FASTA file and GFF file, and reports specific
features of the GFF in FASTA format. For example, if a user wants `exon`, then
the program reports the sequences of all exons in FASTA format. There should be
an option `--plus` to convert all sequences to the plus strand.




- Data Structures
	- Vector
	- Dictionary
- File Parsers - reading stuff into tidy data structures
	- GFF and other line-based records
	- GenBank and other weird flat-files
	- BLAST reports
	- FASTA files
	- Scoring matrices
	- Phylogenetic trees
	- Jaspar
	- JSON
- Patterns


- Regex something
- PWM
- Markov model
- Smith-Waterman
- Viterbi

----


- atg - build a pwm and assess its accuracy
- blast - run blast, parse the output, estimate lambda
- cds - translate the longest ORF in an mRNA
- concensus - make an optimal concensus sequence
- imeter - re-implement the imeter and historical studies
- sw - write Smith-Waterman and variants
- viterbi - write a Viterbi decoder for hidden Markov models
