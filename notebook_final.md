1, Alignment
I used clustalw to align the sequences. 
I used ```$ ./clustalw2.exe -ALIGN -INFILE=sequence_final.fasta -OUTFILE=fraserav5_aligned_cl.nex -OUTPUT=NEXUS```to output a nexus file
I also used ```$ ./clustalw2.exe -ALIGN -INFILE=sequence_final.fasta -OUTFILE=fraserav5_aligned_cl.fasta -OUTPUT=PHYLP```to output a fasta file for IQtree.
 
This is the output of NEXUS:

```
 CLUSTAL 2.1 Multiple Sequence Alignments


Sequence format is Pearson
Sequence 1: Fpuberulenta     842 bp
Sequence 2: Fmontana         842 bp
Sequence 3: Falbicaulis      842 bp
Sequence 4: Fspeciosa2       842 bp
Sequence 5: Fcaroliniensis   842 bp
Sequence 6: Fspeciosa1       842 bp
Sequence 7: Swertia          774 bp
Start of Pairwise alignments
Aligning...

Sequences (1:2) Aligned. Score:  98
Sequences (1:3) Aligned. Score:  93
Sequences (1:4) Aligned. Score:  79
Sequences (1:5) Aligned. Score:  86
Sequences (1:6) Aligned. Score:  85
Sequences (1:7) Aligned. Score:  85
Sequences (2:3) Aligned. Score:  94
Sequences (2:4) Aligned. Score:  79
Sequences (2:5) Aligned. Score:  87
Sequences (2:6) Aligned. Score:  87
Sequences (2:7) Aligned. Score:  84
Sequences (3:4) Aligned. Score:  78
Sequences (3:5) Aligned. Score:  85
Sequences (3:6) Aligned. Score:  86
Sequences (3:7) Aligned. Score:  83
Sequences (4:5) Aligned. Score:  97
Sequences (4:6) Aligned. Score:  97
Sequences (4:7) Aligned. Score:  91
Sequences (5:6) Aligned. Score:  97
Sequences (5:7) Aligned. Score:  97
Sequences (6:7) Aligned. Score:  96
Guide tree file created:   [sequence_final.dnd]

There are 6 groups
Start of Multiple Alignment

Aligning...
Group 1: Sequences:   2      Score:14041
Group 2: Sequences:   3      Score:14100
Group 3: Sequences:   4      Score:13189
Group 4: Sequences:   2      Score:11951
Group 5: Sequences:   3      Score:11457
Group 6: Sequences:   7      Score:10593
Alignment Score 83505

NEXUS-Alignment file created    [fraserav5_aligned_cl.nex]
```
I also used Muscle to do alignment:
```
$ ./muscle5.1.win64.exe -align sequence_final.fasta -output fraserav6_ms.fasta

muscle 5.1.win64 [ddb630]  16.9Gb RAM, 8 cores
Built Jan 13 2022 15:30:12
(C) Copyright 2004-2021 Robert C. Edgar.
https://drive5.com

Input: 7 seqs, avg length 724, max 818

00:00 4.9Mb  CPU has 8 cores, running 8 threads
00:00 82Mb    100.0% Calc posteriors
00:00 13Mb    100.0% Consistency (1/2)
00:00 8.1Mb   100.0% Consistency (2/2)
00:00 5.8Mb   100.0% UPGMA5
00:01 6.8Mb   100.0% Refining
```
2, IQtree

```
bin/iqtree -s fraserav5_aligned_cl.fasta -bb 1000 -redo
IQ-TREE multicore version 1.6.12 for Windows 64-bit built Aug 15 2019
Developed by Bui Quang Minh, Nguyen Lam Tung, Olga Chernomor,
Heiko Schmidt, Dominik Schrempf, Michael Woodhams.

Host:    DESKTOP-183TNGN (AVX512, FMA3, 15 GB RAM)
Command: C:\Users\75180\Bot563\tree\bin\iqtree.exe -s fraserav5_aligned_cl.fasta -bb 1000 -redo
Seed:    210634 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Mon May 09 21:51:35 2022
Kernel:  AVX+FMA - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file fraserav5_aligned_cl.fasta ... Phylip format detected
Alignment most likely contains DNA/RNA sequences
Alignment has 7 sequences with 842 columns, 116 distinct patterns
59 parsimony-informative, 48 singleton sites, 735 constant sites
            Gap/Ambiguity  Composition  p-value
   1  Fspeciosa2    9.74%    passed     99.09%
   2  Fspeciosa1    6.65%    passed     97.87%
   3  Fcarolinie    2.85%    passed     99.72%
   4  Swertia       8.08%    passed     91.96%
   5  Fpuberulen   23.87%    passed     80.19%
   6  Fmontana     24.11%    passed     90.78%
   7  Falbicauli   23.04%    passed     91.48%
****  TOTAL        14.05%  0 sequences failed composition chi2 test (p-value<5%; df=3)

NOTE: Restoring information from model checkpoint file fraserav5_aligned_cl.fasta.model.gz

CHECKPOINT: Initial tree restored
NOTE: ModelFinder requires 0 MB RAM!
ModelFinder will test 286 DNA models (sample size: 842) ...
 No. Model         -LnL         df  AIC          AICc         BIC
  1  JC            1793.442     11  3608.884     3609.202     3660.977
  2  JC+I          1792.915     12  3609.831     3610.207     3666.660
  3  JC+G4         1792.931     12  3609.862     3610.239     3666.692
  4  JC+I+G4       1793.089     13  3612.179     3612.618     3673.744
  5  JC+R2         1792.924     13  3611.848     3612.288     3673.414
  6  JC+R3         1792.924     15  3615.848     3616.430     3686.885
 14  F81+F         1754.827     14  3537.653     3538.161     3603.954
 15  F81+F+I       1754.147     15  3538.294     3538.875     3609.331
 16  F81+F+G4      1754.122     15  3538.244     3538.825     3609.281
 17  F81+F+I+G4    1754.235     16  3540.469     3541.129     3616.242
 18  F81+F+R2      1754.150     16  3540.300     3540.959     3616.072
 19  F81+F+R3      1754.150     18  3544.299     3545.130     3629.543
 27  K2P           1791.810     12  3607.620     3607.996     3664.449
 28  K2P+I         1791.349     13  3608.697     3609.137     3670.262
 29  K2P+G4        1791.351     13  3608.703     3609.142     3670.268
 30  K2P+I+G4      1791.565     14  3611.131     3611.639     3677.432
 31  K2P+R2        1791.351     14  3610.703     3611.211     3677.004
 32  K2P+R3        1791.351     16  3614.703     3615.362     3690.475
 40  HKY+F         1752.438     15  3534.876     3535.457     3605.913
 41  HKY+F+I       1751.863     16  3535.727     3536.386     3611.499
 42  HKY+F+G4      1751.817     16  3535.635     3536.294     3611.407
 43  HKY+F+I+G4    1752.002     17  3538.005     3538.748     3618.513
 44  HKY+F+R2      1751.841     17  3537.682     3538.424     3618.190
 45  HKY+F+R3      1751.841     19  3541.681     3542.606     3631.661
 53  TNe           1791.747     13  3609.494     3609.933     3671.059
 54  TNe+I         1791.278     14  3610.557     3611.065     3676.858
 55  TNe+G4        1791.284     14  3610.568     3611.076     3676.869
 56  TNe+I+G4      1791.482     15  3612.963     3613.544     3684.000
 57  TNe+R2        1791.283     15  3612.565     3613.146     3683.602
 58  TNe+R3        1791.283     17  3616.565     3617.308     3697.074
 66  TN+F          1752.422     16  3536.843     3537.503     3612.616
 67  TN+F+I        1751.847     17  3537.694     3538.436     3618.202
 68  TN+F+G4       1751.802     17  3537.603     3538.346     3618.111
 69  TN+F+I+G4     1751.979     18  3539.959     3540.790     3625.203
 70  TN+F+R2       1751.825     18  3539.650     3540.481     3624.894
 71  TN+F+R3       1751.825     20  3543.649     3544.672     3638.365
 79  K3P           1791.745     13  3609.489     3609.929     3671.054
 80  K3P+I         1791.274     14  3610.549     3611.056     3676.849
 81  K3P+G4        1791.282     14  3610.563     3611.071     3676.864
 82  K3P+I+G4      1791.467     15  3612.935     3613.516     3683.971
 83  K3P+R2        1791.279     15  3612.558     3613.139     3683.595
 84  K3P+R3        1791.279     17  3616.558     3617.301     3697.066
 92  K3Pu+F        1752.415     16  3536.831     3537.490     3612.603
 93  K3Pu+F+I      1751.844     17  3537.689     3538.432     3618.197
 94  K3Pu+F+G4     1751.794     17  3537.589     3538.332     3618.097
 95  K3Pu+F+I+G4   1751.973     18  3539.947     3540.778     3625.191
 96  K3Pu+F+R2     1751.820     18  3539.639     3540.470     3624.883
 97  K3Pu+F+R3     1751.819     20  3543.639     3544.662     3638.354
105  TPM2+F        1752.200     16  3536.401     3537.060     3612.173
106  TPM2+F+I      1751.636     17  3537.271     3538.014     3617.780
107  TPM2+F+G4     1751.568     17  3537.137     3537.880     3617.645
108  TPM2+F+I+G4   1751.769     18  3539.538     3540.369     3624.782
109  TPM2+F+R2     1751.601     18  3539.201     3540.032     3624.445
110  TPM2+F+R3     1751.600     20  3543.201     3544.224     3637.916
118  TPM2u+F       1752.200     16  3536.400     3537.060     3612.173
119  TPM2u+F+I     1751.636     17  3537.271     3538.014     3617.780
120  TPM2u+F+G4    1751.568     17  3537.137     3537.880     3617.645
121  TPM2u+F+I+G4  1751.766     18  3539.533     3540.364     3624.777
122  TPM2u+F+R2    1751.600     18  3539.201     3540.032     3624.445
123  TPM2u+F+R3    1751.600     20  3543.201     3544.224     3637.916
131  TPM3+F        1750.510     16  3533.019     3533.679     3608.792
132  TPM3+F+I      1749.832     17  3533.664     3534.406     3614.172
133  TPM3+F+G4     1749.794     17  3533.587     3534.330     3614.095
134  TPM3+F+I+G4   1749.899     18  3535.799     3536.630     3621.043
135  TPM3+F+R2     1749.829     18  3535.658     3536.490     3620.903
136  TPM3+F+R3     1749.828     20  3539.655     3540.678     3634.371
144  TPM3u+F       1750.510     16  3533.019     3533.679     3608.792
145  TPM3u+F+I     1749.832     17  3533.663     3534.406     3614.172
146  TPM3u+F+G4    1749.794     17  3533.587     3534.330     3614.096
147  TPM3u+F+I+G4  1749.898     18  3535.796     3536.627     3621.040
148  TPM3u+F+R2    1749.829     18  3535.658     3536.489     3620.902
149  TPM3u+F+R3    1749.827     20  3539.654     3540.677     3634.370
157  TIMe          1791.683     14  3611.366     3611.874     3677.667
158  TIMe+I        1791.205     15  3612.410     3612.991     3683.446
159  TIMe+G4       1791.216     15  3612.431     3613.012     3683.468
160  TIMe+I+G4     1791.376     16  3614.751     3615.411     3690.524
161  TIMe+R2       1791.212     16  3614.423     3615.082     3690.196
162  TIMe+R3       1791.211     18  3618.423     3619.254     3703.667
170  TIM+F         1752.399     17  3538.798     3539.541     3619.306
171  TIM+F+I       1751.828     18  3539.655     3540.486     3624.899
172  TIM+F+G4      1751.778     18  3539.557     3540.388     3624.801
173  TIM+F+I+G4    1751.942     19  3541.884     3542.808     3631.864
174  TIM+F+R2      1751.803     19  3541.607     3542.531     3631.586
175  TIM+F+R3      1751.803     21  3545.607     3546.733     3645.058
183  TIM2e         1791.594     14  3611.189     3611.697     3677.490
184  TIM2e+I       1791.090     15  3612.181     3612.762     3683.217
185  TIM2e+G4      1791.113     15  3612.226     3612.807     3683.263
186  TIM2e+I+G4    1791.234     16  3614.467     3615.127     3690.240
187  TIM2e+R2      1791.104     16  3614.209     3614.868     3689.981
188  TIM2e+R3      1791.104     18  3618.208     3619.039     3703.452
196  TIM2+F        1752.184     17  3538.368     3539.111     3618.876
197  TIM2+F+I      1751.619     18  3539.237     3540.068     3624.481
198  TIM2+F+G4     1751.552     18  3539.104     3539.936     3624.348
199  TIM2+F+I+G4   1751.735     19  3541.469     3542.394     3631.449
200  TIM2+F+R2     1751.584     19  3541.167     3542.092     3631.147
201  TIM2+F+R3     1751.583     21  3545.167     3546.294     3644.618
209  TIM3e         1787.691     14  3603.382     3603.890     3669.683
210  TIM3e+I       1787.040     15  3604.080     3604.662     3675.117
211  TIM3e+G4      1787.052     15  3604.103     3604.685     3675.140
212  TIM3e+I+G4    1787.108     16  3606.216     3606.876     3681.989
213  TIM3e+R2      1787.059     16  3606.119     3606.778     3681.891
214  TIM3e+R3      1787.059     18  3610.118     3610.949     3695.362
222  TIM3+F        1750.497     17  3534.995     3535.737     3615.503
223  TIM3+F+I      1749.820     18  3535.641     3536.472     3620.885
224  TIM3+F+G4     1749.782     18  3535.564     3536.395     3620.808
225  TIM3+F+I+G4   1749.877     19  3537.754     3538.679     3627.734
226  TIM3+F+R2     1749.817     19  3537.633     3538.558     3627.613
227  TIM3+F+R3     1749.816     21  3541.631     3542.758     3641.083
235  TVMe          1787.435     15  3604.870     3605.451     3675.907
236  TVMe+I        1786.733     16  3605.465     3606.125     3681.238
237  TVMe+G4       1786.761     16  3605.523     3606.182     3681.295
238  TVMe+I+G4     1786.777     17  3607.555     3608.298     3688.063
239  TVMe+R2       1786.771     17  3607.541     3608.284     3688.049
240  TVMe+R3       1786.769     19  3611.538     3612.462     3701.518
248  TVM+F         1750.062     18  3536.124     3536.955     3621.368
249  TVM+F+I       1749.395     19  3536.790     3537.714     3626.769
250  TVM+F+G4      1749.330     19  3536.659     3537.584     3626.639
251  TVM+F+I+G4    1749.455     20  3538.910     3539.933     3633.626
252  TVM+F+R2      1749.374     20  3538.748     3539.771     3633.464
253  TVM+F+R3      1749.372     22  3542.744     3543.980     3646.931
261  SYM           1787.382     16  3606.765     3607.424     3682.537
262  SYM+I         1786.678     17  3607.356     3608.099     3687.864
263  SYM+G4        1786.709     17  3607.417     3608.160     3687.926
264  SYM+I+G4      1786.720     18  3609.440     3610.271     3694.684
265  SYM+R2        1786.717     18  3609.433     3610.264     3694.677
266  SYM+R3        1786.714     20  3613.428     3614.451     3708.144
274  GTR+F         1750.049     19  3538.098     3539.023     3628.078
275  GTR+F+I       1749.381     20  3538.763     3539.786     3633.478
276  GTR+F+G4      1749.317     20  3538.633     3539.657     3633.349
277  GTR+F+I+G4    1749.440     21  3540.880     3542.007     3640.331
278  GTR+F+R2      1749.361     21  3540.721     3541.848     3640.173
279  GTR+F+R3      1749.358     23  3544.716     3546.066     3653.639
Akaike Information Criterion:           TPM3+F
Corrected Akaike Information Criterion: TPM3+F
Bayesian Information Criterion:         F81+F
Best-fit model: F81+F chosen according to BIC

All model information printed to fraserav5_aligned_cl.fasta.model.gz
CPU time for ModelFinder: 0.062 seconds (0h:0m:0s)
Wall-clock time for ModelFinder: 0.369 seconds (0h:0m:0s)
Generating 1000 samples for ultrafast bootstrap (seed: 210634)...

NOTE: 0 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -1754.827
Optimal log-likelihood: -1754.827
Rate parameters:  A-C: 1.00000  A-G: 1.00000  A-T: 1.00000  C-G: 1.00000  C-T: 1.00000  G-T: 1.00000
Base frequencies:  A: 0.352  C: 0.184  G: 0.180  T: 0.284
Parameters optimization took 1 rounds (0.008 sec)
Computing ML distances based on estimated model parameters... 0.000 sec
Computing BIONJ tree...
0.002 seconds
Log-likelihood of BIONJ tree: -1756.900
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 0.022 second
Computing log-likelihood of 36 initial trees ... 0.006 seconds
Current best score: -1754.827

Do NNI search on 20 best initial trees
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -1754.827
Iteration 10 / LogL: -1754.827 / Time: 0h:0m:0s
Iteration 20 / LogL: -1754.827 / Time: 0h:0m:0s
Finish initializing candidate tree set (1)
Current best tree score: -1754.827 / CPU time: 0.080
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
UPDATE BEST LOG-LIKELIHOOD: -1754.827
Iteration 30 / LogL: -1754.827 / Time: 0h:0m:0s (0h:0m:0s left)
Iteration 40 / LogL: -1754.922 / Time: 0h:0m:0s (0h:0m:0s left)
Iteration 50 / LogL: -1754.827 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -1765.944
Iteration 60 / LogL: -1754.827 / Time: 0h:0m:0s (0h:0m:0s left)
Iteration 70 / LogL: -1754.827 / Time: 0h:0m:0s (0h:0m:0s left)
Iteration 80 / LogL: -1754.827 / Time: 0h:0m:0s (0h:0m:0s left)
Iteration 90 / LogL: -1754.916 / Time: 0h:0m:0s (0h:0m:0s left)
Iteration 100 / LogL: -1754.827 / Time: 0h:0m:0s (0h:0m:0s left)
Log-likelihood cutoff on original alignment: -1765.028
NOTE: Bootstrap correlation coefficient of split occurrence frequencies: 1.000
TREE SEARCH COMPLETED AFTER 102 ITERATIONS / Time: 0h:0m:0s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -1754.827
Optimal log-likelihood: -1754.827
Rate parameters:  A-C: 1.00000  A-G: 1.00000  A-T: 1.00000  C-G: 1.00000  C-T: 1.00000  G-T: 1.00000
Base frequencies:  A: 0.352  C: 0.184  G: 0.180  T: 0.284
Parameters optimization took 1 rounds (0.009 sec)
BEST SCORE FOUND : -1754.827
Creating bootstrap support values...
Split supports printed to NEXUS file fraserav5_aligned_cl.fasta.splits.nex
Total tree length: 0.172

Total number of iterations: 102
CPU time used for tree search: 0.703 sec (0h:0m:0s)
Wall-clock time used for tree search: 0.811 sec (0h:0m:0s)
Total CPU time used: 0.750 sec (0h:0m:0s)
Total wall-clock time used: 0.921 sec (0h:0m:0s)

Computing bootstrap consensus tree...
Reading input file fraserav5_aligned_cl.fasta.splits.nex...
7 taxa and 15 splits.
Consensus tree written to fraserav5_aligned_cl.fasta.contree
Reading input trees file fraserav5_aligned_cl.fasta.contree
Log-likelihood of consensus tree: -1754.827

Analysis results written to:
  IQ-TREE report:                fraserav5_aligned_cl.fasta.iqtree
  Maximum-likelihood tree:       fraserav5_aligned_cl.fasta.treefile
  Likelihood distances:          fraserav5_aligned_cl.fasta.mldist

Ultrafast bootstrap approximation results written to:
  Split support values:          fraserav5_aligned_cl.fasta.splits.nex
  Consensus tree:                fraserav5_aligned_cl.fasta.contree
  Screen log file:               fraserav5_aligned_cl.fasta.log
```
3, Parsimony-likelyhood tree. 
In Rmarkdown file. 
```{r setup, include=FALSE}
library(ape)
library(adegenet)
library(phangorn)
```

```{r frasra apply phangorn example}
#data(Laurasiatherian)
#dm <- dist.hamming(Laurasiatherian)
#tree <- NJ(dm)
dna <- read.dna(file="fraserav5_aligned_cl.fasta")
dna_data=phyDat(dna, type = "DNA")#translate dna data into phyDat
D <- dist.dna(dna, model="raw")#calculate disdance
tre_f <- nj(D)#make neiborgh joining tree
# NJ
set.seed(123)
NJtrees <- bootstrap.phyDat(dna_data,
     FUN=function(x)NJ(dist.hamming(x)), bs=100)#make bootstrap
treeNJ <- plotBS(tre_f, NJtrees, "phylogram")#plot

# Maximum likelihood
fit <- pml(tre_f, dna_data)
fit <- optim.pml(fit, rearrangement="NNI")
set.seed(123)
bs <- bootstrap.pml(fit, bs=100, optNni=TRUE)
treeBS <- plotBS(fit$tree,bs)

# Maximum parsimony
treeMP <- pratchet(dna_data)
treeMP <- acctran(treeMP, dna_data)
set.seed(30)
BStrees <- bootstrap.phyDat(dna_data, pratchet, bs = 100)
treeMP <- plotBS(treeMP, BStrees, "phylogram")
add.scale.bar()
write.tree(treeMP, file="bootstrap_example.tre")
```

4, BEAST: 

a. BEAUti 2, imported fraserav5_aligned_cl.nex
Since the IQtree model selection found the model fits this data the best is F81+F, I set the substitution model as GTR and fixed all rate parameters to 1.0 (uncheck the "estimate" box) following the protocol from https://justinbagley.rbind.io/2016/10/11/setting-dna-substitution-models-beast/
Next,  Clock Model, I left the selection at the default value, because this taxa diversed relatively recent and does not need rate variation among branches to be included in the model.
Prior: I set Yule Mode, birthRateY.t:tree, for the first try I set the Alpha (shape) parameter to 0.1 and the Beta (scale) parameter to 1000. I added a hyperprior on both parameters of the Gamma prior by checking estimate. And I left all others default. 
MCMC: I set chain length 100,000, tracelog every 200, leave all others default. 
I saved the file as fraserav3_gamma.xml

I also used muscle alignment input. I set everything as default except I set site model as GTR + all the rates to 1 without estimate, MCMC chain length to 10,000
b. BEAST: 
I set seeds as 777
For ms, seed: 10000
output:
```
Random number seed: 777

Failed to load BEAGLE library: no hmsbeagle64 in java.library.path
Falbicaulis: 842 4
Fcaroliniensis: 842 4
Fmontana: 842 4
Fpuberulenta: 842 4
Fspeciosa1: 842 4
Fspeciosa2: 842 4
Swertia: 842 4
Alignment(fraserav5_aligned_cl)
  7 taxa
  842 sites
  116 patterns

TreeLikelihood(treeLikelihood.fraserav5_aligned_cl0) uses BeerLikelihoodCore4
  Alignment(fraserav5_aligned_cl): [taxa, patterns, sites] = [7, 116, 842]
===============================================================================
Citations for this model:

Bouckaert, Remco, Timothy G. Vaughan, Joëlle Barido-Sottani, Sebastián Duchêne, Mathieu Fourment, 
Alexandra Gavryushkina, Joseph Heled, Graham Jones, Denise Kühnert, Nicola De Maio, Michael Matschiner, 
Fábio K. Mendes, Nicola F. Müller, Huw A. Ogilvie, Louis du Plessis, Alex Popinga, Andrew Rambaut, 
David Rasmussen, Igor Siveroni, Marc A. Suchard, Chieh-Hsi Wu, Dong Xie, Chi Zhang, Tanja Stadler, 
Alexei J. Drummond 
  BEAST 2.5: An advanced software platform for Bayesian evolutionary analysis. 
  PLoS computational biology 15, no. 4 (2019): e1006650.

===============================================================================
Start likelihood: -3399.488237128869 
Writing file C:\Users\75180\Bot563\BEAST\frasera\fraserav2_gamma.log
Writing file C:\Users\75180\Bot563\BEAST\frasera\fraserav2_gamma.trees
         Sample      posterior     likelihood          prior
              0     -3399.7527     -3379.8542       -19.8985 --
           1000     -1804.0210     -1800.3002        -3.7207 --
           2000     -1795.3363     -1795.3953         0.0589 --
           3000     -1793.5579     -1792.8815        -0.6763 --
           4000     -1792.6346     -1792.9951         0.3604 --
           5000     -1794.4291     -1793.6865        -0.7425 --
           6000     -1795.5096     -1793.5980        -1.9116 --
           7000     -1790.0698     -1788.6564        -1.4133 --
           8000     -1786.3618     -1785.8196        -0.5421 --
           9000     -1781.1358     -1780.0421        -1.0936 --
          10000     -1781.3530     -1780.6192        -0.7337 --
          11000     -1782.1101     -1776.2871        -5.8229 6s/Msamples
          12000     -1779.9077     -1778.1556        -1.7521 8s/Msamples
          13000     -1779.1728     -1778.8498        -0.3229 8s/Msamples
          14000     -1777.0314     -1777.4006         0.3691 8s/Msamples
          15000     -1774.3762     -1775.3092         0.9330 8s/Msamples
          16000     -1773.7437     -1774.0498         0.3061 8s/Msamples
          17000     -1774.1870     -1775.9923         1.8053 8s/Msamples
          18000     -1768.7828     -1770.7410         1.9581 8s/Msamples
          19000     -1771.7266     -1771.2694        -0.4571 8s/Msamples
          20000     -1771.2976     -1773.8744         2.5767 8s/Msamples
          21000     -1772.0889     -1773.3498         1.2609 8s/Msamples
          22000     -1772.0009     -1771.2919        -0.7089 8s/Msamples
          23000     -1771.7750     -1772.8333         1.0582 8s/Msamples
          24000     -1768.7771     -1768.7754        -0.0016 8s/Msamples
          25000     -1767.6644     -1768.6767         1.0123 8s/Msamples
          26000     -1770.3241     -1770.1301        -0.1940 8s/Msamples
          27000     -1773.9076     -1770.4272        -3.4804 8s/Msamples
          28000     -1768.7435     -1768.3919        -0.3516 8s/Msamples
          29000     -1772.2064     -1772.2509         0.0444 1m1s/Msamples
          30000     -1770.8160     -1770.3040        -0.5119 59s/Msamples
          31000     -1770.9795     -1771.0418         0.0623 56s/Msamples
          32000     -1772.7477     -1773.2953         0.5475 54s/Msamples
          33000     -1769.8935     -1770.4300         0.5365 52s/Msamples
          34000     -1770.9126     -1768.6151        -2.2974 50s/Msamples
          35000     -1767.1803     -1767.2920         0.1117 48s/Msamples
          36000     -1767.8055     -1766.6730        -1.1324 47s/Msamples
          37000     -1765.9474     -1765.9553         0.0078 45s/Msamples
          38000     -1761.6750     -1761.3003        -0.3746 44s/Msamples
          39000     -1768.6468     -1767.6720        -0.9748 43s/Msamples
          40000     -1765.9985     -1764.9168        -1.0817 42s/Msamples
          41000     -1765.2434     -1763.1241        -2.1192 40s/Msamples
          42000     -1760.3912     -1760.4915         0.1002 39s/Msamples
          43000     -1763.5464     -1763.8381         0.2917 38s/Msamples
          44000     -1763.0981     -1762.7069        -0.3912 37s/Msamples
          45000     -1761.6607     -1761.4480        -0.2127 37s/Msamples
          46000     -1768.1215     -1762.6926        -5.4288 36s/Msamples
          47000     -1762.1625     -1763.0655         0.9029 35s/Msamples
          48000     -1763.8780     -1764.3801         0.5021 34s/Msamples
          49000     -1760.4513     -1761.1074         0.6560 34s/Msamples
          50000     -1764.9402     -1765.6803         0.7401 33s/Msamples
          51000     -1760.7332     -1761.2287         0.4955 32s/Msamples
          52000     -1762.5544     -1761.7331        -0.8213 55s/Msamples
          53000     -1762.9609     -1762.0270        -0.9338 55s/Msamples
          54000     -1764.6813     -1761.8341        -2.8471 54s/Msamples
          55000     -1764.1324     -1763.3473        -0.7850 53s/Msamples
          56000     -1762.8431     -1761.6022        -1.2409 52s/Msamples
          57000     -1764.7087     -1763.4198        -1.2889 51s/Msamples
          58000     -1762.4099     -1761.3613        -1.0486 50s/Msamples
          59000     -1762.5936     -1761.4091        -1.1844 49s/Msamples
          60000     -1763.7387     -1763.5812        -0.1574 48s/Msamples
          61000     -1766.6580     -1766.3690        -0.2889 47s/Msamples
          62000     -1764.4813     -1762.7701        -1.7111 46s/Msamples
          63000     -1763.5510     -1763.3104        -0.2405 46s/Msamples
          64000     -1762.8964     -1761.9563        -0.9400 45s/Msamples
          65000     -1765.2911     -1762.3457        -2.9454 44s/Msamples
          66000     -1768.8866     -1767.3609        -1.5257 44s/Msamples
          67000     -1764.9082     -1762.5688        -2.3393 43s/Msamples
          68000     -1765.1136     -1762.0813        -3.0322 42s/Msamples
          69000     -1763.2373     -1761.1124        -2.1249 42s/Msamples
          70000     -1770.9354     -1768.9041        -2.0312 41s/Msamples
          71000     -1762.5728     -1760.1076        -2.4651 41s/Msamples
          72000     -1773.0867     -1767.9282        -5.1584 40s/Msamples
          73000     -1764.4262     -1763.0765        -1.3497 39s/Msamples
          74000     -1763.7651     -1762.8538        -0.9112 39s/Msamples
          75000     -1762.7414     -1760.0563        -2.6851 38s/Msamples
          76000     -1763.5689     -1761.5958        -1.9731 53s/Msamples
          77000     -1762.2768     -1759.7482        -2.5286 53s/Msamples
          78000     -1763.9972     -1760.9639        -3.0332 52s/Msamples
          79000     -1764.9502     -1762.8989        -2.0513 52s/Msamples
          80000     -1763.6768     -1762.6657        -1.0111 51s/Msamples
          81000     -1763.6883     -1762.6040        -1.0842 50s/Msamples
          82000     -1763.7298     -1762.4961        -1.2337 50s/Msamples
          83000     -1767.8407     -1767.9099         0.0691 49s/Msamples
          84000     -1763.4804     -1762.5231        -0.9573 48s/Msamples
          85000     -1763.7898     -1763.9655         0.1757 48s/Msamples
          86000     -1763.0351     -1763.3667         0.3316 47s/Msamples
          87000     -1762.3673     -1761.2937        -1.0736 47s/Msamples
          88000     -1765.0148     -1764.5652        -0.4496 46s/Msamples
          89000     -1766.7047     -1764.6372        -2.0675 46s/Msamples
          90000     -1761.1126     -1762.2791         1.1665 45s/Msamples
          91000     -1764.4231     -1764.1194        -0.3037 45s/Msamples
          92000     -1771.5313     -1771.6451         0.1138 44s/Msamples
          93000     -1760.3087     -1761.2557         0.9469 44s/Msamples
          94000     -1761.2418     -1761.4139         0.1721 43s/Msamples
          95000     -1759.3775     -1762.6615         3.2839 43s/Msamples
          96000     -1765.1106     -1768.1734         3.0628 43s/Msamples
          97000     -1763.6357     -1768.3050         4.6692 42s/Msamples
          98000     -1759.1416     -1766.0847         6.9431 42s/Msamples
          99000     -1760.1562     -1764.8203         4.6641 41s/Msamples
         100000     -1757.8950     -1762.7757         4.8806 41s/Msamples

Operator                                                                                            Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
ScaleOperator(hyperScaler.hyperGamma-alpha-CalibratedYuleBirthRatePrior.t:fraserav5_aligned_cl)    0.25611         73         66    0.00133    0.52518 Try setting scaleFactor to about 0.066
ScaleOperator(hyperScaler.hyperGamma-beta-CalibratedYuleBirthRatePrior.t:fraserav5_aligned_cl)     0.25153         61         59    0.00133    0.50833 Try setting scaleFactor to about 0.063
ScaleOperator(YuleBirthRateScaler.t:fraserav5_aligned_cl)                                          0.28618       2108       1885    0.03984    0.52792 Try setting scaleFactor to about 0.082
ScaleOperator(YuleModelTreeScaler.t:fraserav5_aligned_cl)                                          0.54326        775       3167    0.03984    0.19660 
ScaleOperator(YuleModelTreeRootScaler.t:fraserav5_aligned_cl)                                      0.53280        925       2969    0.03984    0.23754 
Uniform(YuleModelUniformOperator.t:fraserav5_aligned_cl)                                                 -      10695      29223    0.39841    0.26792 
SubtreeSlide(YuleModelSubtreeSlide.t:fraserav5_aligned_cl)                                         0.21987        206      19748    0.19920    0.01032 Try decreasing size to about 0.11
Exchange(YuleModelNarrow.t:fraserav5_aligned_cl)                                                         -        565      19257    0.19920    0.02850 
Exchange(YuleModelWide.t:fraserav5_aligned_cl)                                                           -          8       4020    0.03984    0.00199 
WilsonBalding(YuleModelWilsonBalding.t:fraserav5_aligned_cl)                                             -          5       4025    0.03984    0.00124 
DeltaExchangeOperator(FrequenciesExchanger.s:fraserav5_aligned_cl)                                 0.04392         92         69    0.00133    0.57143 Try setting delta to about 0.088

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total nEnd likelihood: -1757.8950954482116
umber of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 7.02 seconds
```
output as fraserav3_gamma_777.txt

set seed 30000 ran again
output:
```
Start likelihood: -3806.117436335983 
Writing file C:\Users\75180\Bot563\BEAST\frasera\fraserav2_gamma.log
Writing file C:\Users\75180\Bot563\BEAST\frasera\fraserav2_gamma.trees
         Sample      posterior     likelihood          prior
              0     -3806.1174     -3786.9002       -19.2172 --
           1000     -1798.5424     -1795.5316        -3.0108 --
           2000     -1799.5146     -1796.5929        -2.9216 --
           3000     -1798.2706     -1794.7876        -3.4830 --
           4000     -1796.3387     -1794.3218        -2.0169 --
           5000     -1801.8901     -1801.0117        -0.8783 --
           6000     -1798.3367     -1797.5218        -0.8148 --
           7000     -1792.6191     -1790.3079        -2.3111 --
           8000     -1792.4392     -1792.3053        -0.1338 --
           9000     -1793.2458     -1791.3840        -1.8617 --
          10000     -1795.1274     -1793.5937        -1.5337 --
          11000     -1791.1673     -1789.4277        -1.7396 7s/Msamples
          12000     -1787.8898     -1787.7912        -0.0985 7s/Msamples
          13000     -1792.6544     -1792.3998        -0.2545 7s/Msamples
          14000     -1787.7967     -1785.5723        -2.2244 7s/Msamples
          15000     -1788.4792     -1790.0539         1.5746 7s/Msamples
          16000     -1789.1586     -1786.4628        -2.6957 7s/Msamples
          17000     -1788.6014     -1788.4091        -0.1922 8s/Msamples
          18000     -1785.9412     -1786.0462         0.1049 8s/Msamples
          19000     -1785.4047     -1785.6907         0.2860 8s/Msamples
          20000     -1787.4529     -1787.7754         0.3224 8s/Msamples
          21000     -1783.8311     -1784.7726         0.9414 8s/Msamples
          22000     -1788.9433     -1789.7513         0.8079 8s/Msamples
          23000     -1787.0144     -1788.3584         1.3439 8s/Msamples
          24000     -1785.8495     -1789.0478         3.1982 8s/Msamples
          25000     -1783.9846     -1785.5486         1.5640 8s/Msamples
          26000     -1787.6234     -1789.3660         1.7425 8s/Msamples
          27000     -1782.7311     -1783.7677         1.0366 8s/Msamples
          28000     -1782.5176     -1783.5095         0.9918 8s/Msamples
          29000     -1780.9143     -1782.5967         1.6823 8s/Msamples
          30000     -1783.4115     -1784.2512         0.8397 8s/Msamples
          31000     -1785.0014     -1784.8760        -0.1254 8s/Msamples
          32000     -1784.7520     -1785.7166         0.9645 8s/Msamples
          33000     -1782.7521     -1784.4594         1.7072 8s/Msamples
          34000     -1780.9455     -1783.0085         2.0630 8s/Msamples
          35000     -1778.9944     -1783.2051         4.2107 8s/Msamples
          36000     -1777.8673     -1781.5670         3.6996 8s/Msamples
          37000     -1778.0562     -1779.8301         1.7738 8s/Msamples
          38000     -1775.2991     -1777.7314         2.4323 8s/Msamples
          39000     -1772.6622     -1775.5698         2.9075 8s/Msamples
          40000     -1773.7156     -1776.5710         2.8553 8s/Msamples
          41000     -1771.1597     -1774.6883         3.5286 8s/Msamples
          42000     -1770.1582     -1773.7065         3.5483 8s/Msamples
          43000     -1768.6222     -1771.3855         2.7633 8s/Msamples
          44000     -1765.9026     -1768.7609         2.8582 8s/Msamples
          45000     -1764.4053     -1768.0494         3.6441 8s/Msamples
          46000     -1764.9699     -1767.4841         2.5142 8s/Msamples
          47000     -1765.1577     -1767.3561         2.1983 8s/Msamples
          48000     -1764.5475     -1766.7326         2.1850 8s/Msamples
          49000     -1764.7540     -1766.6184         1.8643 8s/Msamples
          50000     -1762.7575     -1764.7502         1.9926 33s/Msamples
          51000     -1764.1096     -1763.1276        -0.9820 33s/Msamples
          52000     -1762.5948     -1763.5714         0.9765 32s/Msamples
          53000     -1764.8561     -1766.6941         1.8380 31s/Msamples
          54000     -1759.9984     -1762.2991         2.3007 31s/Msamples
          55000     -1756.7260     -1760.3050         3.5790 30s/Msamples
          56000     -1758.9573     -1761.9940         3.0366 30s/Msamples
          57000     -1758.4167     -1761.1455         2.7288 29s/Msamples
          58000     -1762.8315     -1765.2199         2.3884 29s/Msamples
          59000     -1757.7424     -1759.8871         2.1446 28s/Msamples
          60000     -1758.7385     -1761.4926         2.7540 28s/Msamples
          61000     -1758.5055     -1760.7127         2.2072 28s/Msamples
          62000     -1757.5335     -1760.9737         3.4401 27s/Msamples
          63000     -1762.2253     -1764.1563         1.9309 27s/Msamples
          64000     -1758.3682     -1762.1348         3.7665 26s/Msamples
          65000     -1760.2708     -1762.6279         2.3570 26s/Msamples
          66000     -1758.6465     -1763.4671         4.8205 26s/Msamples
          67000     -1756.7161     -1761.1777         4.4615 25s/Msamples
          68000     -1760.0913     -1764.7901         4.6987 25s/Msamples
          69000     -1758.7492     -1764.8912         6.1420 25s/Msamples
          70000     -1756.0974     -1762.3399         6.2425 24s/Msamples
          71000     -1760.0137     -1766.4881         6.4743 24s/Msamples
          72000     -1759.0577     -1764.9561         5.8983 24s/Msamples
          73000     -1758.6192     -1763.2820         4.6628 23s/Msamples
          74000     -1759.4550     -1763.1598         3.7047 39s/Msamples
          75000     -1757.3946     -1763.3702         5.9755 39s/Msamples
          76000     -1756.4801     -1762.9091         6.4290 38s/Msamples
          77000     -1761.7285     -1768.9706         7.2420 38s/Msamples
          78000     -1755.9377     -1764.2272         8.2894 37s/Msamples
          79000     -1755.6561     -1763.5410         7.8849 37s/Msamples
          80000     -1754.4672     -1763.3587         8.8914 36s/Msamples
          81000     -1757.5003     -1766.9422         9.4419 36s/Msamples
          82000     -1755.6434     -1765.3738         9.7303 36s/Msamples
          83000     -1749.5621     -1762.0316        12.4695 35s/Msamples
          84000     -1750.3920     -1762.1111        11.7191 35s/Msamples
          85000     -1752.1846     -1763.6162        11.4316 34s/Msamples
          86000     -1749.4890     -1760.7777        11.2887 34s/Msamples
          87000     -1747.0203     -1760.1354        13.1151 34s/Msamples
          88000     -1749.2946     -1762.7563        13.4616 33s/Msamples
          89000     -1749.8045     -1762.4743        12.6697 33s/Msamples
          90000     -1747.9315     -1761.4559        13.5243 33s/Msamples
          91000     -1749.9831     -1761.7150        11.7319 32s/Msamples
          92000     -1754.2585     -1768.1865        13.9279 32s/Msamples
          93000     -1748.9312     -1760.8118        11.8806 32s/Msamples
          94000     -1751.0238     -1762.3811        11.3572 31s/Msamples
          95000     -1757.4947     -1766.6297         9.1349 31s/Msamples
          96000     -1754.7938     -1765.1867        10.3929 31s/Msamples
          97000     -1751.5237     -1762.9199        11.3962 31s/Msamples
          98000     -1752.6038     -1764.4198        11.8159 30s/Msamples
          99000     -1748.7449     -1761.6970        12.9521 30s/Msamples
         100000     -1750.0687     -1762.4302        12.3614 41s/Msamples

Operator                                                                                            Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
ScaleOperator(hyperScaler.hyperGamma-alpha-CalibratedYuleBirthRatePrior.t:fraserav5_aligned_cl)    0.25047         65         68    0.00133    0.48872 Try setting scaleFactor to about 0.063
ScaleOperator(hyperScaler.hyperGamma-beta-CalibratedYuleBirthRatePrior.t:fraserav5_aligned_cl)     0.22765         64         68    0.00133    0.48485 Try setting scaleFactor to about 0.052
ScaleOperator(YuleBirthRateScaler.t:fraserav5_aligned_cl)                                          0.25428       1927       1988    0.03984    0.49221 Try setting scaleFactor to about 0.065
ScaleOperator(YuleModelTreeScaler.t:fraserav5_aligned_cl)                                          0.51189        806       3167    0.03984    0.20287 
ScaleOperator(YuleModelTreeRootScaler.t:fraserav5_aligned_cl)                                      0.50069        899       3121    0.03984    0.22363 
Uniform(YuleModelUniformOperator.t:fraserav5_aligned_cl)                                                 -      10695      29182    0.39841    0.26820 
SubtreeSlide(YuleModelSubtreeSlide.t:fraserav5_aligned_cl)                                         0.20261        216      19923    0.19920    0.01073 Try decreasing size to about 0.101
Exchange(YuleModelNarrow.t:fraserav5_aligned_cl)                                                         -        402      19385    0.19920    0.02032 
Exchange(YuleModelWide.t:fraserav5_aligned_cl)                                                           -         14       3971    0.03984    0.00351 
WilsonBalding(YuleModelWilsonBalding.t:fraserav5_aligned_cl)                                             -          4       3907    0.03984    0.00102 
DeltaExchangeOperator(FrequenciesExchanger.s:fraserav5_aligned_cl)                                 0.04802         59         70    0.00133    0.45736 Try setting delta to about 0.094

     Tuning: The value of theEnd likelihood: -1750.0687905341279
 operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 5.999 seconds
```
c. tracer:
seed 777 shows the higher ESS
All others are shitty trees

d. Fig tree, reroot the tree with Swertia. 






