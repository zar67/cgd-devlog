---
layout: post
title: "Cohort Meeting"
date: 2022-04-06 18:00:00 +0100
tags: cohort-project
---

This week we started with a cohort meeting to assess how the project was going and to attempt to fix any concerns the cohort had. We came to the conclusion that weekly demonstrations of what everyone was doing made sense and we should be play testing as a group each week as well. We also came up with a list of things we needed for the game and from that list decided what we wanted for next week. 

Features still to implement:
- Health Bars (both on the client HUD and in world-space above other players heads).
- Damage feedback to indicate when you've shot someone.
- Tutorial/guide on how to play.
- Respawn system showing UI with a delay timer.
- Ability to change skills in the respawn UI.
- Base placement around the map.
- Ability selection on initial spawn.
- Player cards that balance teams automatically.
- Nameplates for players.
- Team indicators (mech colour, health bar colour etc).
- Ability to buy AI.
- Ability to control AI and for them to move and shoot.
- Ability to heal at bases.
- Increase the jet movement speed.
- Colliders need to be tagged with ground.

Features for next week:
- Health bars
- Respawn system
- Base placement
- Team indicators
- Nameplates
- Buying AI
- AI moving and shooting

The session was very productive and I think got most people motivated about the project again.

Firstly I fixed a bug with the turrets where the state wasn't being send over the network, meaning infinite amount of turrets could be placed on one location. I also fixed a bug with the turret health so that turrets could be destroyed again.

I also added in a UI prompt when in range of a unit generation block or a base defence location so that it's easier for the players to understand what to do.

<p align="center">
  <img src="{{site.baseurl}}/assets/cohort-project/defence-interact-ui.png" alt="Defence Interact UI"/>
</p> 

Over the week I took up the tasks of the respawn system. I set the mech model to be disabled on death and added some UI to show when the player dies as well as a respawn button that is only interactable after a certain amount of time. After this I added in a mini-map style view for the player to select which of their bases they want to spawn at. 

<p align="center">
  <img src="{{site.baseurl}}/assets/cohort-project/respawn-death-ui.png" alt="Respawn UI"/>
</p> 

With several systems now requiring the cursor to be shown or hidden, I added in a CursorManager script that had static functions, allowing all the systems to work correctly without fear of the overlap causing issues. 

This week I also added healing from bases when the player is inside a capture zone of their own base and the base isn't being contested or cooling down. 

As Ed managed to get the model in for the player, I edited the materials to create one for blue as well as read and setup a function to change the colour of the player based on what team they're on. 

<p align="center">
  <img src="{{site.baseurl}}/assets/cohort-project/team-colours.png" alt="Team Colours"/>
</p> 

Finally we had another play test on Monday where we found more issues and closed ones that had been fixed. 