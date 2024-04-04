---
title: "Adding your own rig to FPS Core"
date: "2022-11-17"
categories: 
  - "fps-core"
  - "fps-core-guides"
tags: 
  - "guides"
  - "rig"
---

0.1.4

The most recent confirmed working version for this guide

FPS Core was built to be flexible with the types of rigs that it accepts, but it has a few requirements for proper compatibility with all of FPS Core's features.

## Component Heirarchy

FPS Core builds its component hierarchy upon the SpringArmComponent. This lets us get the player's input and pass it on to the hands mesh and camera. Next, we have our HandsMesh. Some setups use the camera here, and it's really a matter of preference. FPS Core uses the hands so that it's easier to align the camera with the weapon, and it's easier to create animations that include movement of the camera bone. Finally, the camera is attached to a bone in the hands mesh.

I describe the architecture so that you can understand the functions that the rig has to provide in FPS Core in order to function properly with the rest of the systems. Really, there is only one fundamental requirement, and one recommended requirement for an FPS Core hand rig:

- **\[Required\]** A 'weapon' bone designed to attach a weapon to

- **\[Recommended\]** A camera bone designed to have a camera attached to it

## The Weapon Bone

A weapon bone is **required** in FPS Core, as weapons must be spawned attached to a certain bone on the player character. Weapons are always spawned and attached to the bone at (0,0,0). If you wish to adjust the location of weapons in-engine, it is easiest to add a socket to your weapon bone, attach your weapon to that, and then give that socket your desired location, rotation, and scale offset. You may choose to substitute your designated weapon bone for one of your character's hand bones. This is not advisable, as it does not allow you to create animations in which the player lets go of the weapon with both hands (not necessarily at the same time - imagine an animation where the player must swap the weapon from their right to their left hand in order to pull back the bolt after reloading) without an extreme amount of difficulty, both in your animation software of choice, and the game engine.

## The Camera Bone

A camera bone is not explicitly required - you can position your camera manually in your FPS Character blueprint, and you won't face any issues with the code in FPS Core. The reason this is recommended is that it makes it significantly easier to align your camera to your rig, reducing the hassle from attempting to get ADS animations to line up perfectly.

If you would like to use the FPS Core rig as a reference, you can download it below

[FPS-Core-Rig](https://emmadocs.dev/wp-content/uploads/2022/11/FPS-Core-Rig.zip)[Download](https://emmadocs.dev/wp-content/uploads/2022/11/FPS-Core-Rig.zip)
