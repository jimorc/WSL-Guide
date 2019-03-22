# Uninstalling a Distro
There are two ways described in this guide for installing a Linux distro
in WSL:
  * installing a distro from the Windows Store; and,
  * installing a non-Windows Store distro using wsldl.

The instructions for uninstalling a distro varies depending on which method
was used to install the distro. Each method for uninstalling a distro is
described below.

__Warning:__ All of your data (your home directory) is also deleted. You may
wish to save the contents of your home directory before uninstalling the
distro.
## Uninstall a Windows Store Distro
Distros that have been installed from Windows Store may be uninstalled like any
other app. That is, go to the Windows menu, right-click on the distro and
select *Uninstall*. Alternatively, you can uninstall by selecting 
*Settings->Apps & features*, then locate the distro in the list, select it,
and then click on the *Uninstall* button.

## Uninstall a Distro Installed with wsldl
The following instructions are for uninstalling Arch Linux. For
any other distro that was installed using wsldl,
make changes as appropriate.

1. Start cmd.exe or Powershell.
2. At the prompt, enter:

  * cd \<directory containing Arch Linux>
  * Arch clean

Your Arch Linux distro will be unregistered with WSL and uninstalled.