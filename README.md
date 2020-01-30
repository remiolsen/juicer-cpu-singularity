# Juicer-singularity

Singularity version of Juicer (https://github.com/aidenlab/juicer)

Two supported modes:
  * CPU: singularity exec --app slurm juicer.sif juicer.sh -D /opt/juicer [params]
  * SLURM: singularity exec --app cpu juicer.sif juicer.sh -D /opt/juicer [params]
