## Modules

- A tool that **simplifies** shell initialization and lets users easily modify their environment during the session with modulefiles
- Each modulefile contains the **information** needed to configure the shell for an application. (PATH, LD_LIBRARY_PATH, CPATH, etc.)
- Modules are useful in managing **different versions** of applications. 
- Modules can also be bundled into metamodules that will load an entire **set of different applications (dependencies)**. 


!!! example "Module  Commands"

    - `module av` : to check all available modules
    - `module load` : to load a particular module
    - `module list` : to list modules that are loaded
    - `module purge` : purge any loaded modules

### Check All Available Modules

- To check **ALL available modules** installed on the cluster:

```
module av
```

- Upon login, environment `PATH` is set for the system to search executables:

```
echo $PATH
```
 
!!! info "output"

    ```
    /usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/cluster/home/your_utln/bin:/cluster/home/your_utln/.local/bin
    ```

- For example, I would like to use `blast`, to **check** what versions of blast are available:


```
module av blast
```

!!! info "output"

    ```
    ---------------------- /opt/shared/Modules/modulefiles-rhel6 ----------------------
    blast/2.2.24 blast/2.2.31 blast/2.3.0  blast/2.8.1

    ---------------------- /cluster/tufts/hpc/tools/module ----------------------------
    blast-plus/2.11.0
    ```

### Load Desired Module

- To **load** the version I would like to use, and use it:

```
module load blast-plus/2.11.0
```
 
### Check Which Modules Are Loaded

- To **check** which modules are loaded:

```
module list
```

!!! info "output"

    ```
    Currently Loaded Modulefiles:
        1) use.own     2) blast-plus/2.11.0
    
    ```

### Check The Tool Version

- To determine the tool **version**:
 
```
blastp -version
```

!!! info "output"

    ```
    blastp: 2.11.0+
     Package: blast 2.11.0, build Aug 17 2021 06:29:22 
    ```


### Check Module Paths

- To determine the **module paths**:

```
which blastp
```

!!! info "output"
 
    ```
    /cluster/tufts/hpc/tools/spack/linux-rhel7-ivybridge/gcc-9.3.0/blast-plus-2.11.0-ip4jcqabi3a2jscgusnkipvib6goy5mv/bin/blastp
    ```


```
echo $PATH
```

!!! info "output"

    ```
    /cluster/tufts/bio/tools/edirect:/cluster/tufts/hpc/tools/spack/linux-rhel7-ivybridge/gcc-9.3.0/blast-plus-2.11.0-ip4jcqabi3a2jscgusnkipvib6goy5mv/bin:/cluster/home/your_utln/.iraf/bin:/cluster/home/your_utln/.iraf/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/cluster/home/your_utln/bin:/cluster/home/your_utln/.local/bin 
    ```
  
## To Unload Modules

- To **unload** a loaded module:


```
module unload blast-plus/2.11.0
```
  
```
echo $PATH
```

!!! info "output"

    ```
    /usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/cluster/home/your_utln/bin:/cluster/home/your_utln/.local/bin
    ```

- To **unload ALL** of the loaded modules:


```
module purge
```
  
```
module list
```

!!! info "output"

    ```
    No Modulefiles Currently Loaded.
    ```

