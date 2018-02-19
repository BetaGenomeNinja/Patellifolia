# README.md 
Patellifolia Sequencing
-
01_Read_Processing_Trimmomatic

The raw reads were downloaded from admera. Reads were cleaned using trimmomatic, passing the appropriate adapter sequence for trimming.
```
java -jar $TRIM/trimmomatic PE ${File}_R1_001.fastq.gz ${File}_R2_001.fastq.gz ${File}_R1_pe.fastq ${File}_R1_se.fastq ${File}_R2_pe.fastq ${File}_R2_se.fastq ILLUMINACLIP:/mnt/scratch/galewski/CROP/CT_EL_SR_PAT_genomes/admera_adapters.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36
```
$cat admera_adapters.fa
```
>AdapterRead1
AGATCGGAAGAGCACACGTCTGAACTCCAGTCA
>AdapterRead2
AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGT
```
02_Alignment_to_Referance
-












