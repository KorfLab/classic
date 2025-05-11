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

