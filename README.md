# Problem_Set_10

This week we continued to learn about Hidden Markov Models. A common use for HMMs is analysis of biological sequence data. 

For this problem set we will build and analyze an HMM using the aphid package. https://cran.r-project.org/web/packages/aphid/aphid.pdf

The scenario we will be replicating is very common in my work. We are often interested in identifying homologous genes in new genomes using a reference set of gene annotations. 

First we build an HMM from the reference sequences. Then we use that HMM to find orthologues in the new genome. 

### Step 1 - Load Packages

Install and load the aphid package ("aphid")
Install and load the sequence package ("ape")

### Step 2 - Read in Sequences

Our reference sequences are in the file BBH1.fasta . This is a part of a real analysis conducted on budding yeast species. 

The BBH1 gene is a part of the carnitine biosynthesis pathway. In our preliminary analysis of budding yeast species we had identified enzymes corresponding to the first 2 enzymes in this biosynthesis pathway. This preliminary anlaysis was based on HMMs built from other eukaryotic species. A literature search demonstrated that BBH1 is known to exist in _Candida_ yeast species. This suggested we needed to construct a new HMM! 

Read in the sequence file using the function ```read.FASTA()```. Make sure to set the type to AA


### Step 3 - Align the sequences

Use the ```align()``` function from aphid to align the input sequences. Save the output into a new variable

Answer the following questions about the alignment
1) How many modules were in the PHMM used to create the alignment
2) How many of the hidden states were "Insertion" states? 


### Step 4 - Create a PHMM 

We want to utilize the fact that the aphid package _knows_ about the relationships between amino acids 

Use the ```derivePHMM.AAbin()``` function from aphid to build a PHMM from the AAbin sequence alignment. Save the output into a new variable

Answer the following questions about the resulting HMM 
1) Look at the emission matrix. What amino acid has the higest probability of emission from the 2nd module? 
2) Look at the transition matrix. This format is slightly different from what we have seen before. Instead of listing _every_ state they list the possible transitions between Deletion (D), Insertion (I), or Module (M) states. Identify the row that contains hidden state transition from Module to Insertion. Which module has the greatest transition probability from Module to Insertion? 
 


### Step 5 - Probability of new sequences

You have three new sequences. You want to determine if any of these three sequences are likely to encode the BBH1 gene. 

Read in the new sequences found in the file **new_SeqsA.fasta**

For each of the new protein sequences use the ```forward()``` method to examine the probability of each of the new sequences

There is an option to report either the full probability or the Log odds score (odds = T or odds = F). You can use either to answer the questions below

1) Which sequence is likely **not** an ortholog of the BBH1 gene?
