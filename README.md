# PACAnalyzer
#### By Bryan O'Malley (bo122081@hotmail.com)

[![Join the chat at https://gitter.im/Reithan/PACAnalyzer](https://badges.gitter.im/Reithan/PACAnalyzer.svg)](https://gitter.im/Reithan/PACAnalyzer?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
Perception-Action Cycle analysis plugin for SC2Reader (https://github.com/GraylinKim/sc2reader)

This plugin is built based on the work of Mark Blair, Ph.D, 
and the Simon Fraser University Cognitive Science Lab (http://cslab-sfu.ca) on the SkillCraft project. You can find their project website at:
http://skillcraft.ca

This plugin adds a list of PACs to each human player in a replay.

The list consists of PAC objects with the following attributes
* **min, max**: Min & max camera coordinates for this fixation
* **cameras**: list of camera actions during this PAC, formatted as [frame#, x, y] for each camera action in the list
* **actions**: list of frame numbers actions were taken on during this PAC

Additionally, a PACInfo object is added to the replay with the attributes DispThreshold and DurThreshold. DispThreshold is the max combined x & y shift before a new fixation is started while DurThreshold is the minimum duration for a camera location to be considered a fixation.

Finally, a PACStats object is added to each human player with the following statistics calculated:
* **ppm**: average(mean) PAC per minute
* **pal**: PAC action latency. e.g: how long it takes you to take your first action after each fixation shift. (mean average)
* **app**: Actions per PAC. The average(mean) number of actions you take each PAC.
* **gap**: How long it takes you, after finishing your actions in one PAC to establish a new fixation. (mean average)

**PACAnalysis.exe** is a command-line tool for analyzing replays for PAC stats. You can execute it from command line, or simply drag one or more replays, or even a folder of replays on the executable.

**PACAnalysis.py** is the SC2Reader script used to generate the executable, with the help of **setupExe.py**, a setup script for py2exe. Once the distributible executable has been generated by py2exe (dist/PACAnalysis.exe), change its extension to .zip and draw the accompanying folder (dist/sc2reader) into it. Then simply change its extension back to exe and it will run.
