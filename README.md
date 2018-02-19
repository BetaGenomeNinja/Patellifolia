# README.md Patellifolia Sequencing
01_Read_Processing_Trimmomatic
-
The raw reads were downloaded from admera. Reads were cleaned using trimmomatic, passing the appropriate adapter sequence for               trimming.
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
```
module load bowtie2/2.2.3
bowtie2 -q --phred33-quals -k 2 -x genome.fa -1 in_R1.fastq -2 in_R2.fastq -S output.sam
```
03_Sam_to_Bam
-

```
module load SAMTools/0.1.18
samtools view -b -S -o out.bam input.sam
```

04_BamSort
-
```
module load SAMTools/0.1.18
samtools sort /mnt/ls15/scratch/users/galewski/CROP/04_SNP_CROP_TYPE_1/03_SAM_to_BAM.out/0_C869_7_ATCACG_pe_bowtie.out.bam /mnt/ls15/scratch/users/galewski/CROP/04_SNP_CROP_TYPE_1/04_bam_sort.out/0_C869_7_ATCACG_pe.bam.sorted
```

05_BamMerge
-
```
module load SAMTools/0.1.18
samtools merge /mnt/ls15/scratch/users/galewski/CROP/04_SNP_CROP_TYPE_1/05_bam_merge.out/0_C869_7_ATCACG_pe.bam.merged /mnt/ls15/scratch/users/galewski/CROP/04_SNP_CROP_TYPE_1/04_bam_sort.out/0_C869_7_ATCACG_pe.bam.sorted.bam /mnt/ls15/scratch/users/galewski/CROP/04_SNP_CROP_TYPE_1/04_bam_sort.out/0_C869_7_ATCACG__se.bam.sorted.bam
```










