---
layout: post
title: "First Play Test"
date: 2021-10-20 18:00:00 +0100
tags: jam-one assassins-creed play-test
---

In the start of the second week I implemented a wall jump where the player can slide down and jump off the wall. To do this I have a boolean value called m_canGrabWall which determines if the player is close enough to a wall to 'grab', this is calculated by an OverlapCircle check with a transform placed at the front of the player. If a player can grab a wall and is moving into the wall they will 'grab' it, sliding down the wall at a reduced fall speed. When grabbing a wall the player can use the jump key to launch off the wall away from it, this temporarily removes control from the player to make sure they get far enough away from the wall before control is regained.

{% highlight c# %}
if (m_isGrabbingWall)
{
    m_rigidbody.gravityScale = m_defaultGravityScale * m_wallGrabbingGravityMultiplier;
    m_rigidbody.velocity = Vector2.zero;

    if (m_jumpInput && m_jumpInputPressedThisFrame)
    {
        m_wallJumpTimer = m_wallJumpDuration;
        m_rigidbody.AddForce(new Vector2(-(m_movementInput * m_jumpForce), m_jumpForce * m_wallJumpHeightMultiplier));
        Flip();

        m_rigidbody.gravityScale = m_defaultGravityScale;
        m_isGrabbingWall = false;
        m_canControl = false;
    }
}

{% endhighlight %}

This ended up being quite tricky to do and ended up with the player jumping up to the ceiling on several occasions due to bugs in the code. Eventually I managed to smooth everything out and while the wall jumping could do with improvement in the future the basics are in for now. 

I also added idle and run animations to the player so that it looks much better when moving for the play test. The player character still looks a bit odd when sliding down a wall or crouching (as the player's head slides through the ceiling) but these animations will be improved in future.

After this we had our first group meeting/play test where I got to see Matt's AI work as well as Liam's combat work and Stan's procedural generation work. We discussed next steps and decided we would need to merge all our work together soon, especially the Combat and AI. We also shuffled some work tasks around as some of the more complicated tasks turned out to be easier than expected such as the combat.

We also decided that everyone would make at least one section for the procedural level generation to instantiate so that we have a range of sections to be displayed when playing the game.

After the play test I started work on the character climbing. I began by looking at the PlatformEffector2D which seemed to be popular through the variety of tutorials I watched. However, this doesn't provide the full functionality that I want to implement, it doesn't include hanging off a platform for example. 

I use the PlatformEffect2D component to easily implement the ability to jump up from underneath the platform but use extra code in the player movement script to handle hanging off a platform and climbing. To do this I added another collider to the player which is always disabled except for when the player is hanging, it is used to keep the player in the right position for hanging rather than falling down.

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/hanging-collider.png" alt="Basic Test Environment Setup"/>
</p>

When the player pressed the climb keys (either W and S on the keyboard, or up and down on the joystick) the player climbs in the related direction to either hang, climb up or drop down. 

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

At the end of the week, I created some more animations for the player so that it looks better when moving about the environment. This included a crouching animation, a wall sliding animation as well as a hanging animation.

### Next Steps
- Fix climbing bugs 
- Create more player animations
- Create level sections
- Integrate everyone's work together into a working game loop