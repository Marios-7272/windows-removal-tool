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
7. fetch time, date, device name,
8. save in %systemdrive%\e\systemconfig.cfg 
9. make a list of all installed programes,
10. "translate" them to something linux understands (again, the details),
11. make configs of particular users (ease of access, wallpapers, colors, desktop icon layout (if it is entirely possible), etc.),
12. save in %systemdrive%\e\userconfig.cfg,
13. ask for confirmation,
14. 'Did you back up all your data?'
  if yes: proceed to 15
  if no: slect a drive and do a backup
15. 'Do you have a thumb drive with nothing important on it?'
  if yes: use the thumb drive
  if no: 
    diskpart
    sel vol=%systemdrive%
    shrink desired=k* 1024 where k is a natural number determined by the size of the iso file
    cre par efi size=k* 1024
      if error:
      cre par pri size= k* 1024
    assign letter l
16. download iso
17. unpack (fat32 partiton)/burn .iso
18. modify the copy (includes copying %systemdrive%/e)
19. add Linux to boot options
20. remove Windows from boot options

#### Details and remarks:

point 3: In this section I want the program to explain what is a distro, show basic info and a ton of screenshots from various places and apps, all standardized.

point 4: A searchbox and a status: 'good', 'janky', 'forget about it' and most popular equivalents.

point 10: By 'translating' I mean creating a scipt which will be all sudo apt install programs-name. Furthermore not everything availible on Windows will be availible on Linux. In this situation we will need to copy %systemdrive%\Program Files or Program Files (x86)\whatever-it-is and prey that WINE or Proton will run it. 

point 18: .iso has to be stock, it doesn't need to have any modifications. An autoinstall script will be made by this program based/basing on a given template (plis help my english).

point 18 again: I know Ubuntu can do that. I also know not every distribution can do that.

### Part two: Linux installation

#### General plan:

1. wait until diskcheck finishes,
2. format 
3. install
4. copy
5. apply systemconfig 

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
