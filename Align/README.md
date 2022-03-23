Alignment HW
I tried both simple NJ and Parsimony using Rmd
```{r simple nj}
dna <- read.dna(file="fraserav1-aligned.fasta")
D <- dist.dna(dna, model="TN93")
tre <- nj(D)
tre <- ladderize(tre)
plot(tre1, cex=.6)
title("A simple NJ tree")
tre1 <- bionj(D)
tre1 <- ladderize(tre1)
plot(tre1, cex=.6)
title("A simple BIONJ tree")
```
```{r parsimony_frasera}
dna_f <- as.phyDat(dna)
#We need a starting tree for the search on tree space and compute the parsimony score of this tree (422)
tre.ini <- nj(dist.dna(dna,model="raw"))
parsimony(tre.ini, dna_f)
#Search for the tree with maximum parsimony:
tre.pars <- optim.parsimony(tre.ini, dna_f)
plot(tre.pars, cex=0.6)
title("A parsimony tree of frasera")
```

