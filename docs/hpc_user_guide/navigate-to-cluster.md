## Prerequisites

!!! example ""
    - [Request an Research Computing Cluster account](http://research.uit.tufts.edu/){:target="_blank" rel="noopener"}
    - [Connect to the VPN](https://access.tufts.edu/vpn){:target="_blank" rel="noopener"} if off campus


## Navigate to the Cluster

- You can access the Tufts HPC in two ways, either the OnDemand website, or command line.

### The OnDemand Website:

!!! info "[OnDemand Website](https://ondemand.pax.tufts.edu){:target="_blank" rel="noopener"}"

- Log in with your tufts credentials
- Once you are logged in you'll notice a few navigation options:

![](images/ondemand_layout_pic.png)

**To Access A Shell Terminal**

- Click on Clusters > Tufts HPC Shell Access

**To Access An Interactive App**

- Click on Interactive Apps
- Select the App you are interested in using
- For more information on how to access an interactive app take a look at our tutorials on RStudio and JupyterLab:


!!! info "[RStudio Interactive Session](../tools/r-rstudio.md){:target="_blank" rel="noopener"}"

!!! info "[JupyterLab Interactive Session](../tools/python-jupyter.md){:target="_blank" rel="noopener"}"


### Command Line:

- You can access the Tufts HPC Cluster via command line with:

    - The Terminal app on a Mac or Linux machine
    - PuTTy or Cygwin SSH or SecureCRT or other SSH clients on a Windows machine

- To Log in open one of the aformentioned apps and enter:


```sh
ssh your_utln@login.pax.tufts.edu
```

- Next log in with your Tufts Credentials
- At this point you are on a login node and should see something like the following:

!!! info "output"

    ```sh
    [your_utln@login-prod-02 ~]
    ```
    
- While on a login node please do not run any programs. For this you will need to get compute resources. See the following to get compute resources: 
    
!!! info "[Compute Resources](./compute-resources.md){:target="_blank" rel="noopener"}"
    
    
