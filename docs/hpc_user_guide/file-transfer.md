

!!! example ""
    
    You can transfer files to and from the cluster using:
    
    - OnDemand
    - A File Transfer Client
    - Command Line

## OnDemand

!!! note
    Only for transfering files size up to 976MB per file.

- Go to:

!!! info "[OnDemand]( https://ondemand.pax.tufts.edu/){ :target="_blank" rel="noopener"}"

- Under **`Files`**

![](images/Home.png)

- Using the **`Upload`** or **`Download`** buttons to transfer. 

![](images/Home.png)


## File Transfer Client

-  Download one of these free file transfer programs:

    - **[WinSCP](https://winscp.net/eng/index.php)** <img src="https://miro.medium.com/max/500/1*Of7JOwV0wZgDIjgaS4qKlQ.png" alt="WinSCP" width="20%">

    - **[FileZilla](https://filezilla-project.org/)** <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/01/FileZilla_logo.svg/1200px-FileZilla_logo.svg.png" alt="FileZilla" width="10%">

    - **[Cyberduck](https://cyberduck.io/)** <img src="https://cdn.cyberduck.io/img/cyberduck-icon-384.png" alt="CyberDuck" width="10%">

- Then use the following information to connect to the cluster:

    - Hostname: xfer.cluster.tufts.edu
    - Protocol: SCP or SFTP
    - Use port 22 for SFTP


## Command Line

!!! example "Terminology"

    - **Local_Path:** is the path to your files or directory on your local computer
    - **Cluster_Path:** is the path to your files or directory on the cluster
    - **Cluster Home Directory:** /cluster/home/your_utln/your_folder
    - **Cluster Home Directory:** /cluster/home/your_utln/your_folder
    - **Cluster Research Project Storage Space Directory:** /cluster/tufts/yourlabname/your_utln/your_folder


- Execute these commands from your local machine terminal using this general format to transfer files:


```sh
scp From_Path To_Path
```

```sh
rsync From_Path To_Path
```

!!! note
    If you are transfering very large files that could take hours to finish, we would suggest using `rsync` as it has ability to restart from where it left if interrupted.

### Download from cluster

```sh
scp your_utln@xfer.cluster.tufts.edu:Cluster_Path Local_Path
```

```sh
rsync your_utln@xfer.cluster.tufts.edu:Cluster_Path Local_Path
```

### Upload to cluster

```sh
scp Local_Path your_utln@xfer.cluster.tufts.edu:Cluster_Path 
```

```sh
rsync Local_Path your_utln@xfer.cluster.tufts.edu:Cluster_Path
```

!!! tip
    If you are transfering a directory use `scp -r` or `rsync -azP`

### Download from cluster

```sh
scp -r your_utln@xfer.cluster.tufts.edu:Cluster_Path Local_Path  
```

```sh
rsync -azP your_utln@xfer.cluster.tufts.edu:Cluster_Path Local_Path
```

### Upload to cluster

```sh
scp -r Local_Path your_utln@xfer.cluster.tufts.edu:Cluster_Path
```

```sh
rsync -azP Local_Path your_utln@xfer.cluster.tufts.edu:Cluster_Path
```
    

