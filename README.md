# GTARW-BlenderMapExport
Simple scripts for Blender 2.8 and DragonFF -plugin to export IPL/IDE files for GTASA and GTAVC.

Some simple and messy scripts to <b>export IPL/IDE files from Blender to GTASA/GTAVC</b>. I use them with map-cleaned GTASA/VC to make a new map from the scratch.
These scripts are meant to use in conjuction with <b>DragonFF -plugin, made by Parik27</b> (https://github.com/Parik27/DragonFF).

# Usage:
# Blender_IplExport.txt:

Have your map ready in Blender with .dff Collections. Open the script in Blender Text Editor and in the first lines change 'iplName' to name that you wish to use with your .ipl and .ide files (I use "vesanto"). Next there is 'lod' and 'interior' variables. I have only used -1 for 'lod' and 0 for 'interior', maybe they work with other values too (?).

After that, there is two variables for .ide settings: 'textureName' and 'drawDistance'. At the time this script will be able to use only one .txd file for all models, so put that name to variable 'textureName', without ".txd" extension.
Next there is 'ID' variable that will be used as base for the objects ID. Every exported object will increase this by 1. I use 5001 (note that I'm using map cleaned GTASA, so there will be a lot of unused IDs).

When you have all that set up, select all models that you want to export, go to the Text Editor and hit ALT + P, or select Edit -> Run Script and you should have your IPL and IDE files exported!

Exporting DFFs is easy as you have all your models selected already, just hit File -> Export -> DragonFF DFF (.dff), check 'Mass Export', uncheck 'Preserve Positions' and export your .dff files to where you want.

<b>NOTE:</b> This script uses fixed scale and rotation, so if your models appears with wrong rotation or scale in-game, you need to "Apply Rotation" and/or "Apply Scale" in Blender before exporting. Sorry for that!

<b>NOTE 2:</b> If your object have property named "prop" or "skip", it won't be exported!

-------------------------------------------------------------

# Blender_DffColConverter.txt:

After you have exported your .ipl, .ide and .dff(s) files, you can use this script to export the same models to collision file. Open this script in Blender Text Editor and in first lines there is 'toDFF' variable. Set its value to 0 to convert .dff collections to .col collections. After that line, there is a section with arrays where you can put your texture names that will be converted to spesific collision type (NOTE: WIP). Then in Text Editor hit ALT + P, or select Edit -> Run Script and it removes ".dff" from name of the collections and set their Type to 'Collision'.

After that you can export your collisions from File -> Export -> DragonFF Collision (.col). After you exported the collisions, you can set the 'toDFF' to value 1 and run script again and it will convert your .col collections back to .dff collections.

<b>NOTE:</b> I'm not sure if this is needed, but after exporting the collisions, I open them in "Collision File Editor II 0.4 BETA", select all collisions, right click and select "Optimize" and save after that.

-------------------------------------------------------------

# Blender_PropsIplExport.txt:

Let's say that you want to use props from the game, which have .ide already defined. You can use this script to export .ipl file for them.

First import .dff ('CJ_Dumpster' for example) to your scene and place it where you want. Then select object, go to "Object Properties" tab and find "Custom Properties" column. Then add new custom property, and set "Property Name" to "prop" and put your object ID to the "Property Value" (for 'CJ_Dumpster' it would be 1345). Now your prop is ready for export! You can also duplicate the prop as many time as you want, the script will remove .001, .002 etc. from the name when exporting.

So open the script in Blender Text Editor and set 'iplName' value to name that you want to use (I used 'vesantoprops') and set 'path' variable to point your custom map folder. Then just hit ALT + P, or select Edit -> Run Script and your props will be exported to .ipl file!

<b>NOTE:</b> Only objects with property named "prop" will be exported!
