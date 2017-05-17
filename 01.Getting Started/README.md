# Introduction
In this project I will be guiding you through the process of building a Full-stack JavaScript web application. We will be building a social media website. Throughout this project I will explain key principles in the various technologies we will be using leaving nothing in the development process unexplained.

# Assumed Knowledge
* Intermediate JavaScript
* Basic HTML, CSS

# Checklist
* Linux Server (We're using Ubuntu 16 LTS)
* Get a hello world express.js app running

# Linux Server
To get started I'm going to be using an Ubuntu Virtual Machine. I'm running Windows 10 and will be using putty to access the command line of the server. I'll also be using the code editor Atom. I use Atom as I like the syntax highlighting and the plugins available.

## Setting up your Linux Server
Options:
A. You are already running a machine with a unix-like console and you are comfortable troubleshooting your OS.
B. You are running Windows and you have good enough hardware to run a virtual machine.
C. You are running Windows and you need to use a remote server.

### A. I'm all Set
Fantastic. Move on

### B. Using Windows and a Local VM
TODO: Make Guide More Detailed
Install [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads) if you haven't already.
Download [Ubuntu 16.04 LTS Server](https://www.ubuntu.com/download/server) (Use another distro if you are comfortable troubleshooting it).
Set up new Linux Machine on VirtualBox, insert Virtual Disk and start box.
Install Ubuntu Server Following installation prompt.
Setup SSH for SFTP to put code on server over secure connection.
`sudo apt-get install openssh-server`

### C. Using Windows and Remote VM
TODO: Make Guide More Detailed
Setting Up a remote server. Use AWS for a free server with minimum specifications or use [digital ocean and get $10 free credit with my referral link](https://m.do.co/c/fbefaeb56055)
If using Digital Ocean, create an Ubuntu 16.04 Droplet and follow the [initial Ubuntu Setup Guide](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04). When you have finished you will have SSH access and Putty.

# Checklist
* ~~Linux Server (We're using Ubuntu 16 LTS)~~
* Get a hello world express.js app running

# Install Node
For this project we will be using Node version 6.10.3. This is the latest stable release at time of writing. You may intall node however you wish but I prefer to use NVM (Node.js Version manager). 
[How To Install Node.js on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04#how-to-install-using-nvm)

# Install express
When you have node installed you can start using npm (node package manager). 
`npm install -g express`
If you get errors try to `sudo` it.
`sudo npm install -g express`
The `-g` installs it as a global module.

# Install nodemon
Nodemon is very useful as a development tool. Running a node application with nodemon will save you time having to rerun the server after every change as it listens for changes. As a bonus it will only rerun if it has to so any changes that don't require restarting the server won't.
`npm install -g nodemon`
Again, use `sudo` if needed.

# What Next?
Move on to HELLO_WORLD.MD
