# Introduction to Parallel

[GNU Parallel](https://www.gnu.org/software/parallel/){:target="_blank" rel="noopener"} is a shell tool that allows for independent jobs to be run in parallel over multiple compute resources. 

## Bash Loop Using Parallel

[GNU Parallel](https://www.gnu.org/software/parallel/){:target="_blank" rel="noopener"} can greatly speed up a task given that it can leverage multiple compute resources at once. Let's examine the case of the following bash loop (example taken from [Yale Center For Research Computing - Parallel](https://docs.ycrc.yale.edu/clusters-at-yale/guides/parallel/)):

```bash
for letter in {a..f};
do
    echo $letter
done
```

!!! info "output"

    ```bash
    a
    b
    c
    d
    e
    f
    ```

To parallelize this task we can use the `parallel` module and ask for multiple CPUs per task:

```bash
salloc -c 4
module load parallel
parallel -j 4 "echo {}" ::: {a..f}
```

!!! info "output"

    ```bash
    a
    b
    c
    d
    e
    f
    ```
## Parallel In A Bash Script

Additionally, we can leverage the `parallel` module in a batch script:

```bash
#!/bin/bash
#SBATCH --job-name=runParallel
#SBATCH --time=01-00:00:00
#SBATCH --nodes=1
#SBATCH -c 8
#SBATCH --mem=4G
#SBATCH --output=%x.%j.out
#SBATCH --error=%x.%j.err

# load modules
module load parallel
module load fastqc

# make an output directory
mkdir fastqc_output

# find all fastq files and run fastqc them
ls *.fastq.gz | parallel -j ${SLURM_CPUS_PER_TASK} "fastqc {} -o fastqc_output"
```

Here we load the `parallel` and `fastqc` modules. We then create an output directory (`fastqc_output`). In our command we list all our fastq files (`ls *.fastq.gz`), then use the parallel command to run fastqc on each file (`fastqc {} -o fastqc_output`). We reference each fastq file with the curly brackets `{}`. You'll also notice that we specify how many compute resources are available with `-j ${SLURM_CPUS_PER_TASK}`.

## References

1. https://www.gnu.org/software/parallel/
2. https://docs.ycrc.yale.edu/clusters-at-yale/guides/parallel/
