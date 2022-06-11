# Windows removal tool
Welcome to Windows removal tool site! This is a concept of a program which is supposed to:
- delete Windows,
- install Linux,
- move all the user data while keping it intact,
- install all the previously present programs.
It is targeted to people who either want to start their Linux adventure with some training wheels or need their grandma's computer to run linux, because it is from 6 years ago and it would be a pitty to discard it yet, or want to prank school's IT guy. 

#### Disclaimer:
I am a Polish highschool student who can't code at all but daily drives Linux. This is my first project ever. I will make a ton of misakes, so please do not expect everything to be correct, let alone neat and easily understandable. 

## Inner workings:

### Part one: preperations in Windows

#### General plan:

The first part is preperations to overwrite Windows. I think it should look more or less like this:
1. ask for admin privileages,
2. download .iso or ask to point to a directory of a previously downloaded file,
3. create %systemdrive%\e (it doesn't have to be C:\),
4. ask about usernames and their passwords and which is the administrator,
5. make a list of all installed programes,
6. "translate" them to something linux understands (more about that in the details),
7. make configs of particular users (ease of access, wallpapers, colors, desktop icon layout (if it is entirely possible), etc.),
8. save all of it in %systemdrive%\e\sth.cfg,
9. ask for confirmation,
10. format the boot volume,
11. shrink the %systemdrive% by about 20GB,
12. create a bootable partition, onto which the installators image will be unpacked, the autoinstallation script copied and configs moved,
13. reboot.

#### Details and remarks:

generarily: .bat will do, maybe something else. There is no need for sophisticated GUI. The user will have to be happy with a frame made out of dashes and equasin signs. It would be nice to pack it into an installator.

point 2: .iso has to be stock, it doesn't need to have any modifications. The autoinstall script will be made by this program basing on a given template.

point 6: by "translating" i mean creating a scipt which will be all sudo apt install programs-name. Furthermore not everything availible on Windows will be availible on Linux. In this situation it will be needed to go to %systemdrive%\Program Files or Program Files (x86)\whatever-it-is-supposed-to-be, copy all the files, do all we can and prey that WINE or Proton will run it. As a last resort a folder with the program and all the data can be brutally moved.

point 8: It will be necesarry to split it into multiple scripts. One of them would contain only the information needed by the installator, the other ones all the rest.

point 10: I'm thinking about the usage of [MS-DOS mode by Endermanch](https://dl.malwarewatch.org/multipurpose/) (Windows10DOS.zip); this way the computer wont reboot into Windows.

point 12: I know Ubuntu can do that. I also know not every distribution can do that.

### Part two: Linux installation

#### General plan:

1. wait until diskcheck finishes,
2. mount the previously formated partition in /boot,
3. create an ext4 partition mounted in / on which data will be written !from the end!,
4. install the system with using previously collected data, 
5. copy the appropriate script to the appropriate folder,
6. reboot.

No details and remarks.

### Part three: Self-made OOBE

#### General plan:

1. autoexecute the script,
2. close the welcoming program provided by the distro,
3. create a folder /Dysk Właściwy as a replacement of %systemdrive%,
4. recreate the whole folder structure,
5. start moving the files,
6. wait for error: "not enough space"
7. stop copying,
8. shrink the Windows' partition and expand Linux's partition,
9. go back to point 5,
10. sudo apt install name-of-the-program, but only the native ones,
11. read configurations of particular programs and move it (what can be applied),
12. install WINE, Bottles or whatever will be trendy and install appropriate programs,
13. delete scraps of Windows and manage empty space,
14. load the appropriate user configuration,
15. sudo apt update && sudo apt upgrade && reboot one again.

#### Details and remarks:

point 4: It's an easily understandable idea, which makes it independant from NTFS

points 5-10: Normal copying would throw a "not enough space" error.

I hope that's all for now.
