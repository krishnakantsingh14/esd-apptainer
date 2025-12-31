# esd-apptainer

**Before Running apptainer**
Please add and change these variable to avoid filesystem error:
```
export APPTAINER_CACHEDIR=/p/scratch/<>
export APPTAINER_TMPDIR=/p/scratch/<>
```

# Basic Apptainer command 
**To build the container**

```
apptianer build --fakeroot arborcuda.sif arborcuda.def
```
**To exec the container**
```
srun -A <> --nodes=<> --gpus-per-node=<> --partition=<> --output=out_%j.out --error=err_%j.err --nv apptainer exec arborcuda.sif mycode
```
or 
 
```
srun -A <> --nodes=<> --gpus-per-node=<> --partition=<> --output=out_%j.out --error=err_%j.err --nv apptainer exec arborcuda.sif bash
```



Running a shell inside apptainer 

```bash 
apptainer shell rocky.sif
```


```
apptainer exec rocky.sif ls
```

Run apptainer as a sandbox (like an isolated environment)
```
apptainer run rocky.sif
```

#Apptainer Chache

* To list all the cache 
* `apptainer cache list`
* To clean: before cleaning, please use dry-run
* `apptainer cache clean --dry-run` 


