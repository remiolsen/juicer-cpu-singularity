BootStrap: docker
From: conda/miniconda2

%labels
    Maintainer remi-andre.olsen@scilifelab.se

%post
    apt-get update
    apt-get install -y git openjdk-8-jdk coreutils gawk wget

    conda config --add channels bioconda
    conda install --yes bwa=0.7.17

    echo 'alias awk=gawk' >> $HOME/.bashrc

    apt-get clean


%help
    https://github.com/remiolsen/juicer-singularity (built $NOW)
    Singularity version of Juicer (https://github.com/aidenlab/juicer)
    juicer-$REV
    Two supported modes:
      * CPU: singularity exec --app slurm juicer.sif juicer.sh -D /scif/apps/cpu/juicer
      * SLURM: singularity exec --app cpu juicer.sif juicer.sh -D /scif/apps/slurm/juicer


################

### CPU

%appinstall cpu
  git clone https://github.com/theaidenlab/juicer.git && cd juicer
  NOW=`date`
  REV=`git rev-parse --short HEAD`
  ln -s CPU scripts
  cd scripts/common
  wget -O juicer_tools.jar http://hicfiles.tc4ga.com.s3.amazonaws.com/public/juicer/juicer_tools.1.8.9_jcuda.0.8.jar

%apphelp cpu
  This is the CPU version of Juicer

%appenv cpu
  export PATH="/scif/apps/cpu/juicer/scripts/:$PATH"




### SLURM

%appinstall slurm
  git clone https://github.com/theaidenlab/juicer.git && cd juicer
  NOW=`date`
  REV=`git rev-parse --short HEAD`
  ln -s SLURM/scripts
  cd scripts
  wget -O juicer_tools.jar http://hicfiles.tc4ga.com.s3.amazonaws.com/public/juicer/juicer_tools.1.8.9_jcuda.0.8.jar

%apphelp slurm
  This is the SLURM version of Juicer

%appenv slurm
  export PATH="/scif/apps/slurm/juicer/scripts/:$PATH"
