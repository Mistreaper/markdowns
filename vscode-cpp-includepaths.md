# Add default includePaths to vscode and test SDL2

There is a way to set default `includePaths` in vscode without having to add them manually each time you create a project. The default `includePath`s are there in your `settings.json` file.

## Method 1: Settings (UI):

Press `ctrl+shift+p`, type in `settings` and select `Settings (UI)`. In the settings tab, search for `includePath`. There should be one that says "C_Cpp › Default: Include Path", that's where you add your `includePaths`.

Click "Add Item", and type in the path without quotation marks or double backslashes (on Windows).

For example:
```
C:\ProgramData\scoop\apps\sdl2\current\include\SDL2
```
or
```
/usr/include
```
## Method 2: Settings (JSON):

Press `ctrl+shift+p` and type in `settings`. From there, select `Settings (JSON)`. This will bring you up to a JSON file that you can edit. 

Add this line:

```
,"C_Cpp.default.includePath": [
        "C:\\ProgramData\\scoop\\apps\\sdl2\\current\\include\\SDL2",
],
```

The comma at the start is only needed when the previous line doesn't include a comma at the end. Now, you may add your includePaths inside the brackets, separated by commas. **On Windows, use double backslashes.**

Example:

```
"C:\\Windows\\include",
```
or
```
"/usr/include",
```

## Testing SDL2 (Windows)

I presume that you have `scoop` installed. If not, refer to my other guides (`scoop.md`) for instructions on how to install it. Run this command to install SDL2 systemwide (you need administrator privileges in PowerShell):

```
scoop install sdl2 -g
```

Then, add this to your default includePath (UI):

```
C:\ProgramData\scoop\apps\sdl2\current\include\SDL2
```
or if you're editing the JSON file:
```
"C:\\ProgramData\\scoop\\apps\\sdl2\\current\\include\\SDL2",
```

Test it by creating a new C++ project using the [C/C++ Project Generator](https://marketplace.visualstudio.com/items?itemName=danielpinto8zz6.c-cpp-project-generator) and adding:

```
#include <SDL2\SDL.h>
```