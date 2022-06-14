# Tiny intro to `scoop`

Scoop is a package manager for Windows, which allows you to install programs through the command line and update all of them at once. Scoop is more developer centric unlike `choco`.

Scoop uses `.json` manifests (similar to `PKGBUILDS`) to install programs. The manifests tell Scoop how a program is installed and its dependencies + conflicts.

## Installing scoop

Open PowerShell without admin:

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

irm get.scoop.sh | iex
```

If there's an error related to opening Internet Explorer, try running the commands again after opening IE. Otherwise, head over to the next step.

## Setting up scoop + installing MinGW

Open PowerShell without admin:

```
scoop install git
scoop install sudo
scoop bucket add main
scoop bucket add extras
scoop update
```

If you want to install the programs globally, then run these commands in PowerShell (admin):
```
scoop install git -g
scoop install sudo -g
scoop bucket add main 
scoop bucket add extras
scoop update
```

Installing MinGW is quite tricky. The name of the package is `msys2`, not `mingw`. Open PowerShell (admin) and run this command:

```
scoop install mingw msys2 -g
```
If you want to, you can try using `sudo`, which lets you run commands with elevated privileges without leaving normal powershell:

```
sudo scoop install mingw msys2 -g
```