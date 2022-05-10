---
layout: post
title: "Win Conditions"
date: 2022-02-09 18:00:00 +0100
tags: cohort-project
---

This week I focused on getting the win conditions of the game working, I used Liam's game timer script and Ed's base ownership checking but merged them all together and got them all working correctly. The three win conditions of the game are as follows:

- A team reaches a score threshold, score is earned by owning bases.
- The timer for the game runs out, the team with the biggest score wins.
- A team owns all bases - and therefore wins by default.

These three are all now working correctly together, however nothing yet happens when the win condition is triggered except for the timer stops and the bases stop producing score. 

Finally this week I organised the folders of our scripts and modified Liam's defences to work together with the original defence structure I created, I removed assets that weren't needed and focused on simplifiying the code and the branches. 