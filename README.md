# ACCESS_SV

SV calling scripts for ACCESS

## Installation

### Git setup

Recursively git clone for [iAnnotateSV](https://github.com/rhshah/iAnnotateSV) submodule within this repository.


```bash
git clone --recursive https://github.com/mskcc/ACCESS_SV.git
```

You might need [git-lfs](https://git-lfs.github.com/)

```bash
wget https://github.com/git-lfs/git-lfs/releases/download/v2.7.1/git-lfs-linux-amd64-v2.7.1.tar.gz
tar -xvf git-lfs-darwin-amd64-v2.7.1.tar.gz
cd git-lfs-2.7.1
./git-lfs install
```
### Manta setup

Refer to [Manta Github](https://github.com/Illumina/manta/releases) for the latest releases

```bash
wget https://github.com/Illumina/manta/releases/download/v1.5.0/manta-1.5.0.centos6_x86_64.tar.bz2
tar -xvf manta-1.5.0.centos6_x86_64.tar.bz2
cd manta-1.5.0.centos6_x86_64 
```


## Usage

### Step 1: Manta

```bash
Rscript manta_sample.R
usage: manta_sample.R [-h] [-t TUMOR] [-n NORMAL] [-o OUTPUT] [-f FASTA]
                      [-m MANTA]

optional arguments:
  -h, --help
                        show this help message and exit
  -t TUMOR, --tumor TUMOR
                        Tumor bam for SV calling
  -n NORMAL, --normal NORMAL
                        Normal bam for SV calling
  -o OUTPUT, --output OUTPUT
                        Output directory for manta
  -f FASTA, --fasta FASTA
                        Fasta file for alignment
  -m MANTA, --manta MANTA
                        Directory of manta installation
```

### Step 2: Annotation Scripts and iAnnotateSV

```bash
bash iAnnotateSV.sh $1 $2 $3 $4 $5
# somatic.vcf.gz from manta output
vcf_gz=$1
# sample name
prefix=$2
# output directory
outdir=$3
# manta directory
mantadir=$4
# fasta reference
fasta=$5
```
