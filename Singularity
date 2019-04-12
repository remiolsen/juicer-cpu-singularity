BootStrap: docker
From: conda/miniconda2

%label
    Maintainer remi-andre.olsen@scilifelab.se

%post
    apt-get update
    apt-get install -y git openjdk-8-jdk coreutils gawk wget

    conda config --add channels bioconda
    conda install --yes bwa
 
    echo 'alias awk=gawk' >> $HOME/.bashrc

    cd /opt
    git clone https://github.com/theaidenlab/juicer.git
    chmod +x juicer/CPU/juicer.sh
    cd juicer && ln -s CPU scripts
    cd scripts/common
    wget -O juicer_tools.jar http://hicfiles.tc4ga.com.s3.amazonaws.com/public/juicer/juicer_tools.1.8.9_jcuda.0.8.jar 
    cd /bin && ln -s /opt/juicer/CPU/juicer.sh

    apt-get clean

