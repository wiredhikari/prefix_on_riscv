# Porting Prefix
Gentoo Prefix allows to use the power of Gentoo and its tools on other distributions or operating systems, it allows to install packages into `${EPREFIX}` without root privileges. 

## Setting up the host system
Firstly, we should ensure that all the necessary packages are available on the host system so we can compile stage 1 and stage 2 by using the packages in host.
## Starting the script
After ensuring that you have all the necessary packages installed on the host you can start the bootstrap script. 
In case `bash` is missing from the host, you need to bootstrap it first with the `bootstrap-bash.sh` script. 
```
wget https://gitweb.gentoo.org/repo/proj/prefix.git/plain/scripts/bootstrap-bash.sh
chmod +x bootstrap-bash.sh
./bootstrap-bash.sh /var/tmp/bash
export PATH="/var/tmp/bash/usr/bin:${PATH}" 
```
The script does all the work we just need to debug issues while installing packages. Now download the [bootstrap-prefix.sh](https://gitweb.gentoo.org/repo/proj/prefix.git/plain/scripts/bootstrap-prefix.sh). 
```
wget https://gitweb.gentoo.org/repo/proj/prefix.git/plain/scripts/bootstrap-prefix.sh
chmod +x bootstrap-prefix.sh
bootstrap-prefix.sh 
```

<!-- ## Pushing work into the Portage tree -->

## Create the Profiles
The first profile was just a 'make it work' solution. Now a much more complete one must be created:
- `profiles/prefix` - Add initial profile in this directory

After the profile is committed, update the following files in the `profiles` subdir: 
- `arch.list` - Add prefix keyword here
- `profiles.desc` - Declare the profile status in profiles.desc as exp
Declare the profile in profiles.desc as exp for now.

## Add Symlink
After creating a profile, add the symlink to the new profile in `bootstrap-prefix.sh` script. You can refer to [riscv](https://github.com/gentoo/prefix/blob/master/scripts/bootstrap-prefix.sh#L426) symlink in the script.

## Getting through the stages
### Stage-1
After having a new profile, we will ensure Stage-1 installs coretools required for Portage to function. Then the latest python and portage will be installed in `${EPREFIX}/tmp`. 

### Stage-2
After getting a working Stage-1 and making a new profile, Stage-2 will start with emerging build utilities. Portage will use the system’s compiler to install GCC into `${EPREFIX}/tmp`; then coretools from the base profile. Portage will use the dependency system to emerge system. Eventually, this will lead to using Portage to emerge as a base system.

### Stage-3
After getting Stage-2 to work, we will use GCC installed by Portage to install a Gentoo base system in `${EPREFIX}`. Continue emerging some of the core toolchain packages that make sure we compile and link everything taking the Prefix into account. Post this `emerge -uDNv system` will be executed.

## Get ready to fix bugs
Now that we have the new profile and symlink setup, run the bootstrap script. We might get bugs during the three stages, you can post the bug on bugzilla or ask on `#gentoo-prefix`. 
## Start commiting KEYWORDS

Now that you have a working prefix, start to test and keyword packages. You can start by [keywording](https://devmanual.gentoo.org/keywording/index.html) packages. Make sure you use `~arch` instead of `arch` if you are unsure about the package being stable on the new profile.

<!-- ## Guide to testing packages on prefix -->

## Resources
- https://wiki.gentoo.org/wiki/Porting
- https://wiki.gentoo.org/wiki/Project:Prefix
- https://wiki.gentoo.org/wiki/Project:Prefix/Technical_Documentation\
- https://wiki.gentoo.org/wiki/Profile_(Portage)
- https://bugs.gentoo.org/755551