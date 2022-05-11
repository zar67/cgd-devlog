---
layout: post
title: "Game Jam One Start - De-Make"
date: 2021-10-19 18:00:00 +0100
tags: jam-one assassins-creed 
---

### Brief

- De-make a modern, popular title so it could theoretically play on the Atari 2600.
- Can use any game engine to make the game.
- Needs to have visuals and controls that would be realistic on an Atari 2600.
- An arcade style game, with no saves, to be played in one session.

### Summary

Our group started off with a list of games that we could possibly de-make and narrowed it down to Assassin's Creed.

After some discussion on day one about the design of the game we decided on: A 2D platformer with a focus on climbing and stealth. 
The player plays as an assassin and tries to avoid the sight of guards to get through the platforms.
The player recieves score based on how far they get and how many guards they kill but loses points if they're seen by the guards.

We also broke up the game into the major features and tasks to split them between everyone in the group. Here's what we decided:

- Level Generation - Stan
- Guard AI - Matt
- Movement - Zoe
- Combat - Liam
- Sprites - Zoe
- UI - Zoe
- Score - Liam
- Sound - Stan
- Camera - Zoe

After the main session, I spent some time designing the movement for the character and designing a sprite:

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/character-run.gif" alt="Animated Character Run"/>
</p>

I designed the movement I wanted to create alonside some values for movement based on Celeste. I decided the player will be able to wall jump and hang from platforms as the two climbing abilities. I think this will give elements of Assassin's Creed's movement but on a simplified, 2D, scale. I brought my ideas to the group, and they agreed. 

After setting up the Unity project, I started working on the movement code. I setup a basic environment to test my movement in and added in my character sprite (without any animations yet).

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/test-movement-setup.png" alt="Basic Test Environment Setup"/>
</p>

By the end of the first couple of days I had the basic movement for the character setup (walking, jumping and crouching), meaning that it is easier for others in the group to test out their work.

Next, I implemented a wall jump where the player can slide down and jump off the wall. This ended up being quite tricky to do and ended up with the player jumping up to the ceiling on several occasions due to bugs in the code. Eventually I managed to smooth everything out and while the wall jumping could do with improvement in the future the basics are in for now. 

I also added idle and run animations to the player so that it looks much better when moving for the play test. The player character still looks a bit odd when sliding down a wall or crouching (as the player's head slides through the ceiling) but these animations will be improved in future.