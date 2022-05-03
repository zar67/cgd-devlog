---
layout: post
title: "Simplifications"
date: 2022-04-27 18:00:00 +0100
tags: cohort-project
---

# Summary

This week I started by getting the unit spawning hooked up with the AI map so when spawned units are designated to defend the base they are spawned at, meaning that the AI map and new AI system is fully functioning. I also added a separate camera for the death and AI map screens, however this was made redundant later in the week when I reconfigued the maps to be full screen later.

I also fixed a few bugs this week including the name tag flickering and the death minimap camera being unset.

This week I also updated respawn UI to be in line with the rest of the UI style. As mentioned I also made the AI map and the respawn map full screen and added some more interactivity such as displaying when the bases are being contested. I had some issues with the positioning of the base selectors on the map but eventually managed to get this to work correctly.

<img src="{{site.baseurl}}/assets/cohort-project/ai-map.png" alt="AI Map"/>

I also made some changes to the unit spawning and defence UI to simplify it and to get the colours updating correctly per team. I reduced the options of the turrets down to the one basic turret. 

Finally I also got the entity script on the VTOL setup with the values, duplicated from the entity script on the mech. This makes sure that the capture zone will detect both the mech and plane versions of the player.