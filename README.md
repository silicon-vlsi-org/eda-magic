# MAGIC LAYOUT

[Magic] is the most popular open-source Layout tool written in the 1980's at Berkeley by John Ousterhout (now famous for writing scripting languuage Tcl) and now maintained by Tim Edwards (opencircuitdesign.com/magic).

This repo contains pre-compiled binaries/libraries/etc of **Magic Version 8.3** for **64-bit 18.04 Ubuntu Linux**. It's also tested on a light-weight Ubuntu-variant LXLE distro. If you are interested in compiling from the source, instructions in Section-[Compiling and Installing Magic](#compiling-and-installing-magic) should help.

## Setting Up Magic
**NOTE**: The below is path is an example. Just make sure it matches your particular path.
```bash
export MAGIC_HOME=$HOME/eda-magic
export CAD_ROOT=$MAGIC_HOME/lib
export PATH=$PATH:$MAGIC_HOME/bin
```

## Compiling and Installing Magic
**NOTE** This repo contains pre-compiled binaries/libraries/etc for **64-bit 18.04 Ubuntu Linux**. It's also tested on a light-weight Ubuntu-variant LXLE distro. If you are interested in compiling from the source, instructions in this section should help.
- Clone and checkout the git repo:
```bash
git clone git://opencircuitdesign.com/magic
cd magic
git checkout magic-8.3
```
- Some required packages if not already installed: **M4 preprocessor, tcsh, csh, Xlib.h, Tcl/Tk, Cairo, ncurses** (Ubuntu package names: ```m4, tcsh, csh, libx11-dev, tcl-dev, tk-dev, libcairo2-dev, libncurses-dev```)
- Configure: To see all configure options ```./configure -----help```. To install in root with all default options just type ```./configure```
- To install it in a user directory for eg. in ```$HOME/eda-magic```: 
```bash 
./configure --prefix=$HOME/eda-magic
```
- Make and install:
```bash
make
make install
```
**IMPORTANT** If this install directory needs to be used by other users by copying the install directory, replace the absolute path: eg. 
```
$HOME/eda-magic -> $MAGIC_HOME
```
- Make the above change in the following files:
```bash
  bin/magic, bin/ext2sim, bin/ext2spice, lib/magic/tcl/magic.tcl
```
- Additionally, since the ```magic.tcl``` is sourced from ```bin/magic``` the environment variable needs to be passed by adding the following statement to ```magic.tcl```:
```tcl
set MAGIC_HOME $::env(MAGIC_HOME)
```
- Also, magic internally sets variable ```CAD_ROOT``` to the absolute path as well which fortunately can be set in the shell environment variable as well (eg. bashrc).
- Set the following environment variables
```bash
export MAGIC_HOME=$HOME/eda-magic
export CAD_ROOT=$MAGIC_HOME/lib
export PATH=$PATH:$MAGIC_HOME/bin
```

# Tasks
- [ ] 

* * *

[OpenRAM]:              https://openram.soe.ucsc.edu/
[OpenRAMgit]:           https://github.com/VLSIDA/OpenRAM 
[OpenRAMpaper]:         https://ieeexplore.ieee.org/document/7827670/
[SCMOS]:                https://www.mosis.com/files/scmos/scmos.pdf
[NGSpice]:              http://ngspice.sourceforge.net
[NGSpiceMan]:           http://ngspice.sourceforge.net/docs/ngspice-html-manual/manual.xhtml
[Magic]:                http://opencircuitdesign.com/magic/
[Netgen]:               http://opencircuitdesign.com/netgen/


