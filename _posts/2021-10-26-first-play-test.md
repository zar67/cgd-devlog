---
layout: post
title: "Game Jam One - First Play Test"
date: 2021-10-26 18:00:00 +0100
tags: jam-one assassins-creed play-test
---

At the start of week two we had our first group meeting / play test. We discussed next steps and decided we would need to merge all our work together soon, especially the Combat and AI. We also shuffled some work tasks around as some of the more complicated tasks turned out to be easier than expected such as the combat.

We also decided that everyone would make at least one section for the procedural level generation so that we have a range of sections to be displayed when playing the game.

After the play test I started work on the character climbing. I began by looking at the PlatformEffector2D which seemed to be a popular method. However, this doesn't provide the full functionality that I want to implement, it doesn't include hanging off a platform for example. 

I use the PlatformEffect2D component to easily implement the ability to jump up from underneath the platform but use extra code in the player movement script to handle hanging off a platform and climbing. To do this I added another collider to the player which is always disabled except for when the player is hanging, it is used to keep the player in the right position for hanging rather than falling down.

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/hanging-collider.png" alt="Basic Test Environment Setup"/>
</p>

When the player presses the climb keys (either W and S on the keyboard, or up and down on the joystick) the player climbs in the related direction to either hang, climb up or drop down. 

To handle the collisions properly, and make sure no other objects are affected by the hanging of the player, I disable the collisions between the player and the platform collider when the player is hanging.

{% highlight c# %}
private void SetCollidersForHanging(bool hanging)
{
    Physics2D.IgnoreCollision(m_mainCollider, m_platformHangingOn, hanging);
    Physics2D.IgnoreCollision(m_crouchCollider, m_platformHangingOn, hanging);

    m_hangingCollider.enabled = hanging;
}
{% endhighlight %}

The main advantage for doing this is that no other objects will be affected by disabling the colliders, for example when an enemy walks over the platform while a player is hanging, the enemy won't be able to fall through the platform.

One remaining issue with the climbing is that if the player doesn't jump high enough, they may become stuck halfway up the platform, this is due to the Platformeffector2D and the 2 separate colliders on the player (one main collider and one collider disabled when crouching). This is a bug I need to work on and fix, my initial thoughts are to have one collider instead and change the size of it when crouching, but this will be worked on at a later stage.

This week I also created some more animations for the player including a crouching animation, a wall sliding animation and a hanging animation.

At the end of the week, I fixed the bug with climbing where the player gets stuck. As suggested earlier this was because of the two colliders on the player. I fixed this by removing the crouch collider and changing the height of the main collider when the player crouches, this fixed the issue quite nicely. 

I also added in some environment sprites so that there weren’t white cubes everywhere anymore. I made a simple brick texture as well as a wooden platform texture for the hanging platforms. This is what they look like:
 
<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/environment-sprites.png" alt="Environment Sprites"/>
</p>

The final task I completed was merging all of the groups work together so that we had a complete game loop to show off. I made some fixes to the UI and merged in all the branches together (on a test branch). I created a Game Scene and added all the relevant scenes to the build settings. With some minor bug fixes, I had a working game loop that was a culmination of all the work the group has done so far.

The final thing I did before this week’s meeting was create a world section and a better starting section to give some variety as we play and show off the game. The new section also gave the ability to show off the AI and the movement fully.