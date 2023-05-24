## R batch jobs

Sometimes an R script will take to long to either run via an interactive session or RStudio. In these cases we can submit the R script as a batch job.

- Login to the HPC cluster either by Command Line or the OnDemand Website. For information on how to log into the cluster check out:
    
!!! info "[Navigate To The Cluster](../hpc-user-guide/navigate-to-cluster.md){:target="_blank" rel="noopener"}"

- Upload your R script to the HPC cluster

- Go to the directory/folder which contains your R script

- Open your favorite text editor and write a slurm submission script similar to the following one `batchjob.sh` (name your own)

!!! info "batchjob.sh"

    ```
    #!/bin/bash
    #SBATCH -J myRjob  #job name
    #SBATCH --time=00-00:20:00 #requested time
    #SBATCH -p batch  #running on "batch" partition/queue
    #SBATCH -n 2  #2 cores total
    #SBATCH --mem=2g #requesting 2GB of RAM total
    #SBATCH --output=myRjob.%j.out #saving standard output to file
    #SBATCH --error=myRjob.%j.err  #saving standard error to file
    #SBATCH --mail-type=ALL  #email optitions
    #SBATCH --mail-user=Your_Tufts_Email @tufts.edu
    module load R/4.0.0
    Rscript --no-save your_rscript_name.R
    ```
    
- Submit it with: 
  
```
sbatch batchjob.sh
```
   
- If you are submitting multiple batch jobs to run the same script on different datasets, please make sure they are saving results to different files inside of your R script.
