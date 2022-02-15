---
title: "Better & Faster alternative to common bash utilities"
tags: 
    - linux
    - bash
    - linux-utilities
category:
    - Linux
date: 2022-02-15
toc: false
layout: single
classes: wide
# link: https://github.com/Koushikphy/Shared-Expense-Manager
excerpt: "Linux utilities you should use instead"
---


Better and faster alternative to regularly use linux utilities  

### `fd`: replacement for `find`
Install with `sudo apt install fd-find` or download the latest release from https://github.com/sharkdp/fd/releases  
Preferred usage `fd (part of) file_name [-e extension] [-S size_specs] [-x executable {}] [-t d/f] [-E exclude]` 

---
### `exa`: replacement for `ls`  
Download latest release from https://github.com/ogham/exa/releases  
Preferred usage `exa -l -T -L <depth> --no-user`  

---
### `dust`: replacement for `du`
Install with `cargo install du-dus` or download the latest release from https://github.com/bootandy/dust/releases  
Preferred usage `dust [-b]`

---
### `dua`: replacement for `du`
Install it with `cargo install dua-cli` or download the latest release from https://github.com/Byron/dua-cli/releases  
Its preferable for its interactive explorer (like `ncdu`) use it with `dua i`

---
### `fzz`: replacement for `Ctrl+R`(reverse-i-search)
Install with `git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf && ~/.fzf/install`  
Now source the `~/.bashrc` and it will replace the Ctrl+R, bash reverse with `fzf`