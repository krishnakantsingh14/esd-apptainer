# esd-apptainer


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