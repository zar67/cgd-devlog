---
layout: post
title: "Game Jam Two Final Week - Feedback"
date: 2021-12-07 18:00:00 +0100
tags: jam-two turn-based-cyborgs
---

# Summary
The final week was mainly bug fixing and small tweaks as well as adding some quality of life features.

I added in different coloured ruins, to indicate to the player which ruin is theirs. I changed the ruins to have a unit type so when the unit dies the player can change the unit, after discussing with the group I changed this so that when the player changes the unit type on the ruin, the unit is regenerated so they don't have to wait until the unit dies to get the new type. 

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-two/ruin-ui.png" alt="Ruin UI with selectable unit type"/>
</p> 

I also fixed the clamping bug with the camera, so now the camera is correctly clamped to the world.

We managed to get a complete game loop in this final week, with an end state. I added in some checks to make sure that the player can only move their own units, and can only do so on their turn. 

Finally this week I also made the UI one coherant style, and fixed a lot of the positions to make it scalable. I also fixed the game HUD so that the turn ui updated correctly and hid the end turn button when it's not the players turn.