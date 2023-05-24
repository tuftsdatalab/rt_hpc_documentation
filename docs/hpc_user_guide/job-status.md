## Checking Job Status

- Checking your **active** jobs:

```bash
squeue -u $USER
```

!!! info "output"

    ```
       JOBID PARTITION     NAME     USER  ST       TIME  NODES NODELIST(REASON) 
    24063163     batch      job your_utln  R       0:17      1 c1cmp044 
    ```
            
```
squeue -u your_utln
```

!!! info "output"

    ```
       JOBID PARTITION     NAME     USER  ST       TIME  NODES NODELIST(REASON) 
    24063163     batch      job your_utln  R       0:17      1 c1cmp044 
    ```


## To Cancel A Job

- To cancel **a specific job**:

```
scancel JOBID
```

- To cancel **all of your job**s:

```
scancel -u $USER
```

```
scancel -u your_utln
```

## To Check The Details Of Your Active Jobs

- To check details of your active jobs (running "R" or pending "PD"):

```
scontrol show jobid -dd JOBID
```

```bash
scontrol show jobid -dd 24063163
```

!!! info "output"

    ```
    JobId=24063163 JobName=job
       UserId=your_utln(31003) GroupId=your_utln(5343) MCS_label=N/A
       Priority=12833 Nice=0 Account=normal QOS=normal
       JobState=RUNNING Reason=None Dependency=(null)
       Requeue=0 Restarts=0 BatchFlag=1 Reboot=0 ExitCode=0:0
       DerivedExitCode=0:0
       RunTime=00:01:31 TimeLimit=1-00:00:00 TimeMin=N/A
       SubmitTime=2022-07-20T12:33:14 EligibleTime=2022-07-20T12:33:14
       AccrueTime=2022-07-20T12:33:14
       StartTime=2022-07-20T12:33:15 EndTime=2022-07-21T12:33:15 Deadline=N/A
       PreemptEligibleTime=2022-07-20T12:33:15 PreemptTime=None
       SuspendTime=None SecsPreSuspend=0 LastSchedEval=2022-07-20T12:33:15
       Partition=batch AllocNode:Sid=c1cmp044:27677
       ReqNodeList=(null) ExcNodeList=(null)
       NodeList=c1cmp044
       BatchHost=c1cmp044
       NumNodes=1 NumCPUs=2 NumTasks=2 CPUs/Task=1 ReqB:S:C:T=0:0:*:*
       TRES=cpu=2,mem=8G,node=1,billing=2
       Socks/Node=* NtasksPerN:B:S:C=0:0:*:* CoreSpec=*
       JOB_GRES=(null)
         Nodes=c1cmp044 CPU_IDs=2-3 Mem=8192 GRES=
       MinCPUsNode=1 MinMemoryNode=8G MinTmpDiskNode=0
       Features=(null) DelayBoot=00:00:00
       Reservation=bioworkshop
       OverSubscribe=OK Contiguous=0 Licenses=(null) Network=(null)
       Command=/cluster/home/ymalon01/workshop/LS/sbatch.sh
       WorkDir=/cluster/home/ymalon01/workshop/LS
       StdErr=/cluster/home/ymalon01/workshop/LS/24063163.err
       StdIn=/dev/null
       StdOut=/cluster/home/ymalon01/workshop/LS/24063163.out
       Power=
       MailUser=ymalon01 MailType=NONE
    ```

## To Check The Details Of Your Finished Jobs

- Checking your **finished** jobs:

*You can no longer see these jobs in `squeue` command output.*

!!! tip
    Querying finished jobs helps users make better decisions on requesting resources for future jobs.

Display job CPU and memory usage:

```
seff JOBID
```

!!! info "output"

    ```bash
    seff JOBID
    Job ID: JOBID
    Cluster: pax
    User/Group: your_utln/your_utln
    State: COMPLETED (exit code 0)
    Nodes: 1
    Cores per node: 2
    CPU Utilized: 00:03:00
    CPU Efficiency: 50.00% of 00:06:00 core-walltime
    Job Wall-clock time: 00:03:00
    Memory Utilized: 54.16 MB
    Memory Efficiency: 0.66% of 8.00 GB
    ```

## Check Accounting Data for a Job

- Display detailed **job accounting data**:

```
sacct --format=partition,state,time,start,end,elapsed,MaxRss,ReqMem,MaxVMSize,nnodes,ncpus,nodelist -j JOBID
```

!!! info "output"

    ```bash
     Partition      State  Timelimit               Start                 End    Elapsed     MaxRSS     ReqMem  MaxVMSize   NNodes      NCPUS        NodeList 
    ---------- ---------- ---------- ------------------- ------------------- ---------- ---------- ---------- ---------- -------- ---------- --------------- 
         batch  COMPLETED 1-00:00:00 2022-07-20T12:33:15 2022-07-20T12:36:15   00:03:00                   8Gn                   1          2        c1cmp044 
                COMPLETED            2022-07-20T12:33:15 2022-07-20T12:36:15   00:03:00     55464K        8Gn    198364K        1          2        c1cmp044 
               OUT_OF_ME+            2022-07-20T12:33:15 2022-07-20T12:36:15   00:03:00          0        8Gn    108052K        1          2        c1cmp044 
    ```

## Going Further

- For more SLURM options check out:

!!! info "[SLURM Workload Manager](https://slurm.schedmd.com/man_index.html){:target="_blank" rel="noopener"}"




