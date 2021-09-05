#!/bin/bash

echo "you need sudo priveliges, make sure your a sudoer."
sleep 2
# make first folder tree 
echo "make first folder tree"
sleep 2
mkdir /mnt/VG_00
# make second tree
echo "make first folder second tree"
mkdir /mnt/VG_00/HOME
mkdir /mnt/VG_00/PUBLIC-LIBRARY
mkdir /mnt/VG_00/PRIVATE-LIBRARY/
# make second third tree
echo "make first folder third tree"

mkdir /mnt/VG_00/HOME/noa
mkdir /mnt/VG_00/HOME/peter
mkdir /mnt/VG_00/HOME/desiree
mkdir /mnt/VG_00/HOME/djuga
mkdir /mnt/VG_00/PRIVATE-LIBRARY/Prive.docs

# add user and change home path for user
# id noa     1002
# id peter   1000
# id djuga   1011
# id desiree 1003

echo "add user noa with id 1002"
sleep 1
useradd noa     -u 1002 -d /mnt/VG_00/HOME/noa

echo "add user peter with id 1000"
sleep 1
useradd peter   -u 1000 -d /mnt/VG_00/HOME/peter

echo "add user desiree with id 1003"
sleep 1
useradd desiree -u 1003 -d /mnt/VG_00/HOME/desiree

echo "add user djuga with id 1011"
sleep 1
useradd djuga   -u 1011 -d /mnt/VG_00/HOME/djuga

# change ownership

chown noa:noa         -R /mnt/VG_00/HOME/noa
chown peter:peter     -R /mnt/VG_00/HOME/peter
chown desiree:desiree -R /mnt/VG_00/HOME/desiree
chown djuga:djuga     -R /mnt/VG_00/HOME/djuga

# nfs entries in fstab
echo "adding entries in /etc/fstab"

echo "192.168.4.17:/mnt/VG_00/HOME/noa       /mnt/VG_00/HOME/noa             nfs defaults       0 0" >> /etc/fstab
echo "192.168.4.17:/mnt/VG_00/HOME/desiree   /mnt/VG_00/HOME/desiree         nfs defaults       0 0" >> /etc/fstab 
echo "192.168.4.17:/mnt/VG_00/PUBLIC-LIBRARY /mnt/VG_00/PUBLIC-LIBRARY       nfs defaults       0 0" >> /etc/fstab
echo "192.168.4.17:/mnt/VG_00/HOME/peter     /mnt/VG_00/HOME/peter           nfs defaults       0 0" >> /etc/fstab
echo "192.168.4.17:/mnt/VG_00/PRIVATE-LIBRARY/Prive.Docs/ /mnt/VG_00/PRIVATE-LIBRARY/Prive.Docs       nfs defaults      0 0" >> /etc/fstab

sleep 1

#192.168.4.17:/mnt/VG_00/HOME/noa       /mnt/VG_00/HOME/noa             nfs defaults       0 0
#192.168.4.17:/mnt/VG_00/HOME/desiree   /mnt/VG_00/HOME/desiree         nfs defaults       0 0
#192.168.4.17:/mnt/VG_00/PUBLIC-LIBRARY /mnt/VG_00/PUBLIC-LIBRARY       nfs defaults       0 0
#192.168.4.17:/mnt/VG_00/HOME/peter     /mnt/VG_00/HOME/peter           nfs defaults       0 0
#192.168.4.17:/mnt/VG_00/PRIVATE-LIBRARY/Prive.Docs/ /mnt/VG_00/PRIVATE-LIBRARY/Prive.Docs       nfs defaults      0 0

# install sudo 
echo "install  sudo "
sleep 1
apt update
apt install -y sudo

## add user to sudo list
usermod -aG sudo peter

# set time zone 
echo "install  sudo "
sleep 1
timedatectl set-timezone America/Curacao
## wine install
dpkg --add-architecture i386

apt update
apt -y install gnupg2 software-properties-common
wget -qO - https://dl.winehq.org/wine-builds/winehq.key | apt-key add -

apt-add-repository https://dl.winehq.org/wine-builds/debian/
apt update

wget -O- -q https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Debian_10/Release.key | sudo apt-key add -    
echo "deb http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Debian_10 ./" | sudo tee /etc/apt/sources.list.d/wine-obs.list

apt update
apt install -y --install-recommends winehq-stable

apt install -y winehq-staging

## end wine install
## minecraft windows . Wine needs mono
## https://dl.winehq.org/wine/wine-mono/6.2.0/
wget https://launcher.mojang.com/download/MinecraftInstaller.msi
wget https://launcher.mojang.com/download/Minecraft.exe
wget https://download.oracle.com/otn-pub/java/jdk/16.0.1+9/7147401fd7354114ac51ef3e1328291f/jdk-16.0.1_windows-x64_bin.exe
# install chromium

apt install -y chromium

## opengl
apt-get install -y libgl1-mesa-dev

## install -y vulkan 
apt install -y libvulkan1 mesa-vulkan-drivers vulkan-utils libvulkan-dev

## lshw
apt install -y lshw
## game mode
apt install -y gamemode
## git
apt install -y git

#######
## enable opengl on none supported hardware by using software render
## LIBGL_ALWAYS_SOFTWARE=1 *command*
#######

