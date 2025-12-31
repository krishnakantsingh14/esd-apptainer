# esd-apptainer

**Before Running apptainer**
Please add and change these variable to avoid filesystem error:
```
export APPTAINER_CACHEDIR=/p/scratch/<>
export APPTAINER_TMPDIR=/p/scratch/<>
```

Basic Apptainer command 


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


