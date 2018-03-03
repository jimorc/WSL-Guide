# Installing an ArchLinux Image

yuk7 has created a project on GitHub called 
[WSL-DistroLauncher](https://github.com/yuk7/WSL-DistroLauncher).
The general procedure for using
WSL-DistroLauncher was discussed earlier in
[Other Distros](0299-Other-Distros.md), so you may want
to review that. yuk7 has also
created a prebuilt compressed file called [Arch.zip](
https://github.com/yuk7/ArchWSL/releases)
 that contains both
WSL-DistroLaucher and the rootfs files for ArchLinux.
This file provides the easiest way to install and
register ArchLinux on Windows Subsystem for Linux. You can,
of course, also try an Arch cloud image. I will only discuss
using yuk7's prebuilt Arch.zip.

## Known Limitations
1. The locale is set to *en_US.UTF-8*. It is possible to download other
language packs, but WSL does not support the system calls required to
register and switch to another locale. There is probably no great 
problem with this; 
messages are not converted to your preferred language.

## Directory Setup 

1. Create a directory. The best places for this
directory are probably at the root of your system drive or in
your Documents directory. Name the directory \"Arch". For Windows
10 FCU, this directory must be located on your system drive (typically
C:).

1. Download [Arch.zip](
https://github.com/yuk7/ArchWSL/releases) and expand its contents
into the directory you just created. There will be two files:
  * Arch.exe, and
  * rootfs.tar.gz

## Installing via Arch.zip

### ArchLinux Image Setup
#### Image Setup
1. Installation is simple; just execute *Arch.exe* from a cmd.exe or
Powershell prompt.

1. Execute Arch.exe again to start bash within the distro.
At this point, you have a distro that contains root as the only
user, and root has no password. To bring it up to the state you
would have for a distro installed from the Windows Store, you
need to perform the following:
    * Generate signing keyring.
    * Install the latest updates.
    * Add a root password.
    * Add a normal user.
    * Add a user password.
    * Give user sudo privileges

Each of these steps is covered in the subsections below.

#### Generate Package Signing Keyring
1. At the bash prompt, execute the following commands:

```
pacman-key --init
pacman-key --populate archlinux
```
#### Install Updates and Setup Root and User
1. At the bash prompt, execute the following commands:
```
pacman -Syu
passwd root
useradd -s /bin/bash -m <user>
passwd <user>
```

#### Give User sudo Privileges
##### Install sudo

1. At the bash prompt, execute the following command:

```
packman -S sudo
```

##### Allow Members of sudo Group to Execute sudo
1. At the bash prompt, execute the following command to
edit the sudoers file:
```
visudo
```

2. Edit the file to enable the line:

```
%sudo ALL=(ALL) ALL
```
3. Save and close the file.

##### Add \<user> to sudo Group
1. Now create the sudo group and add <user> to that group:

```
groupadd sudo
gpasswd -a <user> sudo
```
2. Test the sudo setup by executing sudo. There should
be no errors reported when you execute the following:

```
su <user>
sudo man chmod
```
## Configure Default User
1. Register the newly created user as the default user for this
distro. To do this, exit back to the cmd or Powershell prompt
and execute:

```
Arch config --default-user <user>
```
2. Close the cmd or Prompt shell, and restart it.
Now when you start *Arch*, \<user> is logged in
rather than root.