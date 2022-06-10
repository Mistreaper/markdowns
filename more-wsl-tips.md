# Here are more WSL(2) tips!

## Linking powershell and cmd to `/bin`

Find the paths of powershell and cmd:
```
which powershell.exe
which cmd.exe
```

The output should be similar to this:
```
$ which powershell.exe
/mnt/c/Windows/System32/WindowsPowerShell/v1.0/powershell.exe
$ which cmd.exe
/mnt/c/Windows/system32/cmd.exe
```
Copy the first path (powershell), and run:
```
sudo ln -s <PATH> /bin/powershell
```

Then, copy the other path (cmd), and run:
```
sudo ln -s <CMDPATH> /bin/cmd
```
## Using `scoop` Windows package manager on WSL2

You can actually use `scoop` on WSl2. Simply just install `scoop` normally through PowerShell:

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

Invoke-WebRequest get.scoop.sh | Invoke-Expression
```
Run these commands to add the `extras` repository:

```
scoop install git
scoop bucket add main
scoop bucket add extras
```
## Running programs as Windows Admnistrator on WSL2 (`sudo` from scoop)

Simply open PowerShell and install `sudo`:

```
scoop install sudo
```

Open WSL2, run `which sudo`. You should find one that starts with `/mnt` and has `scoop/shims` in it. Here is an example of an output:

```
/usr/sbin/sudo
/usr/bin/sudo
/sbin/sudo
/bin/sudo
/mnt/c/Users/realm/scoop/shims/sudo # this one is the path to sudo
```

Copy the path that you got from the command line. Now, run this command to symlink `sudo` from scoop as a command called `addo` (you may name this anything you like, but this stands for "Administrator Do". You need to distinguish it from the Linux `sudo`):

```
sudo ln -s <PASTE-PATH-HERE> /bin/addo
```
Test if you can install `firefox` globally through `scoop` through WSL:

```
addo scoop install firefox -g
```
## Actually, you can run Windows applications from WSL2

Not just only `scoop` and others, but you can run *any* Windows application from WSL2 as long as it is in your `$PATH`. Run this command to check your `$PATH`:
```
echo $PATH
```
The `System32` directory is in your `$PATH` by default. I usually symlink the Windows apps to `/bin/` so that I can run them from WSL2. You can also add directories to your `$PATH`. 

Since `regedit.exe` is already in your `$PATH`, try running `regedit.exe` with `addo` from the step above:

```
addo regedit.exe
```

