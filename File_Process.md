#VCF
-
```
java -jar /opt/software/picardTools/1.113/AddOrReplaceReadGroups.jar I=${File}.bam O=${File}.out.bam RGLB=String RGPL=String RGPU=String RGSM=String
```

```
java -jar /opt/software/picardTools/1.113/SortSam.jar I=${File}.out.bam O=${File}.out.sorted.bam SO=coordinate
```

```
java -jar /opt/software/picardTools/1.113/BuildBamIndex.jar I=$i O=$i'.bai';done
```

```
GATK -T HaplotypeCaller -R /mnt/scratch/galewski/CROP/50genomes/genome/EL10_chr_scaffold.fa -I ${File}.bam -o ${File}.vcf
```

```
GATK -T RealignerTargetCreator -R ../genome/EL10_chr_scaffold.fa -I ${File} -o ${File}.intervals
```

```

```















