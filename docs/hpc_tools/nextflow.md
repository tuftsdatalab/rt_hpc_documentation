## Nextflow

Nextflow is a type of workflow manager, designed to be portable and reproducible. Nextflow can be used on local, HPC schedulers, AWS Batch, Google Cloud Life Sciences, and Kubernetes. Nextflow can access tool dependencies through Conda, Spack, Docker, Podman, Singularity, Modules and more.

## How Do I Access Nextflow on the Cluster?

Nextflow can be accessed on the Tufts HPC Cluster with the following modules:

```bash
module load gcc nextflow/21.10.1 java/15.0.2 anaconda/2021.11
```

You might also have noticed that we include `anaconda/2021.11` as well. This is because many nextflow pipelines you might import will use Anaconda for pipeline tool dependencies. 

## Running nf-core Pipelines

Speaking of importing Nextflow pipelines, it is worth mentioning nf-core pipelines. These are community developed pipelines that are available for your use! There are a number of pipelines you can use:

[Nextflow nf-core Pipelines](https://nf-co.re/pipelines){:target="_blank" rel="noopener"}

!!! danger

    When Nextflow is running tasks it will create many temp files within: the ` ./work` directory. Be very careful when running these pipelines and always be sure to clear out files in this folder to avoid running out of file storage. 


We will demonstrate how to run the RNA-seq pipeline:

```bash
nextflow run nf-core/rnaseq \
    --input samplesheet.csv \
    --outdir <OUTDIR> \
    --genome GRCh37 \
    -profile docker
```

Where your `samplesheet.csv` will include:

!!! info "samplesheet.csv"

    ```
    sample,fastq_1,fastq_2,strandedness
    CONTROL_REP1,AEG588A1_S1_L002_R1_001.fastq.gz,AEG588A1_S1_L002_R2_001.fastq.gz,auto
    CONTROL_REP1,AEG588A1_S1_L003_R1_001.fastq.gz,AEG588A1_S1_L003_R2_001.fastq.gz,auto
    CONTROL_REP1,AEG588A1_S1_L004_R1_001.fastq.gz,AEG588A1_S1_L004_R2_001.fastq.gz,auto
    ```
However, this is a multi-faceted pipeline, with many additional parameters you can tweak for your needs. To better understand those parameters, always check the `Usage docs` and `Parameters` sections of each pipeline's documentation.

## Building your own Nextflow Pipeline



## References

1. [Nextflow Github](https://github.com/nextflow-io/nextflow)
2. [RNA-Seq Nextflow](https://nf-co.re/rnaseq/3.11.1)
