## Python Interactive Session

- Login to the HPC cluster either by Command Line or the OnDemand Website. For information on how to log into the cluster check out:
    
!!! info "[Navigate To The Cluster](../hpc-user-guide/navigate-to-cluster.md){:target="_blank" rel="noopener"}"

- From the login node, load the python module 

```
module load python/3.8.8
```
     
- To check out different python modules enter the command:

```
module av python
```

- Allocate computing resources. Start an interactive session with your desired number of cores and memory, here we are using 2 cores with 4GB of memory: 

```
srun -p interactive -n 2 --mem=4g --pty bash
```

- The Interactive partition has a default 4-hour time limit 

- For more information on how to allocate resources on Tufts HPC cluster, check out:

!!! info "[Compute Resources](../hpc-user-guide/compute-resources.md){:target="_blank" rel="noopener" }"


