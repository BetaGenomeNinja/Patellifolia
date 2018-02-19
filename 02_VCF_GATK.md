# VCF from GATK
Starts with bam files (BWA,bowtie2,etc...)
```
module load picardtools
java -jar /opt/software/picardTools/1.113/AddOrReplaceReadGroups.jar I=${File}.bam O=${File}.out.bam RGLB=String RGPL=String RGPU=String RGSM=String
```

```
module load picardtools
java -jar /opt/software/picardTools/1.113/SortSam.jar I=${File}.out.bam O=${File}.out.sorted.bam SO=coordinate
```

```
module load picardtools
java -jar /opt/software/picardTools/1.113/BuildBamIndex.jar I=$i O=$i'.bai';done
```

```
module load GATK/2.5.2
GATK -T HaplotypeCaller -R /mnt/scratch/galewski/CROP/50genomes/genome/EL10_chr_scaffold.fa -I ${File}.bam -o ${File}.vcf
```

```
module load GATK/2.5.2
GATK -T RealignerTargetCreator -R ../genome/EL10_chr_scaffold.fa -I ${File} -o ${File}.intervals
```

```
module load GATK/2.5.2
GATK -T IndelRealigner -R ../genome/EL10_chr_scaffold.fa -I ${File}.bam  -known ${File}.vcf -targetIntervals ${File}.bam.intervals -o ${File}.bam.realigned.bam
```

```
module load GATK/2.5.2
GATK -T HaplotypeCaller -R /mnt/scratch/galewski/CROP/50genomes/genome/EL10_chr_scaffold.fa -I ${File}.bam -o ${File}.vcf
```















