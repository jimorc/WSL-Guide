# Converting a *.tar.xz File to rootfs.tar.gz

This conversion can be done on a WSL Linux distro;
you do not need a bootable Linux computer, virtual
machine, or container to perform the conversion.

To perform the conversion, start a WSL Linux distro
and follow these steps, changing *<tar.xf file to extract>*
to the name of the tar.xf file:

```
cd <directory containing the tar.xz file>
mkdir tmp
sudo tar --directory=tmp -xf <tar.xf file to extract>
cd tmp
sudo tar -czf ../rootfs.tar.gz *
cd ..
sudo rm -r tmp
```

You are now done with the WSL Linux distro, so you can close it.