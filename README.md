ES-config
=========

A flexible tool for configuring multiple emulators simultaneously.  Written in C++ with SDL and AngelScript.

Building
========

As some of the dependencies are not in the Debian repositories, getting dependencies is a little bit complicated.
To solve that, **I've written a short Bash script named "get_dependencies.sh" that does everything for you**, including install AngelScript. You can run it with `./get_dependencies`.

OR, If you want it install everything yourself, you'll need these dependencies:
```
sudo apt-get install libsdl1.2-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libboost-filesystem-dev
```

You'll also need [AngelScript](http://www.angelcode.com/angelscript/downloads.html), which is inconveniently absent from the Debian repositories!
At the time of writing, the newest version is 2.26.1.

After all that's over, just run `make`. The resulting binary is named `es-config`, and is not copied anywhere.

Usage
=====

Command line arguments (all paths must be absolute: ~ is not expanded):
```
--scriptdir [path]				search for scripts at [path]
--resourcedir [path]			load images, etc from [path]
--settings [path] 				load settings from this file
--configpath [from] [to]	redirect config output [from] to [to]
--help			    	pierce the heavens
```

Currently, ES-config uses the following resource files (expected to be located in ./resources, but changable with --resourcedir):
```
checked.png - icon for selected in emulator list
unchecked.png - icon for unselected in emulator list
done.png - icon for input configured
notdone.png - icon for input unconfigured
font.ttf - font used throughout
controllers/360esque.png - controller image
controllers/360esque.xml - controller image path and button location definitions
```

F4 will close the application if it hasn't frozen.


Settings
========

You can set most of the command line arguments (as well as some extra settings) from an XML file, loaded with `--settings path/to/file`.

```
<scriptDir>/absolute/path/to/scripts/folder/</scriptDir>
<resourceDir>/absolute/path/to/resource/folder/</resourceDir>

<!-- Redirect the "retroarch.cfg" file to the config folder... -->
<changeConfigPath from="retroarch.cfg" to="/home/pi/RetroPie/configs/all/retroarch.cfg" />
```


This is still a work-in-progress!

-Aloshi
http://www.aloshi.com
