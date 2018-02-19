# Converting a .squashfs File to rootfs.tar.gz
To convert a *.squashfs file to rootfs.tar.gz, you must
have a computer, virtual machine, or container running
Linux. Unfortunately, WSL does not support all of the
functionality required to do this conversion.

To perform the conversion, boot or otherwise start your
Linux system and copy the squashfs file to your system,
or cd to the directory containing the file if you have
access to the file system on your Windows machine.

Perform the following steps. These steps
work for Ubuntu and its derivatives. If you are using any
other Linux distro, you may need to make a few modifications
to the procedure, including downloading required packages.

```
sudo unsquashfs -d tmp <filename>.squashfs
cd tmp
sudo tar czf ../rootfs.tar.gz *
cd ..
sudo rm -r tmp
```

If necessary, copy *rootfs.tar.gz* to your Windows WSL distro
directory.

This procedure is a modified version of the procedure provided by
Biswa96[1]. The modifications were necessary to correct errors
that are produced by following Biswa96's procedure.
also, don't follow the procedure outlined by Biswa96 to create a Ubuntu 17.10
WSL distro; it replaces
your Ubuntu Windows Store distro with a different distro rather than
creating an separate distro.

## References
[1] [Install any GNU/Linux distribution having rootfs tarball
.tar.gz format](https://github.com/Microsoft/WSL/issues/2618)