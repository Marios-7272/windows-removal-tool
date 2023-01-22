# Windows Removal Tool
Welcome to the Windows Removal Tool site! This is a concept of a program which is supposed to:
- delete Windows,
- install Linux,
- help with distro selection
- move all the user data while keping it intact,
- install all the previously present programs.
It is targeted to people who either want to start their Linux adventure with some training wheels or need their grandma's computer to run linux, because it is 10 years old and it would be a pitty to discard it yet, or want to prank school's IT guy, or are the IT guy themselves and want automation.  

#### Disclaimer:
I am a Polish highschool student who can't code at all but uses Linux daily. This is my first project ever. I will make a ton of misakes, so please do not expect everything to be correct, let alone neat and easily understandable. 

## Inner workings:

### Part one: preperations in Windows

#### General plan:

The first part is preperations to overwrite Windows. I think it should look more or less like this:
1. elevate
2. ask whether to dualboot or singleboot
3. distro selection (look at the details)
4. program compatibility check
5. create %systemdrive%\e (it doesn't always have to be C:\),
6. ask about usernames and their passwords and which is the administrator,
7. make a list of all installed programes,
8. "translate" them to something linux understands (again, the details),
9. make configs of particular users (ease of access, wallpapers, colors, desktop icon layout (if it is entirely possible), etc.),
10. save it all in %systemdrive%\e\sth.cfg,
11. ask for confirmation,
12. 'Did you back up all your data?'
  if yes: proceed to 13
  if no: open default backup software and display message 'This window can be minimized now.' and a 'My backup is done.' button
13. 'Do you have a thumb drive with nothing important on it?'
  if yes: use the thumb drive
  if no: 
    diskpart
    sel vol=%systemdrive%
    shrink desired=k* 1024 where k is a natural number determined by the size of the iso file
    cre par efi size=k* 1024
      if error:
      cre par pri size= k* 1024
    assign letter l
14. download iso 
15. unpack (fat32 partiton)/burn .iso
16. modify the copy
17. add Linux to boot options
18. remove Windows from boot options

#### Details and remarks:

generarily: .bat will do, maybe something precompiled. There is no need for sophisticated GUI. The user will have to be happy with a frame made out of dashes and equasin signs. It would be nice to pack it into an installator.

point 15: .iso has to be stock, it doesn't need to have any modifications. An autoinstall script will be made by this program based/basing on a given template (plis help my english).

point 9: by "translating" i mean creating a scipt which will be all sudo apt install programs-name. Furthermore not everything availible on Windows will be availible on Linux. In this situation it will be needed to go to %systemdrive%\Program Files or Program Files (x86)\whatever-it-is-supposed-to-be, copy all the files, do all we can and prey that WINE or Proton will run it. 

point 11: It will be necesarry to split it into multiple scripts. One of them would contain only the information needed by the installator, the other ones all the rest.

point 14: I know Ubuntu can do that. I also know not every distribution can do that.

point 15: I'm thinking about the usage of [MS-DOS mode by Endermanch](https://dl.malwarewatch.org/multipurpose/) (Windows10DOS.zip); this way the computer wont reboot into Windows.

### Part two: Linux installation

#### General plan:

1. wait until diskcheck finishes,
2. mount the previously formated partition in /boot,
3. copy the data on the previously slected drive,
4. delete Windows' partition,
5. create an ext4 partition mounted in / on which data will be written !from the end!,
6. install the system with using previously collected data, 
7. create a folder /Dysk Właściwy as a replacement of %systemdrive%,
8. copy the data back,
9. reboot.

#### Details and remarks:

poionts 3,8: Copying data from the level of the installator will decrease drive's load. Linux's installator will put less stress than (if at all).

point 7: It's an easily understandable idea, which makes it independant from NTFS

### Part three: Self-made OOBE

#### General plan:

1. autoexecute the script,
2. close the welcoming program provided by the distro,
3. sudo apt install name-of-the-program, but only the native ones,
4. read configurations of particular programs and move it (what can be applied),
5. install WINE, Bottles or whatever will be trendy and install appropriate programs,
6. translate .lnk to .desktop
7. load the appropriate user configuration,
8. sudo apt update && sudo apt upgrade && reboot one again.

#### Details and remarks:

None.

I hope that's all for now.
