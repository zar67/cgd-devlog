---
layout: post
title: "Death Capturing Bugs and AI Rework"
date: 2022-04-20 18:00:00 +0100
tags: cohort-project
---

# Summary

This week I fixed a few errors with the death minimap camera being un-set and a network object error with the player respawn positions. I also fixed an error in the skill tree where an event was being subscribed to in OnEnable and OnDisable which was causing an error.

This week I fixed a bug where players would still capture bases on death, since the player model was still in the capture zone. This was simple enough to fix as adding a check to make sure players in the zone were alive was all that was needed. 

I also added in a check to make sure that the unit spawning UI only showed for local players, as it was showing for everyone.

We also had a discussion about the capture speed in our group meeting this week, we decided that to make the AI more effective and useful in the game they should capture bases at the same speed as players, so we reduced the capture speed of players and increased the speed of AI.

Due to a change in the skills UI, I managed to simplify the death map to remove the tab system and just have the respawn map show. I plan later to rework the map so that it is easier to use and more interactive.

Finally this week we had a discussion about the AI and what we wanted it to be compared to what was implemented in the game. We decided that the currently implemented map to control the AI wasn't intuitive enough and we wanted to rework it to be similar to the death UI. We also decided to simplify what the player could do with AI, we decided that AI should only be able to be sent to bases and what the AI did depends on what team owns the base. If the base is owned by the same team as the player controlling the AI then AI would defend the base, and if not the AI would attempt to take over the base by attacking. 

<img src="{{site.baseurl}}/assets/cohort-project/ai-map.png" alt="AI Map"/>