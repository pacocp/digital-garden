# DNA Methylation

### Software packages

[gevaertlab/MethylMix](https://github.com/gevaertlab/MethylMix)

### GDC DNA Mehtylation pipeline

[https://docs.gdc.cancer.gov/Data/Bioinformatics_Pipelines/Methylation_LO_Pipeline/](https://docs.gdc.cancer.gov/Data/Bioinformatics_Pipelines/Methylation_LO_Pipeline/)

### Notes on DNA-Methylation

- When a part of the genome is methylated, that gene that is close to it usually is not expressed.
- So it gives  way to control gene expression.
- CpG is a C followed by a G, 5' → 3'
- CpGs sometimes have a methyl group attached to them. When one strand is methylated, so is the other.
- When the DNA replicates, the methylation characteristic is preserved.
- Different characteristics may be in different organs:
- CpG islands → where the methylation occurs.
- For testing if a CpG is methylated, we treat the genome with busulfite. If it is methylated, it will stay as CpG, otherwise the C will change for a T.
- Since we are measuring these across the genome, we will not obtain a 1 or 0 values, but the mean of these (between 0 and 1).
