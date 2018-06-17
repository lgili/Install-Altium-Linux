# Install-Altium-Linux
How to install Altium 16 on linux
# Step 1 - Installing WINE

1. Open a terminal session (I use XTerm). In Ubuntu click on the system search bar and type XT and you’ll find it.

2. Make sure 32-bit architecture is enabled in Linux:

sudo dpkg --add-architecture i386

3. Add the installation repository link for WINE:

sudo add-apt-repository ppa:wine/wine-builds

4. Update the available installation packages list with newly added repository:

sudo apt-get update

5. Install the development build of WINE:

sudo apt-get install --install-recommends winehq-devel

6. Check WINE installed version once installed (should tell you wine-1.9.12 or later):

wine --version

# Step 2: Install winetricks and setup a “WINEPREFIX” for CircuitMaker

7. Install winetricks:

sudo apt-get install winetricks

8. If you have not already done so, download CircuitMakerSetup.exe from the CircuitMaker web site. Saving to the user /Downloads directory default is fine.

9. Create the WINEPREFIX named Altium that establishes the “windows like” environment for Altium to be installed in:

WINEARCH=win32 WINEPREFIX=~/Altium winetricks vd=1366x768 -q gdiplus corefonts riched20 mdac28 msxml6 dotnet40

Replace "1366x768" by your own monitor resolution!

In Manjaro (Arch Linux) I also recommend the installation of "PlayOnLinux", "Q4Wine", "wine-staging", "winetricks" and "pacman -S --noconfirm $(pacman -Qq | grep lib32-*)" to ensure 32 bit compatibility (equivalent to "apt-get install ia32-libs").

# Step 3: Install CircuitMaker into the new WINEPREFIX

10. Install Altium using:

WINEPREFIX=~/Altium wine ~/Downloads/Altium_Designer/AltiumDesigner16Setup.exe

11. Launching Altium by the command-line can now be done with:

WINEPREFIX=~/Altium wine ~/Altium/drive_c/Program\ Files/Altium/AD16/DXP.EXE

# Step 4 (Optional): Create a Program Launcher


12. Install Wine Launcher Creator if you have not already done so. Download the debian package from here and double click on it to install: https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/wine-launcher-creator/wine-launcher-creator_1.0.8-1_all.deb

13. From the Ubuntu program launcher, run the Wine Launcher Creator and choose the DXP.EXE path within the WINE prefix you configured earlier. Specify only the path to DXP.EXE and the Wine Prefix Path - optionally modify the default working Toplevel app path and Name. Also, there’s a handy tool for choosing a desktop icon from within the Windows executable of Altium:
