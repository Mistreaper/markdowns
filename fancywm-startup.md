# Remove FancyWM (tiling WM) annoying popup on startup !

Do you like this tiling WM? I found out a way to remove the annoying popup on startup, which can be a bit annoying for users without a license. Let's get started.

## Create the shortcut for FancyWM
Find FancyWM in the start menu, and drag it to the desktop. You can move the `.lnk` file on the desktop to another directory, most preferably somewhere in your `~` or `/Users/WINDOWSUSERNAME` directory.

## Create a batch file

Create a batch file called `start-minimized-fancywm.bat` with the content:

```
start /min C:\Users\realm\.local\share\FancyWM.lnk
Taskkill /IM FancyWM.exe /F
start /min C:\Users\realm\.local\share\FancyWM.lnk
```

## Moving it to the startups folder.

Open the "Run" window with `Win+R`, and type `shell:startup`. It will bring you somewhere, to this directory: `C:\Users\<WINDOWSUSERNAME>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`.

Move the `start-minimized-fancywm.bat` file to this directory. Now you can start this program minimized on startup! Make sure to disable the original startup program too!