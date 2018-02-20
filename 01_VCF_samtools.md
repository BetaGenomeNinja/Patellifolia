# README.md Patellifolia Sequencing
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
samtools sort out.bam out.bam.sorted
```

05_BamMerge
-
```
module load SAMTools/0.1.18
samtools merge out.bam.merged 1.bam.sorted.bam 2.sorted.bam
```

06_bcf
-
```
module load SAMTools/0.1.18
samtools mpileup -uf genome/EL10byChromosome.fasta out.bam.merged | bcftools view -bvcg - > out.bcf
```

07_vcf
-
```
module load SAMTools/0.1.18
bcftools view out.bcf | vcfutils.pl varFilter -D100 > out.vcf
```










