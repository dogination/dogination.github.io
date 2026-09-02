+++
title = "Setting up a server"
date = "2024-03-03"
+++

![Image alt](/server.jpeg)

## About
This is just a simple guide on how I setup basic software on a server.

### Prerequisites

I would pick [debian](https://www.debian.org/) as it is most supported.

Download and flash correct architecture iso to flash drive or copy to [Ventoy](https://www.ventoy.net/en/index.html) drive or as I do [netboot.xyz](https://netboot.xyz/) on ventoy, easily booting into diffrent up to date operating systems using iPXE (internet required).

Plug in flash drive and you would probably need to connect display, keyboard and/or mouse (depeding cli or gui install) to the server.

Turn on server and boot into flash drive into [debian](https://www.debian.org/) iso

### OS Installation

#### Pick Graphic install or Install (cli)

#### Pick your Language
Select your location (Country where you live for time zone)

#### Configuring the keyboard
Keymap to use (keyboard layout)

#### Configuring the network
Hostname for system (identify the system to network)
Domain name (I keep blank)

#### Set up users and passwords
Root password (I keep blank to disable it and use user "sudo" command)
Full name for the new user (I keep blank)
Username for your account (I enter user)
Choose a password for the new user (enter strong password)

#### Configure the clock

#### Partition disks
Partitioning method (I pick "guided - use entire disk" but pick for your use case)
Select disk to partition (pick disk to install debian)
Partition scheme (I pick All files in one partition)
Click partitioning and write changes to disk and yes to Write the changes to disks

#### Configuring the packages manager
Debian archive mirror country: (pick the country where the server in for the fastest download speed for package manager)
Debian archive mirror: I would pick the recommended "deb.debian.org"
HTTP proxy information (blank for none): (I just keep blank)


#### Configuring popularity-contest
I pick no

#### Software selection
Choose software to install: (I only pick "standard system utilities" and "SSH server")

#### Finish the Installation
I press Continue to reboot into newly installed os

#### Can remove flash drive when server's off

### Software Installation

Now your finished installing you want to get the ip address of the server you can do this by through your router dashboard or by

Login using the set username (I picked user so enter user)
Password (enter your set password)
Then entering the command below which will show your ip under your network adapter under inet

```bash
$ ip a
```

You can logout now by entering

```bash
$ exit
```

Now you got your server ip you can now disconnect your monitor, keyboard and mouse from the server as we will use ssh to manage our server.

Now open a terminal on another computer that is on the same network as your server and enter

```bash
$ ssh user@[server-ip]
```

click yes to fingerprint
and enter the password you set
now your in

I would update the system

```bash
$ sudo apt update
$ sudo apt upgrade
$ sudo apt full-upgrade
$ sudo apt autoremove
$ sudo reboot
```
Log back in
Then install basic tools to help me manage the server

```bash
$ sudo apt install htop ncdu ranger neovim
```

Install docker

```bash
$ curl -sSL https://get.docker.com | sh
$ sudo usermod -aG docker $USER
$ logout
```
Log back in
To test if docker is running correctly

```bash
$ docker run hello-world
```

### [Automatic Updates](https://linuxiac.com/how-to-set-up-automatic-updates-on-debian/)
```bash
$ sudo apt install unattended-upgrades
$ sudo nvim /etc/apt/apt.conf.d/50unattended-upgrades
```

#### Uncomment these line by removing // from the start of the lines
```
"origin=Debian,codename=${distro_codename}-updates";
"origin=Debian,codename=${distro_codename}-proposed-updates";
"origin=Debian,codename=${distro_codename},label=Debian";
"origin=Debian,codename=${distro_codename},label=Debian-Security";
"origin=Debian,codename=${distro_codename}-security,label=Debian-Security";
```

#### Autoremove unused depdencies

Uncomment and change from "false" to "true"

```
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```

Save and exit

## Enabling automatic update
```bash
$ sudo dpkg-reconfigure --priority=low unattended-upgrades
```

Enter on Yes

## Check if unattended-upgrades is running
```bash
$ sudo systemctl status unattended-upgrades.service
```

Beside Active: active (running) should show
