# ADMIN
This documentation is NOT for users, only if you are interested to compile, install and mange releases as done in this repo.

## Compiling and Installing Magic on Ubuntu 18.04

**SETTING UP LINUX FOR COMPILE**

- Prepare for building magic. 
- Base dev pkgs if not already installed ```sudo apt install build-essential linux-headers-‘uname -r‘```
- Some required packages if not already installed: **M4 preprocessor, tcsh, csh, Xlib.h, Tcl/Tk, Cairo, ncurses** (Ubuntu package names: ```m4, tcsh, csh, libx11-dev, tcl-dev, tk-dev, libcairo2-dev, libncurses-dev```)
 
**USING SOURCE FROM GIT REPO**

- **magic 8.3.464** compiled on linode VM running Ubuntu 22.04 kernel  5.15.0-100-generic #110-Ubuntu 03/09/24
- cd ```/home/ubuntu/sit-git-repos/eda-src```
- ```git clone git://opencircuitdesign.com/magic```
- ```cd magic```
- ```git checkout magic-8.3```
- Configure: To see all configure options ```./configure --help```. To install in root with all default options just type ```./configure```
- To install it in a user directory for eg. in ```$HOME/eda-bins/magic```: 
```bash 
./configure --prefix=$HOME/eda-bins/magic
```
- Make and install:
```bash
make
make install
```
- On successful compilation, the new compiled binaries/libs/should be in the target directory eg. ```$HOME/eda-bins/magic```
  
**IMPORTANT** Since this install directory needs to be used by other users by copying the install directory, replace the absolute path: eg. 
```
$HOME/eda-bins/magic -> $MAGIC_HOME
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
- Set the environment variables as shown in [README.md](README.md)

## Compiling and Installing on CentOS 7.9 (Core)

- Setup as described in the ngspice section
- Additionally check to see if the following packages have been installed: `tcsh` `csh` `tcl/tcl-devel` `tk/tk-devel` `cairo/cairo-devel/cairo-tools` `python3` `mesa-libGLw-devel` `mesa-libGL-devel` `mesa-libGLw-devel`
- Then compile the same as ngspice

## Creating a New Release

Check out this [doc](https://docs.github.com/en/github/administering-a-repository/releasing-projects-on-github/managing-releases-in-a-repository) in docs.github.com on how to create and manage releases.
  
- Check out the difference between the previous and current version: eg.
```bash
  diff -qr ~/eda-bins/magic  <GIT-INSTALL_DIR>/eda-magic/glnxa64
```
- Copy only the differences to the git repo, `add`, `commit` and `push` to the `github`.
  - **IMPORTANT** Make sure you backup the previous binaries in case you need it.
- Navigate to the main repo page eg. github.com/silicon-vlsi-org/eda-magic
- To the right of the list of files, click **Create a new release** under the **Release** section.
- Tag the release version eg. ```v8.3.0```
  - The major release ```v8.3``` reflects the version of magic.
  - The minor release ```vx.x.0``` reflects any changes done locally eg. examples, docs, etc.
- Do not add any binaries and do not select pre-release.
- Publish the release. 
- Now users can checkout this version eg. ```git checkout v8.3.0```
  
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


