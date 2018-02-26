# Installing an Alpine Image

yuk7 has created a project on GitHub called 
[WSL-DistroLauncher](https://github.com/yuk7/WSL-DistroLauncher).
The general procedure for using
WSL-DistroLauncher was discussed earlier in
[Other Distros](0299-Other-Distros.md), so you may want
to review that. yuk7 has also
created a prebuilt compressed file for Alpine Linux called [Alpine.zip](
https://github.com/yuk7/WSL-DistroLauncher/releases). Scroll down the page
until you find the first Alpine.zip file and select that for download.
This file contains both
WSL-DistroLaucher and the rootfs files for Alpine Linux.
This file provides the easiest way to install and
register Alpine Linux on Windows Subsystem for Linux. You can,
of course, also try an Alpine cloud image. I will only discuss
using yuk7's prebuilt Alpine.zip.

## Known Limitations
1. The locale is set to *en_US.UTF-8*. It is possible to download other
language packs, but WSL does not support the system calls required to
register and switch to another locale. There is probably no great 
problem with this; 
messages are not converted to your preferred language.

## Directory Setup 

1. Create a directory. The best places for this
directory are probably at the root of your system drive or in
your Documents directory. Name the directory \"Alpine". For Windows
10 FCU, this directory must be located on your system drive (typically
C:).

1. Go to the [WSL-DistroLauncher releases page](
https://github.com/yuk7/WSL-DistroLauncher/releases). Scroll down
until you find *Alpine.zip*. Select that file to download it. Expand
the archive into your *Alpine* directory. It contains
  * Alpine.exe;
  * licenses.txt;
  * rootfs.tar.gz; and,
  * version.txt.

## Installing via Alpine.zip

### Alpine Linux Image Setup
#### Image Setup
1. Installation is simple; just execute *Alpine.exe* from a cmd.exe or
Powershell prompt.

1. Execute Alpine.exe again to start bash within the distro.
At this point, you have a distro that contains root as the only
user, and root has no password. To bring it up to the state you
would have for a distro installed from the Windows Store, you
need to perform the following:
    * Install the latest updates.
    * Add a root password.
    * Add a normal user.
    * Add a user password.
    * Give user sudo privileges.

Each of these steps is covered in the subsections below.


#### Install Updates and Setup Root and User
1. At the bash prompt, execute the following commands:
```
apk update
apk upgrade
passwd root
adduser <user>
```

#### Give User sudo Privileges
##### Install sudo

1. At the bash prompt, execute the following command:

```
apk add sudo
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
4. At the bash prompt, execute the following commands:
```
addgroup sudo
adduser jim sudo
```

5. Test the sudo setup by executing sudo. There should
be no errors reported when you execute the following:

```
su <user>
sudo apk update
```
## Configure Default User
1. Register the newly created user as the default user for this
distro. To do this, exit back to the cmd or Powershell prompt
and execute:

```
Alpine config --default-user <user>
```
If you get the following output:

```
ERROR: Invalid Argument.
Failed to detect user.
```
then restart Alpine, and at the bash prompt, enter:
```
id -u <user>
```
This outputs a number (probably 1000).
Exit back to the cmd or Powershell prompt and execute:
```
Alpine config --default-uid 1000
```
Replace 1000 above with the output from the <code>id</code> command.

2. Close the cmd or Powershell, and restart it.
Now when you start *Alpine*, \<user> is logged in
rather than root.