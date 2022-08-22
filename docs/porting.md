# Porting Prefix
- Introduction
Gentoo Prefix allows to use the power of Gentoo and it's tools on other distributions or operating systems.

## Setting up the host system
Firstly, we should ensure that all the necessary packages are available on the host system so we can compile stage 1 and stage 2 by using the packages in host.

- list of packages on host needed for stage 1 and 2

## Getting through the stages

After ensuring that you have all the necessary packages installed on the host you can start the bootstrap script. 
Incase `bash` is missing from the host, you need to bootstrap it first with the bootstrap-bash.sh script. 
```

```
The script does all the work we just need to debug issues while installing packages.


### Starting the script

### Stage-1
### Stage-2
### Stage-3

## Pushing work into the Portage tree
So to use 
### Create the profiles
- profiles/prefix - Add initial profile here
- profiles/arch.list - Add prefix keyword here
- profiles/profiles.desc - Declare the profile status in profiles.desc as exp

### Add Symlink
After creating a profile, add the symlink to the new profile in bootstrap-prefix.sh script.


### Start commiting KEYWORDS

Now that you have a working prefix, start to test and keyword packages. You can start by keywording packages

## Guide to testing packages on prefix

### Relevent Links