---
title: CTF Overview      # ← label in the sidebar
nav_order: 1             # ← 1st section in the whole book
has_children: true       # ← tells JTD to expect child pages
permalink: /overview/    # (nice clean URL, optional)
---

# Capture the Flag (CTF) Overview

## What is it?

Capture the Flag is a gamified hacking competition format that allows users to
get hands on offensive cybersecurity experience. Participants can practice
real world techniques in many different areas of cybersecurity.

## How does it work?

CTF competitions are held around the world in a variety of sub-formats. The
most popular sub-format is "Jeopardy style," where challenges can be selected
by the competitor in any order they'd like. Sometimes challenges are added
mid-competition, either by the hosts or by solving a previous challenge.

Most competitions use a point system - the harder the challenge, the more
points it is worth! Many also use a decaying point system - the more people
solve a challenge, the less points it is worth.

You solve a challenge by finding a **flag**. Flags tend to look like this:

```
header{message}
```

Typically, the header is related to the name of the CTF. If the competition
was called Example CTF, the flag header might be `example{}`.

A full flag might look like this!

```
example{TH!5_!5_MY_53CR3T_M355AG3}
```

# How to use this book

Throughout this book, we list a number of fundamental concepts that should
guide your intuition when facing the problems and challenges throughout the
book. We also provide a number of real world jobs that implement the skills
shown throughout the chapter, and this can help guide your focus depending on
your career goals. That being said, we do recommend you read through each of
the chapters to gain some experience in each category, as you may end up
enjoying challenges and concepts you were not expecting.

This book provides CTF challenges to try to solve on your own. Sometimes, you
will need to set your own flag - the important part is the learning! Some
challenges will have solutions posted.

We provide `Dockerfile` and `docker-compose.yml` files for challenge setup. For
educators, these can also be a resource for your own infrastructure, since you
can set your own custom flags.


## Categories

CTF challenges are organized into categories. Some challenges use a mixture
of multiple categories but will still be placed into one or the other.

Every CTF competition can have any number of categories. Some competitions
focus on one or two categories.

### Web

In web problems, challenges often revolve around one or more websites.

### Forensics

In digital forensics ("forensics" or "DFIR") problems,
challenges take the form of files with locked, hidden, or lost-but-recoverable
information.

### Reverse Engineering

In reverse engineering ("reversing," "rev," or "RE") problems,
challenges involve some obfuscated code that when understood leads directly to
the flag. Obfuscation can take the form of compiled code, niche programming
languages, and other difficult-to-understand code systems.

### Binary Exploitation

In binary exploitation ("pwn") problems, challenges involve
exploiting vulnerabilities in compiled executable binaries to produce
unintended behavior, such as reading files or system access.

### Cryptography

In cryptography ("crypto") problems, challenges involve recovering messages
from faulty cryptographic algorithms or faulty implementations of secure algorithms.

### Other categories

While we do not have chapters on the following categories, we have seen
these appear in competitions:

- Miscellaneous ("Misc")
    - Challenges that do not fit into any other category. These challenges may
      not be cybersecurity at all.
- Open Source Intelligence ("OSINT")
    - Challenges revolving around publicly available information, such as
      social media, news, cryptocurrency exchanges, or public map data.
- Game Development
    - Challenges about game engines. Sometimes, this could be grouped into
      reverse engineering.
- Artificial Intelligence ("AI")
    - Challenges about large language models and other AI models.
- Blockchain ("Web3")
    - Challenges about blockchain technologies, including cryptocurrency.
      Unlike game development and embedded systems, this is almost never
      grouped into cryptography.
- Industrial Control Systems ("ICS")
    - Challenges focused on industrial control systems and operational
      technology, which has vastly different constraints than information
      technology.
- Embedded Systems
    - Challenges focused on microcontrollers and other embedded devices.
      Sometimes, this could be grouped into binary exploitation.

This is not an exhaustive list, and competitions may create new categories as
new cybersecurity fields emerge.

