## anbox-dinit
a project to port anbox files for dinit.

## What is it?
These are the files to use anbox on dinit based operating systems

## What is anbox?
Anbox is a project for running android apps on other Linux-based operating systems (such as GNU/Linux). for more info visit https://anbox.io

## How to install it?

### Step 1: Install binder & ashmem modules

#### The first method: you can use linux-zen package.

install on artix linux:

**Note: for `pacman` command, you need root access. normal users use `sudo` before `pacman`**
`pacman -S linux-zen`

#### The second method: compiling linux kernel from source with ashmem & binder

If you can do this, you know how to set it up.

### Step 2: Enabling binder module 
When enabling the anbox support option, the binder and ashmem modules are built-in. You don't have to load them.You just need to boot kernel with following parameters: 
`binder.devices=binder,hwbinder,vndbinder,anbox-binder,anbox-hwbinder,anbox-vndbinder`

### Step 3: Mounting binderfs

**Note: You need root access for this. normal users use `sudo` before commands**

Create binderfs directory:`mkdir /dev/binderfs`

Mount binder for this session:`mount -t binder binder /dev/binderfs`

set binderfs on `/dev/fstab/` always, for mounting binderfs by system: 
````
binder                         /dev/binderfs binder   nofail  0      0
````
### Step 4: Install anbox
Install anbox-nosystemd-git:
**Note: for `pacman` command, you need root access. normal users use `sudo` before `pacman`**
````
cd ~
git clone https://github.com/Luciogi/artix_pkg.git
cd artix_pkg/anbox-systemd-git
pacman -S --needed base-devel
makepkg -si
````
Install anbox-dinit(This project):
````
cd ~
git clone https://gitlab.com/mobin2008/anbox-dinit.git
cd anbox-dinit
makepkg -si
````
### Step 5: Enable services
Enable `anbox-container-manager`:
**Note: for `dinitctl` command, you need root access. normal users use `sudo` before `dinitctl`**
````
dinitctl start anbox-container-manager # For loading in this session
dinitctl enable anbox-container-manager # For loading in startup
````
Enable `anbox-session-manager`:
**Note: No longer needed**
````
dinitctl start anbox-session-manager # For loading in this session
dinitctl enable anbox-session-manager # For loading in startup
````
### Step 6: Use anbox xD
Done!

## License

## Screenshots

