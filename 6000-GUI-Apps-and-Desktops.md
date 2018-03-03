# Chapter 4 Linux GUI Apps and Desktops
It is possible to run many GUI apps and at least one desktop
on Ubuntu on WSL. Few or no apps run on other distros, so this
chapter will concentrate on what runs on Ubuntu.

Before proceeding, you must understand that Microsoft's priority
for WSL is enhancing what runs at the command line; running Linux
GUI apps and desktops on Windows is not currently supported. What
works, works, but you are unlikely to get much help if something
doesn't work. You may wish to reference [Frequently Asked Questions](
https://docs.microsoft.com/en-us/windows/wsl/faq) for more information
about WSL and its intended uses.

## The Good News and the Bad News
### The Good News
* Some gtk+ based GUI apps will run on Ubuntu.
* A few Qt base GUI apps will run on Ubuntu.
* At least one desktop will run on Ubuntu.

### The Bad News
* **Some** gtk+ based GUI apps will run on Ubuntu.
* Most Qt based GUI apps error off on Ubuntu.
* A number of functions are not supported:
  * Sound.
  * Accessibility features.
* GUI apps do not run on openSUSE-42 or SLES-12.
* Support for running GUI apps and desktops on other
installed distros is unknown and unlikely to be greater
that support on Ubuntu.

## What You Will Need
To run Linux GUI apps and desktops on WSL, you need
the following:
* An XWindows server than runs on Windows 10.
* Apps and/or a desktop loaded from the distro's repository.

Each of these topics is discussed later in this chapter.