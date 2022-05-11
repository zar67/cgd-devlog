---
layout: post
title: "Game Jam One - First Play Test"
date: 2021-10-26 18:00:00 +0100
tags: jam-one assassins-creed play-test
---

At the start of week two we had our first group meeting / play test. We discussed next steps and decided we would need to merge all our work together soon, especially the Combat and AI. We also shuffled some work tasks around as some of the more complicated tasks turned out to be easier than expected such as the combat.

We also decided that everyone would make at least one section for the procedural level generation so that we have a range of sections to be displayed when playing the game.

After the play test I started work on the character climbing, allowing the player to hang off ledges, climb up and drop off.

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/hanging-collider.png" alt="Basic Test Environment Setup"/>
</p>

When the player presses the climb keys (either W and S on the keyboard, or up and down on the joystick) the player climbs in the related direction to either hang, climb up or drop down. 

This week I also created some more animations for the player including a crouching animation, a wall sliding animation and a hanging animation.

I also added in some environment sprites so that there weren’t white cubes everywhere anymore. I made a simple brick texture as well as a wooden platform texture for the hanging platforms. This is what they look like:
 
<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/environment-sprites.png" alt="Environment Sprites"/>
</p>

The final task I completed was merging all of the groups work together so that we had a complete game loop to show off. I made some fixes to the UI and merged in all the branches together (on a test branch). I created a Game Scene and added all the relevant scenes to the build settings. With some minor bug fixes, I had a working game loop that was a culmination of all the work the group has done so far.

Just before this week’s meeting I created created a world section and a better starting section to give some variety as we play and show off the game. The new section also gave the ability to show off the AI and the movement fully.