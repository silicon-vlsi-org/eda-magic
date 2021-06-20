# MAGIC LAYOUT
### Current distribution version 8.3.178 
Precompiled for **64b 18.04 Ubuntu and Ubuntu-based Linux**. It's also tested on a light-weight Ubuntu-variant LXLE distro. If you are interested in compiling from the source, instructions in [ADMIN.md:Compiling and Installing Magic](ADMIN.md) should help.

[Magic] is the most popular open-source Layout tool written in the 1980's at Berkeley by John Ousterhout (now famous for writing scripting languuage Tcl) and now maintained by Tim Edwards (opencircuitdesign.com/magic).

## Table of Content
- [Downloading & Setting Up Magic](#downloading-&-setting-up-magic)
- [Quick Start Guide](#quick-start-guide)

## Downloading & Setting Up Magic

- Change directory ```cd``` to install directory <INSTALL_DIR> e.g. ```/home/user/cad```
- To download from the ```git``` repository:
  - ```git clone https://github.com/silicon-vlsi-org/eda-magic```
- Change directory to the installed magic directory eg. ```cd eda-magic```
- Checkout the desired version: ```git checkout v8.3.178```
  - To make sure you are on the right version type ```git branch``` and your output should have a line like this :
  - ```* (HEAD detached at v8.3.178)```

- Add the following environment variables in your `~/.bashrc` (**NOTE**: The path below is an example, make sure it matches your particular path) 

```bash
export MAGIC_HOME=<INSTALL_DIR>/eda-magic/glnxa64
export CAD_ROOT=$MAGIC_HOME/lib
export PATH=$PATH:$MAGIC_HOME/bin
```

## Quick Start Guide
Few examples are in the ```examples``` folder to quickly get you started.


* * *

[OpenRAM]:              https://openram.soe.ucsc.edu/
[OpenRAMgit]:           https://github.com/VLSIDA/OpenRAM 
[OpenRAMpaper]:         https://ieeexplore.ieee.org/document/7827670/
[SCMOS]:                https://www.mosis.com/files/scmos/scmos.pdf
[NGSpice]:              http://ngspice.sourceforge.net
[NGSpiceMan]:           http://ngspice.sourceforge.net/docs/ngspice-html-manual/manual.xhtml
[Magic]:                http://opencircuitdesign.com/magic/
[Netgen]:               http://opencircuitdesign.com/netgen/


