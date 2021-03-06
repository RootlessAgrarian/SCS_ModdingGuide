## Intro to Non-Map Mods

### Overview

To get started with non-map modifications to SCS simulators (ATS, ETS2) you need first to understand a little about how
the game boots and configures itself.

The game engine reads zip files (noncompressed zip archive format) which for sake of clarity have been renamed from .zip to
.scs.  With your licensed copy of the game, you get the base.scs and def.scs files, which you will find in the **INSTALL**
folder (see [Before You Start](../tutorialguide.md) for explanation of folder structure).  If you were to unpack these and see them from the game engine's point of view, you would be looking at a deep, complex directory hierarchy whose top level 
looks like this:
```
base/
     automat
     contentbrowser
     custom
     def
     dlc
     effect
     font
     map
     material
     model
     model2
     prefab
     prefab2
     road_template
     sound
     system
     ui
     unit
     vehicle
     video
```
When you create a mod -- whether it be a map mod or some other mod -- you replicate, inside a zipfile, a portion of this 
wide and deep directory structure;  and this shadow structure you populate with files that you have altered.  
In other words, if you modified just *the audio level for interior sounds for the Mercedes Actros Truck*, you 
might end up with a mod (zipfile) containing a directory hierarchy like this:
```
def/
    vehicle/
            truck/
                  mercedes.actros2014/
                                      sound/
                                            interior_16.sii
                                            interior.sii
```
You might name this zipfile, perhaps, QuietCabActros.scs.  If you put it in your USER/mod folder at startup time, and then
configured a profile to use it, the game would read the files in your mod file AFTER it reads the base game files, and
would OVERRIDE values in the base game files with values that you had altered by editing the two .sii files you see above.

The same applies for other aspects of the game.  You could extract a named model from the game, such as the Mercedes
Actros 2014 truck above, and use 3d graphics editing tools to change its appearance.  Then you could package it in a
mod that contained the files you altered, and load the mod.  The game's default version of the truck by that name
would then be overwritten by your version.

When you set the "Priority" of mods for your Profile in the Mod Manager, you are telling the game what order to load
them in.  The highest priority will be loaded last, i.e. they will overwrite all earlier mods and have the last word.
**Note:** the load order of the Map Editor is alphabetical, and it loads everything it finds in the USER/mod folder.  The 
Map Editor neither knows nor cares about Profiles.  If you want to control your mod load order while editing, you may want 
to use numerical or alphabetic sorting prefixes for your mod names.

So now you know the most fundamental fact about modding this game:  it is all about populating a shadow version of the
game's own data hierarchy, storing that shadow structure in a zipfile, and loading the zipfile from the USER/mod folder.

### How do I get at the files?

SCS ships their games as an engine plus a set of .scs files.  (There are some other freestanding .sii files and profile data
and so on, but let's focus on the stuff inside def.scs and base.scs for now).

If you try to unzip base.scs and def.scs, it won't work.  SCS uses something not quite the same as zip to create them, so
you'll need their extractor tool to unpack them.  This tool is found here http://modding.scssoft.com/wiki/Documentation/Tools 
(the Game Archive Extractor).

If you download this tool and use it correctly, you will unpack your enormous **INSTALL/base.scs** file into a directory hierarchy which
the tool by default names base_exp.  You can then use it on def.scs, which will unpack as def_exp.  You probably want to move these
to a working folder somewhere outside **INSTALL**, rename them to "base" and "def", and possibly put "def" inside "base" so that the complete hierarchy will look just like the inside of your finished mod file.

### How do I make my mod?

First, you have to understand what you are trying to change, which files in the hierarchy control what you are trying to change, and
how you need to edit their content to achieve your desired change.  Most of the def files are pretty self-explanatory if you are used
to reading code and reverse-engineering stuff.  Some are less obvious and you may need to google a bit, or do some try-it-and-see experiments.  Some of the game files are binary and may need specialised tools to modify.

There's more information out there about non-map modding than about the Map Editor, which is why I focus on map editing and don't spend much time on non-map modding in this Guide.  Here are some links to get you started...

* [SCS Beginner Tutorials](http://modding.scssoft.com/wiki/Tutorials/Beginners)
