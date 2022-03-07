## anbox-dinit
a project for porting anbox files for dinit.

## What is this?
This is files for using anbox on dinit based operating systems

## What is anbox?
Anbox is a project for running android apps on other Linux-based operating systems (such a GNU/Linux). for more info see https://anbox.io

## How to install it?

### Step 1: Installing binder & ashmem modules

#### The first way: you can using linux-zen package.

installing on artix linux:

`sudo pacman -S linux-zen`

#### The second way: compiling linux kernel from source with ashmem & binder

If you can do this, you know how to set it up.

### Step 2: Enabling binder module 
When enabling the anbox support option, the binder and ashmem modules are built-in. You don't have to load them.You just need to boot kernel with following parameters: 
`binder.devices=binder,hwbinder,vndbinder,anbox-binder,anbox-hwbinder,anbox-vndbinder`

### Step 3: Mounting binderfs

**Note: You need root access for this. for normal users use `sudo` before commands**

Creating binderfs directory:`mkdir /dev/binderfs`

Mounting binder for this session:`mount -t binder binder /dev/binderfs`

setting binderfs on `/dev/fstab/` for always mounting binderfs by system: 
````
binder                         /dev/binderfs binder   nofail  0      0
````
### Step 4: Installing anbox
Installing anbox-nosystemd-git:
**Note: for `pacman` command, you need root access. for normal users use `sudo` before `pacman`**
````
cd ~
git clone https://github.com/Luciogi/artix_pkg.git
cd artix_pkg/anbox-systemd-git
pacman -S --needed base-devel
makepkg -si
````
Installing anbox-dinit(This project):
````
cd ~
git clone https://gitlab.com/mobin2008/anbox-dinit.git
cd anbox-dinit
makepkg -si
````
### Step 5: Enabling services
Enable `anbox-container-manager`:
**Note: for `dinitctl` command, you need root access. for normal users use `sudo` before `pacman`**
````
dinitctl start anbox-container-manager # For loading in this session
dinitctl enable anbox-container-manager # For loading in startup
````
Enable `anbox-session-manager`:
**Note: No longer need this**
````
dinitctl start anbox-session-manager # For loading in this session
dinitctl enable anbox-session-manager # For loading in startup
````
### Step 6: Using anbox xD
Done!

## License
Copyright (C) 2022 Mobin2008
This project lisenced with LGPLv3-or-later

## Screenshots

