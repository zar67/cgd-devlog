---
layout: post
title: "Game Jam Two Start - Random Generation"
date: 2021-11-23 18:00:00 +0100
tags: jam-two turn-based-cyborgs
---

# Brief
- Make a game based on the concept: "A turn based strategy where you colonise ruins with cyborgs."
- Focus on the micro, macro, meta mechanics of the game.

# Summary
We started this week getting our randomly generated theme for our game and spent the session coming up with a concept.

We decided on a 2 player turn based strategy where you have to take over all the other player's colonies to win and decided it would be a futuristic style look. The mechanis are:
Micro: Moving units on a hexagonal grid to gain territory and gain strategic advantage.
Macro: Colonising ruins, to build your empire and dominate other players.
Meta: Daily challenges that contribute to a global leaderboard that you get rewards for e.g. colonising x number of ruins.

We split the tasks up like so:
- Networking (Liam)
- World Generation (Zoe)
- Combat (Matt)
- Sprites (Zoe)
- Sound (Ed)
- Challenges (Stan)
- Leaderboard (Liam)
- UI (Ed)
- Turn Based Logic (Stan)
- Ruins Logic (Ed)
- Camera (Stan)

This week I got the randomly generated map up and running with terrain types and ruins generating. I also setup a pathfinding function to find paths between tiles. 

On Monday we met to consolidate our progress and decide the final things we wanted done before the play test, we decided we wanted to be able to play with 2 players and have them move around and attack eachother - essentially the core functionality of our game.

# Next Steps
- Fix World Generation Bugs