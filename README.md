# Prusaslicer 2.1.0-Skinnydip edition 1.0b 
## (MMU2 stringy tip eliminator)

### Purpose:
This script is used to eliminate the stubborn threads of filament that can jam the MMU2 during toolchanges by providing a brief secondary dip into the melt zone immediately after the cooling moves complete.

### Installation:
Back up any existing PrusaSlicer profile directories that you care about before running this application.   There is no guarantee that this build will play nice with mainstream builds of Prusaslicer.

### Usage:
**This tool adds several new menus into Filament Settings > Advanced.   To see all the available settings, click the expert tab in the top right corner.**

There are 2 main types of interventions for stringy tips that this tool provides.  

The first of these is the ability to set a different toolchange temperature.  It seems that cooler temperatures are associated with less stringy tips, though it may also be partly due to the time it takes the hotend to cool to these temperatures as well

The second intervention is the "Skinnydip" procedure -- a rapid dip of the tip back into the melt zone, for the purpose of burning off any residual stringy tips.

**The most important parameter to configure correctly is the insertion distance.**
This distance is the depth that the filament is plunged back into the melt zone after the cooling moves complete. The goal is to melt just the stringy part of the filament tip, not to remelt the entire tip, which would undo the shaping done by the cooling moves. If this number is too high, filament will be rammed out of the hotend onto the wipe tower, leaving blobs. If it is too low, your tips will still have strings on them.

### Explanation of configuration parameters in Filament Settings > Advanced:

| Parameter 	      | Explanation 	                                                                      | Default Value |
| ----------------- | ----------------------------------------------------------------------------------- | ------------- |
| Toolchange temperature enabled 	| Enables temperature changes when the printer is changing between extruders 	| off |
| Toolchange temperature 	| Adjust hotend temperature to this value during a toolchange |	N/A |
| Fast mode 	| An experimental setting which switches to the toolchange temperature just before the cooling moves in order to save print time 	| off |
| Use part fan to cool hotend 	| Experimental: Enables part fan to come on during temperature change cycle to further reduce print time | off |
| Toolchange part fan speed 	| Experimental: Set toolchange fan speed percentage 	                    |0 (percent)|
| Enable Skinnydip string reduction 	| Enable plunging of tip into the melt zone to burn off stringy tips | off |
| Insertion distance| Distance in mm for filament to be inserted from the cool zone into the melt zone. This setting is hardware and assembly specific, so it must be determined experimentally. For stock extruders, use 40-42mm. For bondtech BMG extruders, use 30-32mm. If blobs appear on the wipe tower or stringing starts getting worse rather than better, this value should be reduced. |	off |
| Pause in melt zone 	  | Stay in melt zone at the bottom of the skinnydip cycle for this amount of time. Gives more time for filament to melt  | 	0 (milliseconds) |
| Pause before extraction 	  | Pause in cooling zone after skinnydip cycle.  Helps prevent hot tip of filament from getting squashed when it passes through the bondtech gears  | 	0 (milliseconds) |
| Speed to move into melt zone 	  | Speed to plunge tip of filament from cooling zone to melt zone  | 	33 mm/sec |
| Speed to extract from  melt zone 	  | Speed to extract of filament from melt zone back to cooling zone during skinnydip move  | 	70 mm/sec |


This method appears to be highly effective for removing fine strings of filament, but my hope is that this edition of Prusaslicer will only be needed for a short time.   Ideally these routines would be included in a mainstream build or incorporated into a plugin (since PrusaSlicer doesn't currently have a plugin manager, it might be a while before the latter happens.



