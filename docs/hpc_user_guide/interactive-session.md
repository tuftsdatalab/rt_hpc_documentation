## Interactive Session

- An interactive session is a way to temporarily grab resources on the Tufts HPC.
    
    - Particularly good for debugging and working with software GUI. 

- The following is the basic layout of the command to get an interactive session:

``` 
srun [options] --pty [command]
```

!!! example "What does this mean?"

    - Command 

        - command to run an application, given the module is already loaded.
        - `bash` for a bash shell

    - Options

        - Pseudo terminal `--pty`
        - Partition `-p` 
            - Default batch if not specified
        - You can start interactive sessions on any partition you have access to
        - Time `-t` or `--time=`
            - Default 15 minutes if not specified on non-"interactive" partition
        - Number of CPU cores `-n` 
            - Default 1 if not specified
        - Memory `--mem=`
            - Default 2GB if not specified
        - GPU `--gres=`
            - Default none
        - X Window `--x11=first`
            - Default none	

### Example of Getting an Interactive Session

```
srun -p batch --time=1-2:10:00 -n 2 --mem=8g --pty bash
```

!!! example "What does this mean?"
    Starting an interactive session of bash shell on preempt partition with 2 CPU cores and 2GB of RAM, with X11 forwarding for 1 day, 2 hours, and 30 minutes (use `exit` to end session and release resources).
 
You will have notice that your prompt changed from:

!!! info ""

    ```
    [your_utln@login-prod-01 ~]$
    ```

To:

!!! info ""

    ```
    [your_utln@c1cmp044 ~]$
    ```
    
- This means you have been placed on a compute node!

