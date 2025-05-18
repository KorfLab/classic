The KorfLab Classics
====================

Suppose you've got some programming skills and want to practice those in a
bioinformatics setting. What should you do? Learn by writing some classic
bioinformatics command-line software. You should complete MCB185 or the
equivalent before tackling these problems. Also, you should try programming
these in more than one language. To begin, fork the repo so you can `git push`
to your own copy.

- Teaming up is good, but you should be able to do these on your own
- All programs should have a proper CLI
- Programs should not have hard-coded paths or values
- Programs should write to stdout mostly
- Limit imports to the standard library
- Follow the style guide for your language

## Contents ##

1. Sequences
	- randomseq
	- readfasta
	- seqstats
	- dust
	- transmembrane
	- translate
	- featureseq
2. Files
	- blast
	- genbank
	- vcf
	- transfac
- Alignments
	- blosum
	- lambda
	-
- Patterns
	- pwm
	-
- Trees

## randomseq ##

Write a program that outputs random sequences in FASTA format. There should be
command line options for type of sequence (nucleotide or protein), number of
sequences, and lengths of sequences. Lines should wrap at 80 characters by
default. For nucleotide sequences, the default should be 25% each, but users
should be able to override these with their own values. For proteins, the
default should be 5% each amino acid, but users should be able to specify a
custom value such as `--ecoli` for E. coli values.

## readfasta ##

Make a function that reads FASTA files. Use this function for all of your
programs that read FASTA files.

- `import` into programs, do not copy-paste
- Reads multi-sequence files
- Reads compressed files and stdin
- Should have a minimal memory footprint

For practice, see the following files in the `data` directory.

- E. coli...
- Something else...


## seqstats ##

Write a function that reports various statistics about a FASTA file.

- Total number of sequences and letters
- Mean, median, and N50 of sequence lengths
- Frequencies of each letter
- When given the `codon` option, it assumees CDS and reports codon usage

## dust ##

Write a low-complexity filter for nucleotide sequences. The output should be a
FASTA file. By default, low-complexity regions should be masked with Ns but you
should provide a command line switch for lowercase masking (often called
soft-masking).

## transmembrane ##

Write a program that finds transmembrane proteins.

## translate ##

Write a program that translates sequences. In `--rna` mode, it finds the
longest protein in each sequence and reports this as the encoded protein. By
default, the program should translate the top strand, but there should be a
switch that allows proteins to exist on either strand. In `--orf` mode, the
program reports all open reading frames greater than some threshold length.f

## featureseq ##

Write a program that reads a FASTA file and GFF file, and reports specific
features of the GFF in FASTA format. For example, if a user wants `exon`, then
the program reports the sequences of all exons in FASTA format. There should be
an option `--plus` to convert all sequences to the plus strand.




- Data Structures
	- Vector
	- Dictionary
- File Parsers - reading stuff into tidy data structures
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
- genes from GFF
- SQL
- XML

----


- atg - build a pwm and assess its accuracy
- blast - run blast, parse the output, estimate lambda
- cds - translate the longest ORF in an mRNA
- concensus - make an optimal concensus sequence
- imeter - re-implement the imeter and historical studies
- sw - write Smith-Waterman and variants
- viterbi - write a Viterbi decoder for hidden Markov models
