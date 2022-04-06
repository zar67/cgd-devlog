---
layout: post
title: "Alpha"
date: 2022-02-23 18:00:00 +0100
tags: cohort-project
---

# Summary

This week we presented the Alpha. But the morning of we realised that one of the teams had cause the project to break in the develop branch. The networking team did a great job at fixing this while we had our reps meeting and talked about what everyone had done and what the next steps were. We finally managed to show off the alpha but due to the late minute development and fixing, there wasn't a lot to show that was working together. 

This week I mainly focused on fixing some of the bugs that occured in the play test. The first one was that the UI for base interaction (defences and units) wasn't working correctly over the network, this was fixed easily by adding if is local player statements to the UI. 

Next I took on the task to give players teams and get them spawning at their correct bases. This was pretty simple to do but allows the functionality of the bases to work as intended without having team names being empty strings or manually setting the team names of the players. 

Finally this week I added in some lasers into the bases that change colour based upon the team that owns it and wether it's being contested. Currently these are just a massive cylinder but in future I think they should be a shader or a particle system instead as they will most likely look better when being flown around by the players.