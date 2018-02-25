# Installing an Ubuntu Image
Ubuntu for WSL is available in the Windows Store. [Instructions
for installing that release](0250-Ubuntu.md) are provided elsewhere
and you should use it unless you have specific reasons for needing
another release.

Here are the steps required to install a different Ubuntu release
image. You may wish to review the information in [Other Distros](
0299-Other-Distros.md) before proceeding. The steps assume you are
installing Ubuntu 17.10 (Artful Aardvark), so make the appropriate
changes for a different release.

There are three high level steps to install the image:

* Set up a directory to contain the distro.
* Install the distro image
* Configure the default user.

Each of these topics is discussed below.


You can use either a Docker image or a more general cloud image for
Ubuntu 17.10. It is also possible to use an image from an ISO file.
The installation and setup are not the same, so they
are placed in separate sections below.

## Directory Setup 

1. Create a directory for your distro. The best places for this
directory are probably at the root of your system drive or in
your Documents directory. Name the directory *Artful*.

1. Copy Launcher.exe to that directory. Rename the program *Artful.exe*.

1. Download an image to install and place it in the same
directory as your Launcher program. The best choices are cloud
images, such as the official Docker image or a more general
cloud image.

## Setup Image For WSL

You can use either a Docker image or a more general cloud image for
Ubuntu 17.10. It is also possible to use an image from an ISO file.
The installation and setup are not the same, so they
are placed in separate sections below.

### Setup Docker Image

#### Known Limitations
1. In the Docker image, the locale is set to *en_US.UTF-8*, but this
locale has not been loaded. It is possible to download the appropriate
language pack, but WSL does not support the system calls required to
register and switch to another locale. Instead, the locale falls back
to *C.utf-8*. There is probably no great problem with this; you get
a lot of messages stating that locale settings cannot be set, and
messages are not converted to your preferred language.

#### Image Setup
1. Artful Docker images are available at 
https://partner-images.canonical.com/core/artful/current/.
Select the image that ends in 
*-amd64.tar.gz* and download it to the Artful directory you created above.

1. Rename the file you just downloaded to *rootfs.tar.gz*.

1. Execute Artful.exe from within cmd.exe or Powershell.exe. This
installs the distro and registers it with WSL.

1. Execute Artful.exe again to start bash within the distro.
At this point, you have a distro that contains root as the only
user, and root has no password. To bring it up to the state you
would have for a distro installed from the Windows Store, you
need to perform the following:
    * Install the latest updates.
    * Add a root password.
    * Add a normal user.
    * Add a user password.
    * Give user sudo privileges

Each of these steps is covered in the subsections below.

#### Install Updates and Setup Root and User
1. At the bash prompt, execute the following commands:

```
apt update
apt upgrade
passwd root
useradd -s /bin/bash -m <user>
passwd <user>
```

#### Give User sudo Privileges
1. At the bash prompt, execute the following commands:

```
adduser <user> sudo
apt install sudo
```
2. Test the sudo setup by executing sudo. There should
be no errors reported when you execute the following:

```
su <user>
sudo man chmod
```

### Setup General Cloud Image

#### Known Limitations
1. The locale is set to C.utf-8. It is possible to download other language
packs, but WSL does not support the system calls required to register and
switch to another locale.

#### Image Setup
The only
tarball image that Ubuntu creates is for Amazon EC2. It is possible
to install from one of these tarballs, but unfortunately, an error
is reported when you ayttempt to launch it. You can, however,
install from the squashfs image.

For this setup, you will need a computer than runs Ubuntu; 
unfortunately, WSL does not have enough functionality to
complete the steps to prepare the image for installation.


1. Other than the Docker images, Ubuntu cloud images are located at
https://cloud-images.ubuntu.com/releases/artful/release/. 

    Download
the server file that ends in *-amd64.squashfs*. [Follow the 
procedure](0300-Convert-squashfs-File-to-tar.gz.md) to convert
the *.squashfs* file to *rootfs.tar.gz*.
1. If necessary, move the *rootfs.tar.gz* file to the *Artful*
directory.
1. Execute *Artful.exe* from within cmd.exe or Powershell.exe. This
installs the distro and registers it with WSL.

1. Execute *Artful.exe* again to start bash within the distro.
At this point, you have a distro that contains root as the only
user, and root has no password. To bring it up to the state you
would have for a distro installed from the Windows Store, you
need to perform the following:
    * Install the latest updates.
    * Add a root password.
    * Add a normal user.
    * Add a user password.
    * Give user sudo privileges

Each of these steps is covered in the subsections below.

#### Install Updates and Setup Root and User
1. At the bash prompt, executre the following commands:

```
apt update
apt upgrade
passwd root
useradd -s /bin/bash -m <user>
passwd <user>
```

#### Give User sudo Privileges
1. At the bash prompt, execute the following commands:

```
chown root /usr/bin/sudo
chmod u+s /usr/bin/sudo
chown root /usr/lib/sudo/sudoers.so
chmod 755 /usr/lib/sudo/sudoers.so
chown root /etc/sudoers
chmod 755 /etc/sudoers
chown -R root /etc/sudoers.d
chmod -R 755 /etc/sudoers.d
adduser <user> sudo
```

2. Test the sudo setup by executing sudo. There should
be no errors reported when you execute the following:

```
su <user>
sudo man chmod
```

### Setup ISO Image

#### Known Limitations
1. The locale is set to *en_US.UTF-8*, but this
locale has not been loaded. It is possible to download the appropriate
language pack, but WSL does not support the system calls required to
register and switch to another locale. Instead, the locale falls back
to *C.utf-8*. There is probably no great problem with this; you get
a lot of messages stating that locale settings cannot be set, and
messages are not converted to your preferred language.

1. Subdirectories of the rootfs contain directories with names like aux
and drm which are reserved for use by Windows. When you attempt to 
uninstall this distro using *Artful clean*, the process will fail. You
will need to follow MichaelLennox's answer to [A folder that refused
to be deleted, invalid file handle](
https://answers.microsoft.com/en-us/windows/forum/windows_8-files/a-folder-that-refused-to-be-deleted-invalid-file/a8506e19-d623-4af0-ab19-0fd17a672a3a).
I had to run the command at various levels to finally remove the 
*rootfs* directory. Once that is done, your system is cleaned up
and you can install a new image here.

#### Image Setup

1. You can obtain a .squashfs file from an iso file. To do that,
download the amd64 iso file for the flavor of Ubuntu you want. Extract
the file *filesystem.squashfs* located in the *casper* directory in the ISO.

1. Follow the procedure outlined in the Setup General Cloud Image
section replacing the cloud image *.squashfs* file with 
*filesystem.squashfs* from the iso file.

## Configure Default User
1. Register the newly created user as the default user for this
distro. To do this, exit back to the cmd or Powershell prompt
and execute:

```
Artful config --default-uid <user>
```

Now when you start *Artful* the next time, \<user\> is logged in
rather than root.
