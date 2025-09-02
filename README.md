# Strandness  
This tutorial will introduce how to run Strandness to analyze strandness of RNAs-seq data.

### Strandness can be used to analyze strandness of RNAs-seq data.  
```
usage: Strandness [-h] [-F {bam,fastq}] -I INPUTPATH -f FILENAME -G GTF [-X HISAT2_INDEX] -O OUTPATH -o OUTFILE
                  [-B BAM_PATH] [-1 FASTQ1] [-2 FASTQ2] [-T THREADS] [--allow-multimappers] [--hisat2-extra ...]
                  [-V]

options:
  -h, --help            show this help message and exit
  -F {bam,fastq}, --format {bam,fastq}
                        Input type: 'bam' uses an existing BAM; 'fastq' aligns the full FASTQ(s) with HISAT2.
  -I INPUTPATH, --inputpath INPUTPATH
                        Path to input files (BAM or FASTQ directory).
  -f FILENAME, --filename FILENAME
                        Base name of input (e.g. sample → sample.bam or sample_R1.fastq.gz by default).
  -G GTF, --gtf GTF     GTF (can be .gtf or .gtf.gz). Exon records are used.
  -X HISAT2_INDEX, --hisat2-index HISAT2_INDEX
                        HISAT2 index prefix (required when -F fastq).
  -O OUTPATH, --outpath OUTPATH
                        Output directory.
  -o OUTFILE, --outfile OUTFILE
                        Output file prefix.
  -B BAM_PATH, --bam BAM_PATH
                        Explicit BAM path (overrides inputpath/filename.bam).
  -1 FASTQ1, --fastq1 FASTQ1
                        Explicit FASTQ read1 path (overrides inputpath/filename_R1.fastq.gz).
  -2 FASTQ2, --fastq2 FASTQ2
                        Explicit FASTQ read2 path. Omit for single-end.
  -T THREADS, --threads THREADS
                        Threads for HISAT2/samtools when -F fastq.
  --allow-multimappers  Include NH>1 alignments (default: exclude).
  --hisat2-extra ...    Any extra args to pass to HISAT2 (e.g., --dta). Everything after this flag is sent to
                        hisat2.
  -V, --version         Print version and exit
```
#### Using an existing BAM (fastest):
#### usage: 
```
    Strandness \
    -F bam \
    -I /data/aln \
    -f sample \
    -G /refs/genes.gtf.gz \
    -O /data/out \
    -o sample_strand
``` 

#### From FASTQs with HISAT2 (paired-end):
#### usage: 
```
  Strandness \
  -F fastq \
  -I /data/fastq \
  -f sample \
  -G /refs/genes.gtf.gz \
  -X /refs/hisat2/grch38_index  \
  -O /data/out \
  -o sample_strand \
  -1 /data/fastq/sample_R1.fastq.gz \
  -2 /data/fastq/sample_R2.fastq.gz \
  -T 16
``` 

#### From FASTQs with HISAT2 (pSingle-end):
#### usage: 
```
   Strandness \
  -F fastq \
  -I /data/fastq \
  -f sample_SE \
  -G /refs/genes.gtf.gz \
  -X /refs/hisat2/grch38_index \
  -O /data/out \
  -o sampleSE_strand \
  -1 /data/fastq/sample_SE.fastq.gz
``` 


### Installation 
#### requirement for installation
python>=3.8  
numpy  
pandas  
argparse  

#### pip install Strandness==1.10.0
https://pypi.org/project/Strandness/1.0.0/


