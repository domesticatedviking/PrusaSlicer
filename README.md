#Prusaslicer-Skinnydip edition (MMU2 string eliminator)

###Purpose:
This script is used to eliminate the stubborn threads of filament that can jam the MMU2 during toolchanges by providing a brief secondary dip into the melt zone immediately after the cooling moves complete.

###Installation:
Back up any existing PrusaSlicer profile directories that you care about before running this application.   There is no guarantee that this build will play nice with mainstream builds of Prusaslicer.

###Usage:
This tool adds several new menus into Filament Settings > Advanced.   To see all the available options, click the expert tab in the top right corner.

There are 2 main types of interventions for stringy tips that this tool provides.  

The first of these is the ability to set a different toolchange temperature.  It seems that cooler temperatures are associated with less stringy tips, though it may also be partly due to the time it takes the hotend to cool to these temperatures as well

The second intervention is the "Skinnydip" procedure -- a rapid dip of the tip back into the melt zone, for the purpose of burning off any residual stringy tips.

The most important parameter to configure correctly is "insertion_distance". 
This distance is the depth that the filament is plunged back into the melt zone after the cooling moves complete. The goal is to melt just the stringy part of the filament tip, not to remelt the entire tip, which would undo the shaping done by the cooling moves. If this number is too high, filament will be rammed out of the hotend onto the wipe tower, leaving blobs. If it is too low, your tips will still have strings on them.

###Explanation of configuration parameters:
Parameter 	Explanation 	Default Value
insertion_speed 	Speed at which the filament enters the melt zone after cooling moves are finished. 	2000 (mm/min)
extraction_speed 	Speed at which the filament leaves the melt zone. Faster is generally better 	4000 (mm/min)
insertion_pause 	Time to pause in the melt zone before extracting the filament. 	0 (milliseconds)
insertion_distance 	Distance in mm for filament to be inserted into the melt zone. This setting is hardware and assembly specific, so it must be determined experimentally. For stock extruders, use 40-42mm. For bondtech BMG extruders, use 30-32mm. If blobs appear on the wipe tower or stringing starts getting worse rather than better, this value should be reduced. 	n/a
removal_pause 	Number of milliseconds to pause in the cooling zone prior to extracting filament from hotend. This pause can be helpful to allow the filament to cool prior to being handled by the bondtech gears. 	0 (milliseconds)
toolchange_temp 	Temperature to extract filament from the hotend. Cooler temperatures are associated with better tips. 	off



This method appears to be highly effective for removing fine strings of filament, but my hope is that this branch will only be needed for a short time.   I hope that one day these methods will either be part of an official branch, or they will be incorporated into a plugin (since PrusaSlicer doesn't currently have a plugin manager, we might be waiting a long while for that option.)



