---
title: "Linking libraries during compilation"
tags: 
    - linker
    - libraries
    - linux
category:
    - Linux
date: 2020-05-10
toc: false
layout: single
classes: wide
---

Linking libraries is very common in compiling source codes. `ld` or The GNU Linker is very useful in this regard. But to properly link the libraries to the source codes understanding the linker utility is important and the options available to it.

## -l namespec / -l :filename
`-l namespec` or `--library=namespec` links a library named `namespec`. This actually searches for a archied or shared library object file named `libnamespec.so` or `libnamespec.a` in available path. If one '`:`' is provided at the begining then the linker, it searches for `filename` instead  
NOTE: The space between `-l` and `namespec` is not mandatory.

## -L searchdir
By default the linker searches for the file in the available path but if the file is not available in the path but instead present in a directory named `searchdir`, one can use `-L searchdir` or `--library-path=searchdir` to let the linker know the location of the available file.

## Available paths
The available paths to the linker utility can be checked by debugging `ld`. Run
```bash
ld --verbose | grep SEARCH_DIR
```  

## Common problem: cannot find `-lfftw3`
One very common problem we face while linking libraries is, it fails to link the library, while the library is installed properly. It happens beacuse the linker can not find the file in available path or the library is installed with different names. If the file is not available in the default path then its quite easy to provide the path with `-L`. But if the file is installed with different name usually, with a version name at the end, then its probably best to create a symbolic link of the file at a proper location.  
### 1. Finding the installed files
Before creating the symbolic link, we need to find location and name of the file, installed as a library. If we know then library is `fftw3` then the file name must be `libfftw3.so` or something very similar, like this `libfftw3.so.3.5.1`, the number at the end being the version number. So, simply search for this file in your system
```
find / -name libfftw* -type f
```
and note the location and full name of the file.  
### 2. Creating symbolic link
Once you find the location and name, create a soft symbolic link in a place available to the path.
```
ln -s /path_to_file/libfftw.so.3.5.1 /path_available_to_linker/libfftw.so
```
Now the linker utility will easily find the symolic link and from there the actual library files.  
##### Useful Links:
<a href='https://linux.die.net/man/1/ld'>https://linux.die.net/man/1/ld</a>
