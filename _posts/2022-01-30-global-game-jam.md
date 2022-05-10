---
layout: post
title: "Global Game Jam"
date: 2022-01-30 18:00:00 +0100
tags: jam-three 
---

For our third jam we participated in the Global Game Jam over a weekend, the theme was Duality and so we spent Friday evening discussing what we wanted the game to be. We decided on: a puzzle game with two dimensions, the player will need to switch between dimensions in order to find objects and solve the puzzle. 

I started by creating an empty project and then focused on getting a greyscale shader up and running which I had done by the end of Friday. I then focused on getting a script setup that could keep objects in a certain dimension, this was quite simple to do and just required turning the gameobject on and off on an event call:

```c#
public class DimensionalObject : MonoBehaviour
{
    [SerializeField] private bool m_inCreepyDimension = false;

    private void Awake()
    {
        DimensionSwitcher.OnDimensionSwitched += OnDimensionSwitched;
    }

    private void OnDimensionSwitched(bool inCreepyDimension)
    {
        gameObject.SetActive(m_inCreepyDimension == inCreepyDimension);
    }
}
```

I also setup logic so that the object the player is carrying would stay with the player when they switched dimensions. 

Finally I setup a level manager script to swtich between levels and begun setting up initial levels to teach the player how to play the game such as: get the key to the door, switches change dimensions, objects will appear/disappear when you switch dimensions etc.

The game was mostly complete by the end of Saturday and just needed some bug fixing and adding levels on Sunday. 

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-three/normal-dimension.png" alt="normal dimension"/>
</p> 

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-two/other-dimension.png" alt="Other dimension"/>
</p> 

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-two/complex-level.png" alt="Complex level"/>
</p> 

We presented our game at the end of the week and got good feedback.

# Improvements/Bugs

- Fixing player/camera bug that jitters player/camera.