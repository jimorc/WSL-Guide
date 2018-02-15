# Upgrading to a New Release
OpenSUSE Leap 42 and SLES-12 are the latest releases
of those distributions so there is nothing to upgrade
to. The Ubuntu app from the Windows Store is version
16.04 LTS. At the time I write this, version 17.10
is the latest Ubuntu release. Is it possible to upgrade to that release?

Before answering that question, it is important to ask yourself "Why
would I want to upgrade?" See [Should You Use Ubuntu LTS or Upgrade to the
Latest Release](
https://www.howtogeek.com/162768/should-you-use-ubuntu-lts-or-upgrade-to-the-latest-release/).
The releases mentioned are out of date, but the argument presented is still valid.

There is an Ubuntu Community Help Wiki page[1] that discusses
how to perform a release upgrade. From the command line, all we need
to do is:
```
sudo do-release-upgrade
```

and the result is:

    Checking for a new Ubuntu release
    No new release found.

Hmmm, that didn't work. The release upgrade is looking for the next LTS release (18.04),
which has not been released yet. There is a way to tell apt to attempt to upgrade to the
latest normal release. I found out how to do this by reading a tutorial on how to upgrade
from one LTS release to another LTS release[2]. So I made the appropriate change, attempted
to perform the release upgrade, and ... (drum roll please)

**IT DID NOT WORK!**

Well, the change resulted in apt attempting to upgrade to Ubuntu 17.10, but the upgrade
did not work. An error occurred while trying to unpack bash. The preinstallation script for bash
aborted because the functionality required by dmesg has not been implemented. It is possible to 
ignore this error and continue with the upgrade, but that leads to a number of other
problems once the upgrade is completed.

So, the answer to the question: "Is it possible to updrade to Ubuntu version 17.10 from
version 16.04?" is No.


## References
[1] [Trusty Upgrades](https://help.ubuntu.com/community/TrustyUpgrades)

[2] [How to Update a Ubuntu LTS release to the next LTS Version (release upgrade)](
https://www.howtoforge.com/tutorial/ubuntu-lts-update-dist-upgrade/)