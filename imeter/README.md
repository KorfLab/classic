imeter
======

- Read the papers
- Train the model
- Write the decoder
- Make the figures

## Manifest ##

- `tpc2000543.pdf` is the first publication
- `978-1-60327-563-7_14.pdf` is a good introduction to the guts of the IMEter
- `extract-introns-correctly.py` gets data for training
- `db_IME_Rose_WT_introns.fa` is the testing data
- `TAIR9_chr_all.fas.gz` is the genome sequence
- `Araport11_GFF3_genes_transposons.current.gff.gz` is all the genes

To get intron data for training, run `extract-introns-correctly.py`. It should
be pretty obvious how to do that. The data files on the official website have
errors. This script was sent to them to fix it, but who knows if they will.

