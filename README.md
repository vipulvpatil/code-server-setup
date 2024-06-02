# code-server-setup
Setup script for quickly getting code server up and running on Ubuntu

## Disclaimer

**Warning: Use at Your Own Risk**

The scripts and code provided in this repository are for educational and informational purposes only. They are provided "as is" without warranty of any kind, either express or implied, including but not limited to the implied warranties of merchantability and fitness for a particular purpose. The use of the scripts is at your own risk. The author is not responsible for any damage, data loss, or other issues that may arise from using the scripts.

Please review and understand the code before executing it on your system.

# Assumptions
1. Scripts are intended for (and tested on) Ubuntu 22.04. Other systems might cause unexpected behavior
2. Scripts assume a PKI-authentication based SSH session can be established with the server. [How to setup PKI based SSH access](https://snapshooter.com/blog/using-ssh-keys-for-digitalocean)

# Prerequisites
1. Assumes [sudo](https://linuxize.com/post/sudo-command-in-linux/)
2. Assumes [wget](https://www.tecmint.com/install-wget-in-linux/)
3. Assumes [rsync](https://operavps.com/docs/install-rsync-command-in-linux/)
4. Assumes [systemd](https://ioflood.com/blog/install-systemd-command-linux/)

# How to use
1. Download [source scripts](https://github.com/vipulvpatil/code-server-setup/releases/latest) and unpack to Server.
2. Change directory `cd code-server-setup`.
3. Ensure [prerequisites](#prerequisites) are installed.
4. Run `./install -u [new-username] -p [access-password] -d [domain] -e [proxy-pattern]` and follow commands.

*Each [argument](#arguments) is explained below. For further details, check [references](#references) at the bottom*

## Arguments
1. `new-username` It is not recommended to use the root user when accessing server, so the script requires a new username. If the given username does not exist in the system, a new user will be created. Since the newly created user will be given sudo rights, a password should be provided when asked.
2. `access-password` This password will guard your code server access.

**Note**
The `access-password` is different from the user password created when creating the new user.

3. `domain` This is you server domain. This should point to the server where you intend to host Code Server.

4. `proxy-pattern` *Optional*. This is a pattern like {{port}}.domain.tld for helping with proxying open ports. Read more [here](https://coder.com/docs/code-server/guide#using-a-subdomain)

# Setup forwarded ports in nginx with SSL.
You can use `./forwarder_setup -d [domain]`

## Arguments
1. `domain` The domain to add to nginx (and SSL) for forwarding.

## Description
Code Server allows forwarding of ports for various services. This enables testing of services (escpecially Web frontends) from a local system. Assume you are running code server at `code.vipul.dev`. You could set it up with proxy forwarding as follows.

```
./install -u vipul -p pass -d code.vipul.dev -e {{port}}.vipul.dev
```

Now if you start a service at 9000, Code Server will auto forward the port to 9000.vipul.dev. To enable public access, you can run the forwarder setup as follows

```
./forwarder_setup -d 9000.vipul.dev
```

This will make the necessary changes in nginx configuration and also allow you to update your SSL certs using LetsEncrypt.

# Packaging instructions (for development purposes only)

`tar --exclude-vcs --exclude-from=.gitignore -czvf ./build/code-server-setup-1.0.2.tar.gz *`

# References.
This guide is put together using the following references.
* https://www.digitalocean.com/community/tutorials/how-to-set-up-the-code-server-cloud-ide-platform-on-ubuntu-22-04
* https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu
* https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04
