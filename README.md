# code-server-setup
Setup script for quickly getting code server up and running on Ubuntu

# Assumptions
1. Scripts are intended for (and tested on) Ubuntu 22.04. Other systems might cause unexpected behavior
2. Scripts assume a PKI-authentication based SSH session can be established with the server. [How to setup PKI based SSH access](https://snapshooter.com/blog/using-ssh-keys-for-digitalocean)
3. Assumes [sudo](https://linuxize.com/post/sudo-command-in-linux/) is installed and working
4. Assumes [wget](https://www.tecmint.com/install-wget-in-linux/) is installed and working
5. Assumes [rsync](https://operavps.com/docs/install-rsync-command-in-linux/) is installed and working
6. Assumes [systemd](https://ioflood.com/blog/install-systemd-command-linux/) is installed and working

# How to use
1. Run `sudo apt update` to get your system up to date
2. Download script
3. Run `./install -u [new-username] -p [access-password] -d [domain]`
**Note** The `access-password` is the password for connecting to Code Server. This is different from the user password that is setup during user creation.

# WIP
git clone repo
chmod +x ./uninstall
chmod +x ./install
chmod +x ./global
