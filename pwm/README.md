Position Weight Matrix
======================

Position weight matrices are a simple yet useful model for sequences.

## Training ##

Make PWMs for the donor and acceptor sites using the introns from
`class/imeter`. You should write functions that create the PWMs and also
functions that print them out. You should find something like this:

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

## Testing ##





## Fake Sites ##

To make a discriminator, you will need both true sites and fake sites. What
exactly is a fake splice site? You have several choices:

- Randomly generated
- Any site with a GT (or AG) that isn't real?
  - Are other GT sites in introns sometimes real donors?
  - What about other GT sites on the opposite strand?
  - What about intergenic sites?
  - What about coding sequence?

Depending on what you choose, you will get different answers.




## Cross-Validation ##

To test how well you PWM works, you have to train it on some data and test it
on some other data. The simplest is to train your PWM on half the data and test
it on the other half of the data. If you do that twice, swapping which one is
the training set and testing set, you are doing a 2-fold cross-validation.

