# Other Distros
There are a number of blog posts on the Internet
that describe how to install Linux distros
other than those available in Windows Store.
Unfortunately, almost all of them were written
for versions of Windows that included WSL as
a beta Windows feature and execute at least one
program that has been marked as deprecated. 

There are a few procedures that work for WSL in
Windows 10 FCU and later. At least one of them uses
a WSL distro registration program that does not have an
uninstaller. The only way to get rid of it is to generate
a Windows restore point before installing the program
and to restore your system back after trying it out. Of course
that removes any changes you made after creating the restore
point so it is rather useless if you don't want to be stuck
with a program that you cannot uninstall.

The cleanest procedure that I have found uses
wsldl[1] by yuk7. That is the procedure
that I describe on this page and in the following
pages that describe how to install non-Windows Store distros.

## Installing Non-Window Store Distros
### Download wsldl

The first step is to download wsldl. wsldl takes
a distro image file called rootsfs.tar.gz, installs the distro, and registers
it with WSL. It also performs a number of other WSL related tasks. A full
description of its capabilities is included in the [project's README file
on GitHub](https://github.com/yuk7/wsldl).

In your Windows
web browser, go to the 
[release page](https://github.com/yuk7/wsldl/releases)
and select Launcher.exe. This will start the download. I suggest saving
the file in a location such as your Documents directory as you will
need it for each distro that you install.

### Installing a Distro
More specific instructions are provided in pages for
specific distros. This section provides a general procedure that
is followed for each distro.

1. Create a directory to contain your distro. The Windows Store distros are 
installed at C:\Users\<*your Windows user name*>\AppData\Local\Packages.
You probably do not want to store your distro on AppData because it is
harder to access, so consider a location like directly on the root of
your system drive (typically C:), or within your Documents directory.
For Windows 10 Fall Creators Update, you must place the distro on your
Windows system drive. This requirement will be dropped in future Windows 10
updates.

    Name your directory after the distro that you are creating. For example,
for Ubuntu 17.10, nicknamed Artful Aardvark, name the directory *Artful*;
for Fedora, where nicknames are not used, name the directory after the
release number. For example: *Fedora-27*. That way, you will be able
to have multiple releases of a distro if you want.

1. Copy Launcher.exe to your new directory and rename it after the distro.
For example, for Ubuntu 17.10, rename it to Artful.exe; for Fedora-27,
rename it to Fedora or something similar. That way, if you have multiple
distros, you are more likely to remember which you are using at any 
particular time.

1. Download a distro to install and place it in the same directory as
you placed your renamed Launcher.exe file.
The easiest distro files to use are cloud base images,
such as Docker images. Locations for various cloud images are listed
in the pages that discuss specific distros. If available, download the 
*.tar.gz file. If not,
download the *tar.xz file or the *.squashfs file. In these latter cases,
the files must be converted to a *.tar.gz file before use. Instructions
for performing these conversions are provided in [Converting a .squashfs 
File to rootfs.tar.gz](0300-Convert-squashfs-File-to-tar.gz.md) and
[Converting a *.tar.xz File to rootfs.tar.gz](
0301-Convert-tar-xz-File-to-tar.gz.md).

      If necessary, rename the file to *rootfs.tar.gz*.

1. Start cmd.exe or Powershell program, cd to the distro
directory, and start the Launcher program. This will install your
distro and register it with WSL.

1. To use the new distro, execute the Launcher program again. Your
distro starts bash as the root user. In most cases, this root user
has no password, and there are no normal users. To create a distro
with similar characteristics to a distro installed from Windows
Store, you will need to do a number of things:

    * Update the packages.
    * Add a root password.
    * Add a new user.
    * Add a password for that user.
    * Add the user to the group of sudoers.
    * Perform any other tasks that are required to create a useable system.
    * Register the newly created user as the default user for that WSL distro.

    Because of differences between distros, how these tasks are performed varies.
These steps are listed
for each distro in a separate page.

## References
[1] [wsldl](https://github.com/yuk7/wsldl)
