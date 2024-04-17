---
title: "Setting up Intel OneAPI compilers in Linux"
tags: 
    - intel compilers
    - intel oneAPI
    - linux
category:
    - Linux
date: 2023-04-20
toc: false
layout: single
classes: wide
excerpt: Setting up Intel OneAPI compilers in Linux
---


### Offline installation of Intel oneAPI Compilers:

Download the Intel oneAPI Base Toolkit for Linux install:

https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html?operatingsystem=linux&distributions=offline

The Base Toolkit contains the core tool set including the C/C++ compilers, Python interpreter, MKL, profilers etc. On ther hand, Intel oneAPI HPC Toolkit need to be installed as an add-on to the Base Toolkit in order to use things like Fortran compilers, MPI etc. 

Download the Intel oneAPI HPC Toolkit for Linux and install:

https://www.intel.com/content/www/us/en/developer/tools/oneapi/hpc-toolkit-download.html?operatingsystem=linux&distributions=offline


---

### Online installation of Intel oneAPI Compilers:

Run the following commands

```bash
wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2023.PUB
sudo apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2023.PUB
rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2023.PUB
echo "deb https://apt.repos.intel.com/oneapi all main" | sudo tee /etc/apt/sources.list.d/oneAPI.list
```  
```bash
sudo apt-get update
sudo apt-get install intel-oneapi-compiler-fortran intel-oneapi-mkl
```


Note: The compilers will auto update each time `apt` updates softwares.


### Set up the compilers:

By default oneAPI is installed in the default directory (`/opt/intel/oneapi` or `~/intel/oneapi`). A `setvars.sh` file should be available in that folder (or whatever directory you have specified during the installation). Source that file in order to use the compilers. Assuming the default directory, one can add the following line in the `~/.bashrc` 
```bash
source /opt/intel/oneapi/setvars.sh &> /dev/null
```
The `/dev/null` suppresses the source messages. This will make all the installed toolkits available for you. Otherwise, you can selectively switch on the tools you need. For example, assuming a file `configfile.txt` with the following content
```bash
default=exclude
compiler=latest
mkl=latest
mpi=latest
```
sourcing the `setvars.sh` like this
```bash
source /opt/intel/oneapi/setvars.sh --config=/opt/intel/oneapi/configFile.txt &> /dev/null
```
will only enable the compilers, mkl and MPI.

### Intel compilers moving to llvm
Since 2021, Intel has started to adopt llvm for their compiler suit, getting rid of their own architecture. Read this blog to learn more:
https://community.intel.com/t5/Blogs/Tech-Innovation/Tools/Intel-C-C-compilers-complete-adoption-of-LLVM/post/1305373. This means, Intel's famous `icc`/`ifort` will be deprecated in future, with `icc` being deprecated in 2024. Therefore, for any future project, it is highly recommended to use the llvm based `icx` and `ifx` as C/C++ and Fortran compiler, respectively.