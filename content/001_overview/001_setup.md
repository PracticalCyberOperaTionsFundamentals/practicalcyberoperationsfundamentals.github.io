---
title: Setup
nav_order: 1
parent: CTF Overview
permalink: /overview/setup/
---

# Setting Up Your Computer

## A Baseline

You can set up your (see note) computer any way you'd like. However, we have
some observations about CTF:

1. While most CTF files are benign, downloading unknown files off the internet
   and running/opening them is not very safe. Some CTF files are even
   *explicitly* listed as malware.

2. Many binary exploitation and reverse engineering challenges are centered
   around `x86` and `x86-64` architectures.

3. Unless a challenge explicitly revolves around Windows, most challenges
   expect a *nix system. This includes Linux, MacOS, and BSD. More particularly,
   many expect an Ubuntu Linux system.

Based on these observations, we recommend using an `x86-64` CPU and a **virtual
machine** running the latest version of Ubuntu. Alternatively, you may want to
install Kali Linux instead of Ubuntu.

If you have a computer with an `arm` CPU, such as an M-series Apple CPU, you
will encounter difficulty with problems surrounding `x86-64`. You will also be
unable to install an `x86-64` virtual machine. If you have the ability to use a
different computer, we highly recommend it. You could also rent a virtual
private server (VPS).

If you decide use an `arm` CPU, you may be able to follow along, but software
compatibility will be limited. 

In a similar vein, if you decide you want to use Windows (or a Windows VM)
instead, software compatability will be limited. However, some problems are
more easily solved on Windows.

To set up a virtual machine, you will need to install a **hypervisor** - a
virtual machine manager - such as Oracle VirtualBox or virt-manager. Once again,
you may be limited by your computer. Some computers do not allow hypervisors,
and some that do may not have the processing power to run a virtual machine. If
this is the case, we recommend using a dedicated separate machine.

We trust that you can install a virtual machine. After all, CTF is about
problem solving!

## Further setup: Docker

Docker is a **containerization** tool which allows a user to create very
small containers with separated filesystems and processes. These are similar
to virtual machines but are more lightweight.

Docker is heavily used by CTF challenge authors, as it allows them to develop
CTF challenges on their own machine, then deploy their challenges to CTF
servers without worrying about compatibility issues.

For CTF challenges in this book that use Docker, we provide `Dockerfile` and
`docker-compose.yml` files for ease of deployment, with customizable parameters
including flags.

In real CTF competitions, some challenges provide the `Dockerfile` (and some
even provide a `docker-compose.yml`) so competitors can test a solution locally
before trying on the CTF server. We aim to imitate this functionality.

Once again, we trust that you can install Docker.

To test whether you have installed it correctly, we encourage you to download
[`hello.zip`](/content/assets/docker/) (within your VM) and run the included
`docker-compose.yml` to have a fun message! You should be able to connect with
`nc`:

```
nc 127.0.0.1 50001
```

You can modify the message using the `FLAG` variable in the `Dockerfile`.
For other problems, these environment variables may be useful for educators
using secret flags for homework or students looking to tinker with settings!


## Notes

- Make sure you are doing this on **your** computer. Installing and running
  unapproved software on work, borrowed, or rented computers (excluding VPSs)
  is a bad idea.

- Kali Linux is a version of Linux with pre-installed versions of many
  cybersecurity tools. This may be appealing to some users, but everything that
  is pre-installed on Kali can be installed on other distributions.

- On this page, we recommend the base tools necessary for every CTF challenge
  category. Category-specific tools can be found within their respective pages.
