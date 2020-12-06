---
title: Portfolio
layout: page
permalink: /portfolio/
---
#### Navigation:

* [Standalone Applications](#Standalone Applications)
* [Publication](#Publication)
* [Game Projects](#Game Projects)
* [Game Mods](#Game Mods)
* [Graphic Work](#Graphic Work)

* * *

<h1 style="text-align: center;">
  <a name="Standalone Applications"></a>Standalone Applications
</h1>

## [![Pep 8 Icon](../content/pep/pep8icon.png)  Pep/8](https://github.com/StanWarford/pep8)

The Pep/8 application is a simulator and assembler for the Pep/8 machine, a 16-bit complex instruction set computer (CISC). It is designed to teach computer architecture and assembly language programming principles in conjunction with [Stan Warford's Computer Systems textbook](http://computersystemsbook.com/).

It features a graphical stack trace that mirrors the C++ memory model, the ability to set breakpoints, trace the program counter and bytes modified by the previous von Neumann step in the memory dump, and easily see the assembler listing alongside machine code, among other things.

![Stack Trace](../content/pep/pep8trace.png)

The Pep/8 simulator is written in C++, and uses the Qt 4 API using the Qt Creator IDE available from Nokia.

It is available under the GPL at <https://github.com/StanWarford/pep8> for Windows, OS X, and Linux.

I wrote this from scratch in conjunction with [Stan Warford](http://www.cslab.pepperdine.edu/warford/) during the summer and fall of 2009 in order to replace the previous version of Pep8 (v8.0.4) which had experienced a great deal of architecture decay. This served as a platform for new features (such as memory trace), as well as smaller improvements across the board.

I have since continued supporting Pep/8 and it's successors, the Pep/9 and Pep/10 machines with bugfixes, features, additional platforms, and so on.

* * *

## [![Pep8 CPU](../content/pep/pep8cpuicon.png) Pep/8 CPU](https://github.com/StanWarford/pep8cpu)

Pep/8 CPU is a simulator for the data section of the Pep/8 CPU, designed as a teaching tool for students to write microcode sequences and execute them to implement machine code instructions found in the Pep/8 application.

It features a visual representation of the CPU's data section, and ability to see the state of memory and CPU registers, as well as the data stored in the sequential circuits in the data section. It also comes with a suite of example microcode sequences for illustration and teaching purposes.

![Pep8CPU](../content/pep/pep8cpu.png)

The Pep/8 CPU simulator is written in C++, and uses the Qt libraries.

It is [available under the GPL](https://github.com/StanWarford/pep8cpu) at  for Windows, OS X, and Linux.

Similar to Pep/8, I started this project in conjunction with Stan Warford during the fall of 2009 in order to bring it up to date with the Pep8 application, and have continued supporting Pep/9 CPU and Pep/10 CPU development for new versions of Stan's textbook.

* * *

## [![Cahoots](../content/misc/cahootsicon.png) Cahoots](https://code.google.com/archive/p/cahootseditor/)

Cahoots is a real-time, collaborative text editor with a built in chat client. It includes basic code editing functionality, such as syntax highlighting for several languages, as well as collaborative controls for modifying user permissions on the fly.

![Cahoots](../content/misc/cahoots.png)

It is not feature-complete, and is currently in beta due to several outstanding issues. It is written in C++, and uses the Qt 4 API using the Qt libraries.

It is available under the GPL at <https://code.google.com/archive/p/cahootseditor/> for Windows, OS X, and Linux.

This was written for the 2010 Pepperdine Computer Science Senior Capstone class in conjunction with Anandi Hira and David Vega.

* * *

<h1 style="text-align: center;">
  <a name="Publication"></a>Publication
</h1>

#### The Pep/8 Memory Tracer: Visualizing Activation Records on the Run-Time Stack

Presented at SIGCSE 2010, the 41st ACM Technical Symposium on Computer Science Education. The paper is available at [https://www.cslab.pepperdine.edu/warford/Papers/SIGCSE-2010.pdf](https://www.cslab.pepperdine.edu/warford/Papers/SIGCSE-2010.pdf).

#### Automated Generation of Failure Modes and Effects Analysis from AADL Models

Presented at ISSRE 2011, the 22nd annual International Symposium on Software Reliability Engineering.The paper is available at [https://ieeexplore.ieee.org/abstract/document/6983803](https://ieeexplore.ieee.org/abstract/document/6983803).

* * *

<h1 style="text-align: center;">
  <a name="Game Projects"></a>Game Projects
</h1>

## ![The Guardians](../content/misc/theguardians.png) The Guardians

A project for the 2009 Senior Capstone led by Roger Hughston, I created many of the models and textures used ingame using a combination of Wings3d, Maya, and Photoshop, as well as several other tools for converting objects for use in the Panda3D engine.

The Guardians is a space combat simulation that obeys newtonian physics (with several limitations for gameplay, such as a maximum velocity). It is written in Python, with dependencies on PyGame and Panda3D.

Unfortunately, due to time constraints, the scope of the project remained small. However, the modular design and open source nature of the game may allow it future development in the OSS community.

* * *

<h1 style="text-align: center;">
  <a name="Game Mods"></a>Game Mods
</h1>

## sMonitor

sMonitor is a buff, debuff, and cooldown tracker for World of Warcraft. It has the ability to display arbitrary buffs and debuffs, filtered by caster, and filtered by the unit field in [UnitAura](http://www.wowwiki.com/API_UnitAura).

![sMonitor Bars](../content/wow/smonitorbarscd.jpg)  ![sMonitor](../content/wow/smonitoricons.png)

It was inspired by sFilter, sFilter2, and KordaCooldown, and is a fork of the three, merged into a single mod.

Configuration is done in the lua.

[WoWInterface Addon Page](http://www.wowinterface.com/downloads/info19667-sMonitor.html)


## sFonts

Font replacement mod for World of Warcraft. Forked from Tekkub's font mod because I liked his implementation, but not his fonts.

In addition, fonts used now insert themselves into LibSharedMedia, for use in other mods. Further configuration if desired is done in lua, but fonts can be previewed in the ingame addons interface.

[WoWInterface Addon Page](http://www.wowinterface.com/downloads/info19682-sFonts.html)

## sPetSummonTracker

Timer mod for World of Warcraft, designed for Enhancement Shaman and Balance Druids, for tracking how much time Feral Spirits and Force of Nature has left. This is mostly intended for Enhancement Shaman, to help ensure Feral Spirits don't disappear before casting Spirit Walk, particularly in PvP.

![sPetSummonTracker](../content/wow/petsummon.png)

Configuration is in lua.

[WoWInterface Addon Page](http://www.wowinterface.com/downloads/info19664-sPetSummonTracker.html)

## oUF_Saone

oUF_Saone is a unit frame mod for World of Warcraft that uses the oUF framework. It features player, target, target of target, focus, party, pet, and party pet frames, as well as party debuffs, target buffs and debuffs, target-of-target debuffs, focus debuffs, and a host of other features. It is intended to mimic the Blizzard unit frames in function, but included extra information that I found useful.

![oUF_Saone](../content/wow/oufsaone.png)

## oUF_sRaid

oUF_sRaid is a raid unit frame mod for World of Warcraft that uses the oUF framework, intended for use by raid leaders, as well as damage and tank classes. It primarily features threat notifications, debuff highlighting and debuff icons interchangeably, class coloring, health and power bars, as well as range and ready check indicators. More recent features, such as party role indicators are also supported. Configuration is done in the lua.

![oUF_sRaid](../content/wow/raidframes.png)

[WoWInterface Addon Page](http://www.wowinterface.com/downloads/info19666-oUF_sRaid.html)

## AutoAttackIndicator

Notification mod for World of Warcraft. Created as an small indicator of attack state, to circumvent the issue of flashing attack indicator (if using an action bar button for an indicator) being ambiguous in the 'off' state.

![AutoAttackIndicator](../content/wow/autoattackindicator.png)

Configuration is in lua.

[WoWInterface Addon Page](http://www.wowinterface.com/downloads/info19665-AutoAttackIndicator.html)

<!-- [Return to top](#top) -->

* * *

<h1 style="text-align: center;">
  <a name="Graphic Work"></a>Graphic Work
</h1>

Most of the art below was done prior to 2005 using Lightwave, Wings3D, Photoshop, and Terragen.

[![](../content/old/Hermes_Thumb.png)](../content/old/Co_op_Hermes_Flight_by_Bletherskit.jpg)

[![](../content/old/Valkyries_Thumb.png)](../content/old/Flight_of_the_Valkyries_by_Bletherskit.jpg)

[![](../content/old/Training_Thumb.png)](../content/old/Desert_Training_by_Bletherskit.jpg)

[![](../content/old/AeoleusIso_Thumb.png)](../content/old/AeoleusIso.png)

[![](../content/old/Erinyes_Thumb.png)](../content/old/Erinyes.png)

[![](../content/old/Harbor_Thumb.png)](../content/old/Harbor.png)

[![](../content/old/Isle_Thumb.png)](../content/old/Isle.jpg)

[Return to top](#top)