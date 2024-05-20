# code-server-setup
Setup script for quickly getting code server up and running on Ubuntu

# Assumptions
1. Scripts are intended for (and tested on) Ubuntu 22.04. Other systems might cause unexpected behavior
2. Scripts assume a PKI-authentication based SSH session can be established with the server. [How to setup PKI based SSH access](https://snapshooter.com/blog/using-ssh-keys-for-digitalocean)

# Prerequisites
1. Assumes [sudo](https://linuxize.com/post/sudo-command-in-linux/)
2. Assumes [wget](https://www.tecmint.com/install-wget-in-linux/)
3. Assumes [rsync](https://operavps.com/docs/install-rsync-command-in-linux/)
4. Assumes [systemd](https://ioflood.com/blog/install-systemd-command-linux/)

# How to use
1. Download scripts to Server.
1. Ensure prerequisites are installed.
3. Run `./install -u [new-username] -p [access-password] -d [domain]` and follow commands.
*Each argument is explained below. For further details, check references at the bottom*

# Arguments
1. new-username. It is not recommended to use the root user when accessing server, so the script requires a new username. If the given username does not exist in the system, a new user will be created. Since the newly created user will be given sudo rights, a password should be provided when asked.
2. access-password. This password will guard your code server access.
**Note** The `access-password` is different from the user password created when creating the new user.
3. domain. This is you server domain. This should point to the server where you intend to host Code Server.

# References.
This guide is put together using the following references.
* https://www.digitalocean.com/community/tutorials/how-to-set-up-the-code-server-cloud-ide-platform-on-ubuntu-22-04
* https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu
* https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04
