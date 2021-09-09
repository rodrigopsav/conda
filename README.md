# Getting started with Conda

Conda is an open source package and environment management system that runs on Windows, macOS and Linux. Conda easily creates, saves, loads and switches between environments on your local computer. It was created for Python programs, but it can package and distribute software for any language. Conda is widely used by  python users to create personalized environments to run specific projects. Environments created by Conda can also be reproduced on other machines. You will learn how to use Conda, create environments, install packages and create environment backups.

## Topics

[Conda tutorials](#conda-tutorials)   
[Installing miniconda](#installing-miniconda)   
[Managing conda environments](#managing-conda-environments)   
* [Add conda channels](#add-conda-channels)   
* [Creating conda environment](#creating-conda-environment)   
* [Changing MKL library in conda environments](#changing-mkl-library-in-conda-environments)   
* [Listing conda environments](#listing-conda-environments)   

[Sharing and restoring Conda environment](#sharing-and-restoring-conda-environment)   
* [Sharing an environment](#sharing-an-environment)   
* [Sharing an environment across Mac OS, Windows, and Linux](#sharing-an-environment-across-mac-os-windows-and-linux)   
* [Removing packages and conda environment](#removing-packages-and-conda-environment)   
* [Creating an environment from an .yml file](#creating-an-environment-from-an-.yml-file)   


## Conda tutorials
[miniconda vs anaconda](https://linuxnetmag.com/miniconda-vs-anaconda/)   
[getting started with conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html)   
[managing conda environments](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)   
[managing conda packages](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html)   
[conda cheat sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)   

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


## Installing miniconda
```
### Downloading miniconda
mkdir ~/softwares
cd ~/softwares
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

### Making bash executable
chmod +x Miniconda3-latest-Linux-x86_64.sh

### Installing miniconda
./Miniconda3-latest-Linux-x86_64.sh -b -p ~/softwares/miniconda3 -f
source ~/softwares/miniconda3/bin/activate
conda init bash
rm Miniconda3-latest-Linux-x86_64.sh
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


## Managing conda environments

### Add conda channels

```
conda config --add channels defaults
conda config --add channels conda-forge 
conda config --add channels anaconda
conda config --add channels bioconda
conda config --add channels biobuilds
conda config --add channels R
conda config --add channels intel
conda config --add channels trent
conda config --add channels plotly
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>



### Creating conda environment

```
conda create --yes --name myEnvironment python=version
```
or
```
conda create -y -n myEnvironment python=version
```

Examples
```
### Bioinformatics environment
conda create -y -n bioinfo python=3.8
conda install -y -n bioinfo -c bioconda bwa-mem2
conda install -y -n bioinfo -c bioconda htslib=1.9
conda install -y -n bioinfo -c bioconda samtools=1.9
conda install -y -n bioinfo -c bioconda bcftools=1.9
conda install -y -n bioinfo -c bioconda gatk4

### Python environment for deep learning
conda create -y -n dl python=3.8
conda install -y -n dl numpy
conda install -y -n dl pandas
conda install -y -n dl statsmodels
conda install -y -n dl -c plotly  plotly
conda install -y -n dl plotnine
conda install -y -n dl matplotlib
conda install -y -n dl seaborn
conda install -y -n dl bokeh
conda install -y -n dl tensorflow
conda install -y -n dl keras
conda install -y -n dl scikit-learn
conda install -y -n dl pytorch

### R v3.6
conda search r-base
conda search r-essentials

conda create -y -n r3.6 -c conda-forge r-base=3.6.3 r-essentials=3.6 python=3.8
conda install -y -n r3.6 "libblas=*=*openblas" 

### R v4.1
conda create -y -n r4.1 -c conda-forge r-base=4.1.0 r-essentials=4.1 python=3.8
conda install -y -n r4.1 "libblas=*=*openblas" 
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


### Changing MKL library in conda environments
https://conda-forge.org/docs/maintainer/knowledge_base.html?highlight

```
conda install -y -n r3.6 "libblas=*=*mkl" 
conda install -y -n r3.6 "libblas=*=*openblas" 
conda install -y -n r3.6 "libblas=*=*blis" 
conda install -y -n r3.6 "libblas=*=*netlib"
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


### Listing conda environments

```
conda env list
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


### Changing conda environment

```
### Activate r4.1 environment
conda activate r4.1

### Activate bioinfo environment
conda activate bioinfo

### Deactivate conda environments
conda deactivate
conda deactivate

### Activate more than one environment
conda activate r4.1
conda activate --stack  bioinfo

conda deactivate
conda deactivate
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


## Sharing and restoring Conda environment

### Sharing an environment

```
conda activate bioinfo
conda env export bioinfo > bioinfo.yml
```
or
```
conda env export -n bioinfo > bioinfo.yml
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


### Sharing an environment across Mac OS, Windows, and Linux

```
conda env export -n bioinfo --from-history> bioinfo_fh.yml
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


### Removing packages and conda environment

```
conda activate bioinfo

### Listing packages in bioinfo environment
conda list

### Removing a package: bwa-mem2
conda remove -y -n bioinfo bwa-mem2

### Removing bioinfo environment
conda remove -y -n bioinfo --all
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>


### Creating an environment from an .yml file

```
### Listing conda environments
conda env list

### Creating bioinfo environment from .yml
conda env create -f bioinfo.yml
```

<div align="right">
    <b><a href="#getting-started-with-conda">↥ back to top</a></b>
</div>
