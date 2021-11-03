# Axnet Docker Basics
### Up and Running with a Docker Container!

Basic container development using Docker on an Ubuntu Virtual Machine

### Pre-Reqs

1. You have a working knowledge of Virtual Machines and how to run them on a computer using a hypervisor.
2. You are familiar with Visual Studo CODE, not regular Visual Studio, but VS Code.  If you aren't familiar, become familiar.
3. You have a basic, trending intermediate, understanding of the command line - any command line.  

## This Guide's Approach

To learn about Docker this guide takes a different approach from the usual "Step 1: Download Docker Desktop..." method of learning about containers.  

You will not be using Docker Desktop for this guide.  Instead we are going to create a Virtual Machine and install Docker on it.  Then use Visual Studio Code to build a container and run it.

### Why?

Mostly because I feel you'll learn more.  Also, you'll end up using Docker in a very "datacenter-y" kinda way. A common architectue for running containers in the datacenter is to have the container platform running on VMs out in the datacenter.  These platforms are often clustered together and coordinated by a "orchestration" system like Kubernetes (a buzzword you might've heard). 

You'll also gain more experience with Linux this way.  Linux servers rule the datacenter.  So why not run one locally as a VM and gain Linux experience?  In this guide we'll be using Ubuntu.

## Things You Will Need

1. A Computer (any OS, any processor archtiecture - this guide works on Apple M1 machines too)
2. A Hypervisor for your computer to run Virtual Machines: VirtualBox, VMware Fusion (mac), VMware Workstion (Windows/Linux) are popular options.  Apple M1 users can pick from the M1 version of Parallels OR the currently free (!) version of VMware Fusion for Apple M1 - google search for their public beta that went live in Sept '21
3. A .iso installer for Ubuntu 20.04.  
    For x86 CPU machines go here: https://releases.ubuntu.com/20.04/
    For ARM CPU machines (Apple M1) go here: https://ubuntu.com/download/server/arm
    Make sure you download Ubuntu 20.04 SERVER - NOT DESKTOP!!!