# Chapter 1: Introduction
This document discusses Windows Subsystem for Linux (WSL). Specifically, 
it covers the following topics:

- What WSL is and how it differs from a GNU/Linux installation
- What WSL is meant to be
- What other functionality WSL supports and doesn't support
- Why this document is written
- How to install WSL
- How to use WSL and what to do if something does not work
- Running GUI applications and desktops
- Printing and Scanning in WSL

That is a lot, but since this is an introduction, let's begin with what
WSL is and what it is meant for.

## What is Windows Subsystem for Linux
According to Microsoft[1], 
> The Windows Subsystem for Linux lets developers run Linux environments 
-- including most command-line tools, utilities, and applications -- 
directly on Windows, unmodified, without the overhead of a virtual 
machine.

and according to Wikipedia[2],
> Windows Subsystem for Linux (WSL) is a compatibility layer for 
running Linux binary executables (in ELF format) natively on Windows 
10. WSL provides a Linux-compatible kernel interface developed by 
Microsoft (containing no Linux kernel code), which can then run a 
Linux userland on top of it, such as that of Ubuntu, SUSE or Fedora.

So, WSL is a compatibility layer that allows users to run Linux
applications on computers running Windows 10. It does not run in a
virtual machine and it does not run in a container. You can think of it 
as WINE but the other way around. 
## What Can WSL be Used For
According to Frequently Asked Questions in the Microsoft documentation
for WSL[3], Windows Subsystem for Linux is intended primarily as a tool 
for developers, especially web
developers and those who work on or with open source projects.

So what can you do with WSL?
- Run GNU/Linux command line tools such as bash, awk, sed, grep, and so
forth[1].
- make and various compilers[1].
- Various services such as ssh, MySQL, Apache, and lighttpd[1].
- Run Linux applications from the Windows command prompt and Powershell[4].
- Run Windows applications from the WSL bash shell[4].
- Run multiple instances of a Linux distro (e.g. Ubuntu).
- Run multiple distros at the same time (e.g. Ubuntu and OpenSUSE Leap)[5].

That's what Microsoft says WSL is for, but there are other things that
WSL can be used for with varying success. If you have a problem with
any of the following, Microsoft will not support you; you will have to
figure them out for yourself, or check with other people on sites such
as reddit's /r/bashonubuntuonwindows. A list of support sites will be
provided in the Troubleshooting section of the Using WSL chapter.
- Run *some* GUI applications.
- Run a GUI desktop.
- Print and scan documents.

This guide will cover each of these topics, sometimes in detail, and
sometines simply by providing a web link to the required information.


## Why Write This Document
WSL is a rapidly evolving system. Much of information available on the
Internet is outdated and therefore incorrect. And some or much of the 
currently correct information will become outdated as WSL evolves.

A few people who subscribe to the  /r/bashonubuntuonwindows subreddit 
have produced what they hoped would be collaborative documents, 
but there has been little or no collaboration. For example, Anders
Aberg has written a very nice document[6] that is intended to help 
beginners to bash get started. However, as I write this, it references
Windows 10 Anniversary edition and refers to Windows Subsystem for
Linux (beta). There have been a number of new Windows 10 releases since
Anniversary edition, and with the release of Windows 10 Fall Creators
Update in October 2017, WSL is no longer in beta.

It is hoped that this document will evolve with each Windows 10 release
and that additional information will be added as it is created and
mentioned in the various information sources.


## References
[1] [About the Windows Subsystem for Linux](
https://docs.microsoft.com/en-us/windows/wsl/about)

[2] [Wikipedia entry for Windows Subsystem for Linux](
https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux)

[3] See the answer to the question *Who is this for?* in
[Frequently Asked Questions](
https://docs.microsoft.com/en-gb/windows/wsl/faq)

[4] [WSL Interoperability with Windows](
https://docs.microsoft.com/en-us/windows/wsl/interop)

[5] [Manage multiple Linux Distributions in WSL](
https://docs.microsoft.com/en-us/windows/wsl/wsl-config)

[6] [Bash on Ubuntu on Windows](
https://github.com/abergs/ubuntuonwindows) - a beginners guide to bash