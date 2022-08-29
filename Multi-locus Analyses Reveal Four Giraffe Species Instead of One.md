### Multi-locus Analyses Reveal Four Giraffe Species Instead of One
https://www.cell.com/current-biology/fulltext/S0960-9822(16)30787-4?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS0960982216307874%3Fshowall%3Dtrue

This is a research that was published in 2016 where the main objectives of the project was to accurately depict the giraffe species and to group each sub-species to the respective class.
Previously giraffe species were classified into one species class with eleven sub-species this research however depicts that the giraffes have been inncorectly classified. The results show that the giraffe poppulation in Africa are four different species each with different sub-speciecs.
To reproduce this paper the following methods were used:-


1. **Retrieval of Sequences**

>is an information indexing and retrieval system designed for libraries with a flat file format,such as the EMBL nucleotide sequence databank, the SwissProt protein sequence databank or the Prosite library of protein subsequence consensus patterns.
Because the data from the paper amounted to about 1423 sequence we opted to use random sequnces from the six organisms that were used in the phylogenetic 
analysis,20 sequences from each of the 9 were selected. This was achieved as follows.

 To print accesion numbers on a file to upload to batch- entrez
We created a python script named seq1.py in giraffe analysis folder 
This code generated the acession numbers, the challenge was it had a white spcae in it for every accesion number outputed 
```
seq = 596685

Start="LT"

for i in range (596685,598170):

    print (Start,i)
```

To remove the whitespace in the accesion numbers 
The following code was used on bash
```
$ seq1.py | sed -r 's/\s+//g' > sequences1 
```
Sequences1 was then uploaded to batch entrez for retrieval of sequences, the sequnces were the downloaded from NCBI.
20 sequences were downloaded for each species/sub-species in the dataset
To get the downloaded sequences into one file the following code was run
```
$ cat *.fasta >> giraffe.fasta
```
To confirm that we had 180 sequences the following code was used
```
grep -c "^>" giraffe.fasta
```

2. **Tree analyses**



## **Challenges**  

### Tree analyses  
* **BEAST**  
Error:
```  
OpenCL error: Unknown error from file </home/icipe/Downloads/beagle-lib/libhmsbeagle/GPU/GPUInterfaceOpenCL.cpp>, line 105.
```  
The error arised from installment errors of beagle-lib.

* **Beagle-lib**  

The error we faced with beagle-lib was failure of the tests:
```  
The following tests FAILED:
	  1 - hmctest (Failed)
Errors while running CTest
make: *** [Makefile:97: test] Error 8
``` 
The problem is in the installation of beagle-lib. One of the solutions was to remove openCL and re-install it, unfortunately that failed to. Another solution was to remove beagle-lib and install it once more. For this, the path to openCL conflicted with the previous path to openCL despite any efforts to change the path.  

* **MrBayes**  
Due to the failure of BEAST, we substituted it with MrBayes, which perfoms the same function as BEAST, unfortunately it also failed as it too utilised beagle-lib  


