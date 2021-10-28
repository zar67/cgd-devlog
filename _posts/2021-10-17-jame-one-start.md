---
layout: post
title: "Game Jam One Start - De-Make"
date: 2021-10-17 18:00:00 +0100
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
The player scores based on how far they get and how many guards they kill but loses points if they're seen by the guards.

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

After the main session, I spent some time designing the movement for the character and designing a sprite for the character (simply reducing the resolution of one I found online).

Here's the initial sprite I came up with: 

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/character-run.gif" alt="Animated Character Run"/>
</p>

I came up with some metrics for the movement based on Celeste's character movement and jump and I also decided the two main climbing features to have in the game: wall jumping and hanging from platforms. I think this will give elements of Assassin's Creed's movement but on a simplified, 2D, scale. I brought my ideas to the group, and they agreed. 

After setting up the Unity project in the repository Liam created, I started working on the movement code. I setup a basic environment to test my movement in and added in my character sprite (without any animations yet).

<p align="center">
  <img src="{{site.baseurl}}/assets/jam-one/test-movement-setup.png" alt="Basic Test Environment Setup"/>
</p>

Setting up the movement was as simple as getting the input and applying a force based on speed and the input to the Rigidbody2D of the character. I also added a bit of smoothing to make the movement feel better.

{% highlight c# %}
  float move = m_movementInput * m_runSpeed * Time.deltaTime;
  Vector3 targetVelocity = new Vector2(move * 10f, m_rigidbody.velocity.y);
  m_rigidbody.velocity = Vector3.SmoothDamp(m_rigidbody.velocity, targetVelocity, ref m_velocity, m_movementSmoothingAmount);
{% endhighlight %}

I did encounter an issue with the basic movement where the player would sometimes get stuck in the middle of a platform and would have to be moved away and moved back again to continue. This was because the platforms are made of individual tiles each with their own collider. This meant the square collider of the player would get caught on the edges of the tiles. To fix this I simply added a composite collider to the tilemap so all the platforms had combined colliders instead of individual ones. 

Jumping was easily as simple, just adding a check for whether the player is grounded or not, then adding a vertical force to the Rigidbody when the jump input is given.

{% highlight c# %}
  m_isGrounded = Physics2D.OverlapCircle(m_groundCheck.position, GROUNDED_RADIUS, m_whatIsGround);

  if (m_jumpInput && m_isGrounded)
  {
    m_isGrounded = false;
    m_rigidbody.AddForce(new Vector2(0f, m_jumpForce));
  }
{% endhighlight %}

Hovever, I did improve the jump by adding a Mario style element - allowing the player to jump higher if they continue to press the jump input:

{% highlight c# %}
  if (m_rigidbody.velocity.y < 0)
  {
    m_rigidbody.velocity += Vector2.up * Physics2D.gravity * (m_fallMultiplier - 1) * Time.deltaTime;
  }
	else if (m_rigidbody.velocity.y > 0 && !m_jumpInput)
  {
    m_rigidbody.velocity += Vector2.up * Physics2D.gravity * (m_lowJumpMultiplier - 1) * Time.deltaTime;
  }
{% endhighlight %}

After the basic movement was setup, I moved on to the more complex movement elements, starting with crouching. The player needs to be able to crouch down to one unit high to be able to hide in hay etc, however if they are hiding under something and they can't stand up (e.g. the ceiling is too low) they need to stay crouching until they can stand up again. This is done by adding a Transform to use as a ceiling check point and using Physics2D.OverlapCircle to see if there is a ceiling above the player.

There are two colliders on the player, one covering the players head and upper body, one covering the lower body and legs. When crouching the top collider is disabled and eventually a crouching animation will be shown so the player is visually one unit tall.

{% highlight c# %}
private void UpdateCrouching(ref float movement)
{
  bool crouch = m_crouchingInput;

  // Crouch Check
  if (!m_crouchingInput)
  {
    if (Physics2D.OverlapCircle(m_ceilingCheck.position, CEILING_RADIUS, m_whatIsGround))
    {
      crouch = true;
    }
  }

  if (m_isGrounded || m_canAirControl)
  {
    if (crouch)
    {
      m_wasCrouching = true;
      movement *= m_crouchSpeedMultiplier;
      m_crouchCollider.enabled = false;
    }
    else
    {
      m_crouchCollider.enabled = true;
      m_wasCrouching = false;
    }
  }
}
{% endhighlight %}

I did come across some issues with the crouching where the player would become stuck in the collider of a platform when standing up underneath it, this was because I was setting the m_crouchInput variable directly in the crouch check, meaning it would be overridden by the input system. I simple fixed this by adding the crouch variable seen above to be temporarily created and update in the UpdateCrouch() function.

By the end of the first week of the Game Jam I have the basic movement for the character setup, meaning that it is easier for others in the group to test out their work. I still need to work on: complex movement (climbing), camera, UI and finding/making more sprites to use in the game. My aim for next week is to get the complex movement of climbing and wall jumping implemented, then I can begin to work on the other, smaller, tasks. 

### Next Steps
- Implementing wall jumping
- Implementing climbing
- Participate in group play test