---
layout: post
title: "Game Jam One - Main Features Complete"
date: 2021-11-02 18:00:00 +0100
tags: jam-one assassins-creed 
---

During the play test this week with Andy we received the following feedback:
- Hay Bales would be good to push the Assassin's Creed IP a bit more.
- Generally, the game is looking good.
- There should be some death animations and effects.
- We need to discuss and think about flow/difficulty, how the player will be kept interested and just on the edge of failure.

After the play test we discussed as a group what we needed to do next and also discussed our ideas for difficulty. We concluded that the difficulty would increase at certain score thresholds the player reached and that the following things would be influenced by the difficulty:
- The speed of the camera movement (changing the camera to a static, constantly moving one)
- The amount of AI that spawn within a section.
- The speed of the enemy movement.
- How far the enemy can see.

The first thing I went about implementing was the death animations, both for the player and the enemies. This was tricker than expected since the enemies would still be able to alert to the player presence even after being killed, because the scripts were still updating. I fiddled around with disabling the scripts on the enemy's death and managed to get it working in the end. 

I also changed the camera from following the player to constantly moving forward at a certain speed, the speed of the camera will increase as the difficulty increases and I allowed for this in the code with a temporary difficulty value to be replaced when the difficulty value is implemented.

I added a tutorial section where the player can learn the mechanics of the game. This will always appear at the start of the game for the player to learn how to move, jump, climb, attack etc.

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/tutorial-section.png" alt="Tutorial Section"/>
</p> 

Finally, this week I worked on some minor improvements and polish. I improved the climbing up so that the player can jump up from a platform rather than just climbing down. I also setup the crouch animation to work when the player is in a pile of hay to improve how it looks.