---
layout: post
title: "Base Capturing"
date: 2022-02-02 18:00:00 +0100
tags: cohort-project
---

This week I started adding in a structure for the base caputuring logic which works as follows:

<p align="center">
  <img src="{{site.baseurl}}/assets/cohort-project/base-states.png" alt="Base States"/>
</p> 

I set this up with a capture trigger collider which detects objects with an Entity script entering and exiting the zone.

I also setup a structure for the defences, where bases have certain defence locations that players can be interacted with to build and repair defences. Finally I added in some UI to display this for Matt to easily hookup with his defence creation.