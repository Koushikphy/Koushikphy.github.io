---
title: "Things to do after installing ubuntu"
tags: 
    - ubuntu
    - softwares
category:
    - Linux
date: 2019-05-19
toc: false
# toc_sticky: true
---
Ubuntu is a great choice for a linux and the most popular one too. But just after installing ubuntu you have to set it up properly before using it. Now the following description are listed as the things I like to do after installing a fresh ubuntu installation, but the set up is completely depend on the user's choice and how they want to use their system. you can skip some steps if you feel you don't need them.

## 1. Setting up proxy
Most of the times I use ubuntu behind a institute/corporate proxy, so setting up proper proxy settings are always my first step after installing ubuntu or any OS for that matter.
### a. Set up proxy in gnome settings
Go to _System > Network > Network Proxy_ and set it up as manual with proper proxy and port. This can also be done from terminal by running,

```
gsettings set org.gnome.system.proxy mode 'manual'
gsettings set org.gnome.system.proxy.http host 'http://username:password@proxy'
gsettings set org.gnome.system.proxy.http port port
gsettings set org.gnome.system.proxy.ftp host 'http://username:password@proxy'
gsettings set org.gnome.system.proxy.ftp port port
gsettings set org.gnome.system.proxy.https host 'http://username:password@proxy'
gsettings set org.gnome.system.proxy.https port port
```

### b. Setup environment proxy
Open the file `/etc/apt/apt.conf` or create if not exist and put the following lines. Also add the same lines in `/etc/environment`
```bash
Acquire::http::proxy "http://username:password@proxy:port";
Acquire::https::proxy "http://username:password@proxy:port";
Acquire::ftp::proxy "http://username:password@proxy:port";
```

Add the following lines in `~/.bashrc` and run `source ~/.bashrc` to take effect.
```bash
export http_proxy="http://username:password@proxy:port";
export https_proxy="http://username:password@proxy:port";
export HTTPS_PROXY="http://username:password@proxy:port"
export HTTP_PROXY="http://username:password@proxy:port"
```

## 2. Check for updates
Though you have just installed a new distro, there may be some new updates regarding some features or bug fixes. So update the system using
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
```

## 3. Installing some useful softwares
Now its time to install some software. Followings are the software I like to install, but you may skip those you don't need
1. `ubuntu-restricted-extras` : Media codecs for playing multimedia files
2. `vlc` : Media player
3. `uget` : Download manager
4. `gfortran` : Fortran compiler
5. `gnuplot` : Plotter
6. `vim` : Editor
7. `python-dev` : Python header files 
8. `python-pip` : Python package manager
10. `gnome-tweak-tool` : System setting tweaker
11. `openssh-server` : SSH server
12. `okular` : Document viewer
13. `libatlas-base-dev liblapack-dev libblas-dev` : ATLAS, LAPACK & BALS libraries
14. `texlive-full texmaker texstudio` : LaTeX compiler and editors.
15. `nodejs npm` : Node JS and package manager. (Stable but not latest)


Install all the above mentioned softwares by running in terminal,
```
sudo apt-get install ubuntu-restricted-extras vlc uget gfortran gnuplot python-pip vim python-dev gnome-tweak-tool openssh-server okular libatlas-base-dev liblapack-dev libblas-dev nodejs npm texlive-full texmaker texstudio
```

## 4. Install gnome shell extensions
Gnome shell extensions are very useful for customizing ubuntu as your choice. These are the shell extensions I like to use
1. `Alternate TAB` : Prevent alt-TAB for switching between windows from different workspaces.
2. `Caffine` : Switch on/off auto turning off of the monitor
3. `Workspace Indicator`: Put a indicator for current workspace at the top
4. `Arc menu` : Put a nice windows start menu like button.  

For detailed guide about how to install them follow this guide [follow this guide.](https://itsfoss.com/gnome-shell-extensions/) 

## 5. Installing some useful python libraries

I use these python libraries regularly, install them by running 
```
pip install numpy scipy h5py matplotlib pandas nose setuptools sympy ipython
```
You can install libraries like `numpy` or `scipy` from the ubuntu repo too, but they doesn't keep the latest version so I like to install them using the `pip` package manager.

## 6. Install Stacer Linux system monitoring and optimizer
[Stacer](https://oguzhaninan.github.io/Stacer-Web/)  is a great tool for linux. Things like app uninstall, process monitoring, removing trash & cache etc. can be done easily from here. Run the following to install it

```
sudo -E add-apt-repository ppa:oguzhaninan/stacer
sudo apt update
sudo apt install stacer
```

## 7. Install new icon pack
I dont like the default icons of ubuntu. They may not be that bad but I like to use `numix-icon-theme-circle` icon pack for my system

```
sudo -E add-apt-repository ppa:daniruiz/flat-remix
sudo apt update
sudo apt install numix-icon-theme-circle
```
Now open ubuntu tweak tool and set up new icons from appearance menu.

## 8. Setting up git
If you are a programmer and living in 2019 then you must be using `git` for managing your projects and programmes. Install and setup git by 
```
sudo apt install git
git config --global user.name "Your Name"
git config --global user.email your_email
git config --global http.proxy http://username:password@proxy:port
git config --global https.proxy https://username:password@proxy:port
```

## 9. Setting up VS Code
I love VS Code text editor. Its an all in one package that is more like an IDE than a mere text editor. VS code can be installed from the [official site.](https://code.visualstudio.com/) The most useful things about VS Code are its extensions. I usually use these extensions for my day to day work,  
1. Beautify
2. Better Align
3. Better Comments
4. Bracket Pair Colorizer
5. Code Runner
6. GitLens
7. jumpy
8. Material Color Theme
9. Modern Fortran
10. Open native terminal
11. Path Intellisense
12. Python  
Also my VS Code settings are available [here](https://gist.github.com/Koushikphy/f91ff8cf61953360c6eebd264eef7d8c).



## 10. Some smaller tweaks and settings
### a. Isolate windows for different workspaces
```
gsettings set org.gnome.shell.extensions.dash-to-dock isolate-workspaces true
```
### b. Fix `Errors were encountered while processing: install-info`
```
sudo mv /var/lib/dpkg/info/install-info.postinst /var/lib/dpkg/info/install-info.postinst.bad
```
