# Axnet Docker Basics
### Up and Running with a Docker Container!

Basic container development using Docker on an Ubuntu Virtual Machine

### Pre-Reqs

1. You have a working knowledge of Virtual Machines and how to run them on a computer using a hypervisor.
2. You are familiar with Visual Studo **Code**, not regular Visual Studio, but VS **Code**.  If you aren't familiar, become familiar.
3. You have a basic, trending intermediate, understanding of the command line - any command line.  

## This Guide's Approach

To learn about Docker this guide takes a different approach from the usual "Step 1: Download Docker Desktop..." method of learning about containers.  

You will not be using Docker Desktop for this guide.  Instead we are going to create a Virtual Machine and install Docker on it.  Then use Visual Studio Code to build a container and run it.

### Why?

Mostly because I feel you'll learn more.  Also, you'll end up using Docker in a very "datacenter-y" kinda way. A common architectue for running containers in the datacenter is to have the container platform running on VMs out in the datacenter.  These platforms are often clustered together and coordinated by a "orchestration" system like Kubernetes (a buzzword you might've heard). 

You'll also gain more experience with Linux this way.  Linux servers rule the datacenter.  So why not run one locally as a VM and gain Linux experience?  In this guide we'll be using Ubuntu.

## Things You Will Need

1. An internet connected Computer (any OS, any processor archtiecture - this guide works on Apple M1 machines too)

2. Visual Studio Code: https://code.visualstudio.com/download

3. A **Hypervisor** for your computer to run Virtual Machines: 

    VirtualBox, VMware Fusion (mac), VMware Workstion (Windows/Linux) are popular options.  
    
    Apple M1 users can pick from the M1 version of **Parallels** OR the currently free (!) version of **VMware Fusion** for Apple **M1** - google search for their public beta that went live in Sept '21

    While they cost money, using VMware sourced hypervisors has benefits.  VMware still rules corporate datacenters, and by using VMware tools, one is exposed to VMware vernacular and terminology regarding Virtual Machines, which prove be beneficial.  Their products also work really well.

    Virtualbox is of course free (and looks it)

4. A **.iso** installer for Ubuntu 20.04.  

    For x86 CPU machines go here: https://releases.ubuntu.com/20.04/

    For ARM CPU machines (Apple M1) go here: https://ubuntu.com/download/server/arm

    Make sure you download Ubuntu 20.04 SERVER - NOT DESKTOP!!!

    Don't leave it in your Downloads folder!  Put it somewhere for safe-keeping.  What I do is create a directory in my user directory called "ISO" or "isoinstallers" or something like that.  Every .iso OS installer I download goes into that directory.  Make sure you put them in a directory that is NOT being sync'd to a cloud service like OneDrive, iCloud, Dropbox, et al.  These installers are large and you don't want them taking up your cloud storage space.

## Part 1: Create an Ubuntu 20.04 Virtual Machine

As mentioned earlier, you should already be familiar with basic Virtual Machine concepts before attempting this guide.  This guide is not meant to provide detailed instructions on using VirtualBox or VMware Fusion or any other hypervisor.  Look for other guides on using these tools in my other repo's on GitHub.

### Steps

1. Create a virtual machine using your chosen hypervisor.  Again any hypervisor will do.
    
    *Virtualbox users*, create a **"Host Only Network"** and in the VM's settings connect **Adapter 2** to that network.  Do this *prior* to powering up the machine.

    By default, Virtualbox will only connect the VM to the "NAT" network, which isolates the VM from everything.  It is a *out to the internet* only connection.

    You want to be able to use SSH to access the VM.  DO NOT using the VM's console in the hypervisor.  That is the machine's virtual monitor and has limited use.  Treat the server VM like it is a server.  It could be 1000's of miles away in a datacenter.  Drop to a command line and ssh into it like you would have to for any other server.

2. Create an Ubuntu 20.04 virtual machine using your chosen hypervisor and your .iso installer.

3. After the machine is created, log into it using its hypervisor console. After logging in, run an "ip addr" to see what IP address got assigned.  Take note of this IP.

4. Use the IP address you found to log into the VM remotely using SSH like this (example - your username and IP will likely be different, perhaps very different): ssh someuser@192.168.1.10


## Part II: Use Visual Studio Code SSH Remoting

Visual Studio Code has a extension that can be added that allows it to connect to a remote machine vi SSH.  Very handy!  VS Code will be running on your computer, but doing everything out on the server.

Open Visual Studio Code, click on the "blocks" icon on the left side and search for "ssh".  Install the "Remote - SSH" extension from Microsoft.

In the lower left a >< looking icon will appear.  Click on it.  Click on "Connect to Host."   Enter the username@ipaddress of your Virtual Machine.  VS Code will attempt to connect.  If successful it will prompt for a password.  This is the same password you used to log into the machine on the command line.
