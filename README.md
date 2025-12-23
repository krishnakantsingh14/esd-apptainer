# esd-apptainer

## Building and running arbor inside an apptainer container 
* Step 1: Building a container
```
apptainer build --fakeroot mpiArbor.sif mpiArbor.def
```
* Step 2: Spawnning mpi based jobs inside container on compute nodes:
```
srun --mpi=pmix --nodes=2 --ntasks-per-node=24 --cpus-per-task=1 --account=<> apptainer exec --nsshare  mpiArbor.sif /opt/src/arbor-src/build/bin/busyring
```




## Basic Apptainer command 

Running a shell inside apptainer 

```bash 
apptainer shell rocky.sif
```
Executing apptainer command 

```
apptainer exec rocky.sif ls
```

Run apptainer as a sandbox (like an isolated environment)
```
apptainer run rocky.sif
```


## Building a def file

```def 
# Define base image
Bootstrap: docker 
From: rockylinux:9

# Metadata
%labels 
    Author Krishna
    Version v1.0
    Description Rocky Linux base container with tools


%post 
    dnf -y update
    dnf -y install python3 vim 

%environment
    export PATH=/usr/local/bin:$PATH

%runscript 
    echo "Hello from apptainer file!"
    /bin/bash
```

run it as `apptainer build basic.sif basic.def` then `apptainer run basic.sif`

## To create arbor container image

```
# Define base image
Bootstrap: docker 
From: rockylinux:9

# Metadata
%labels 
    Author Krishna
    Version v1.0
    Install arbor


%post 
    dnf -y update
    dnf -y --nobest install python3 python3-pip vim wget make gcc g++
    pip3 install --no-cache-dir arbor 
    dnf clean all #clean to save space

%environment
    export PATH=/usr/local/bin:$PATH
    export PYTHONUNBUFFERED=1    # Make Python output appear immediately

%runscript 
    echo "Hello from apptainer with arbor installed"
    python3

%test
    python3 -c "import arbor as A; print (A.print_config())"

```
