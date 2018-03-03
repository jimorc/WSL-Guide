# X Server for Windows 10

Linux GUI applications and desktops communicate with an
XWindows server to handle display and interaction. The
X server that is available in the various Linux distros will
not work on Windows 10; you need an X server for Windows 10.

## Installing an XWindows Server

There are three free, opensource XWindows servers that run
on Windows 10: *VcXsrv*, *XMing*, and *Cygwin/X*. All are compiles
of XOrg source code. *VcXsrv* is compiled using *Visual Studio*,
*XMing* is built with the tools in *mingw64*, and *Cygwin/X* is
built with the *Cygwin* tools. Both *VcXsrv* and *XMing* seem
to work well. Both support cut and paste between XWindows and
Windows apps in both directions. So use the one you want.

You can get *VcXsrv* [here](https://sourceforge.net/projects/vcxsrv/files/)
and *XMing* [here](https://sourceforge.net/projects/xming/files/).
Once either is installed, run *XLaunch*. The default settings are
OK, so just keep clicking the *Next* button. On the final screen,
click the *Save configuration* button. The default file name is good.
Then click the *Finish* button; this will start *VcXsrv* or *XMing*.

## Running Your XServer
From this point on, you can launch *VcXsrv* or *XMing* directly
unless you want to change the configuration.

*VcXsrv* and *XMing* run as servers and therefore do not display a
window, or place an icon in the Windows task bar. They do place an
icon in the system tray to allow you to interact with the server.

## Telling Your Linux Apps What Display to Use
To use an X server, you must tell your applications what display
is tied to your X server. You do that by using an environment
variable. Whenever you start a program, that program inherits the
exported  environment variables from its parent program. In our
case, you will be starting your GUI applications or desktop from
*bash*.

To set up the display environment variable, you have to run *bash*.
You can do this by starting your distro from the Windows start menu,
or by executing the appropriate command from within *cmd.exe* or
*Powershell*. This must be done for each Linux user on your system
that will be executing GUI applications.

At the bash prompt, enter:
```
echo export DISPLAY=:0 >> ~/.bashrc
```

This tells all GUI programs to use the X server for display 0.
This is the first X server that you started. Close bash and restart it
(close and start Ubuntu or other distro, or exit bash from the
command line prompt and start it again). The environment variable will
now be exported to every program that you start from the bash prompt.

## Using Your X Server
Before running any Linux GUI app or desktop, you must start your
X server. The X server is a Windows 10 program, not a Linux program,
so you can start it from the Windows menu. Therefore, you only need
to start the X server once, not every time you use a Linux distro on
WSL. If you will be running Linux GUI apps or a desktop very
frequently, you might consider adding your X server to the list of
programs that start when your start Windows.

Everything is now set up, so the next step is to install a Linux GUI
application or a Linux desktop. That is the topic of the next few
pages.

## References
1. The content of this page was copied, with a few modifications, from
[Running Linux GUI Apps on Windows 10](
https://jaipblog.wordpress.com/2018/01/21/running-linux-gui-apps-on-windows-10/).