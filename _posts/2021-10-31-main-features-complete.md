---
layout: post
title: "Main Features Complete"
date: 2021-10-31 18:00:00 +0100
tags: jam-one assassins-creed 
---

This week I started by completing the bug with climbing where the player gets stuck. As suggested last week this was because of the two colliders on the player. I fixed this by removing the crouch collider and changing the height of the main collider when the player crouches, this fixed the issue quite nicely. 

Next I added in some environment sprites so that there wasn't white cubes everywhere anymore. I made a simple brick texture as well as a wooden platform texture for the hanging platforms. This is what they look like:

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/environment-sprites.png" alt="Environment Sprites"/>
</p>

I next worked on merging all of the groups work together so that we had a complete game loop to show off. I made some fixes to the UI that Liam created and merged in all the branches together (on a test branch). I created a Game scene added all the relevant scenes to the build settings. With some minor bug fixes I had a working game loop that was a culmination of all the work the group has done so far.

The final thing I did before this weeks meeting was create a world section and a better starting section to give some variety as we play and show off the game. The new section also gave the ability to show off the AI and the movement fully.

During the play test this week with Andy we recieved the following feedback:
- Hay Bales would be good to push the Assassin's Creed IP a bit more.
- Generally the game is looking good.
- There should be some death animations and effects.
- We need to discuss and think about flow/difficulty, how the player will be kept interested and just on the edge of failure.

After the play test we discussed as a group what we needed to do next and also discussed our ideas for difficulty. We concluded that the difficulty would increase at certain score thresholds the player reached and that the following things would be influenced by the difficulty:
- The speed of the camera movement (changing the camera to a static, constantly moving one)
- The amount of AI that spawn within a section.
- The speed of the enemy movement.
- How far the enemy can see.

The first thing I went about implementing after the play test was the death animations, both for the player and the enemies. This was tricker than first appeared since the enemies would still be able to alert to the player presense even after being killed, because the scripts were still updating. I fiddled around with disabling the scripts on the enemy's death and managed to get it working in the end. 

I also changed the camera from following the player to constantly moving forward at a certain speed, the speed of the camera will increase as the difficulty increases and I allowed for this in the code with a temporary difficulty value to be replaced when Liam implements the difficulty value with the score.