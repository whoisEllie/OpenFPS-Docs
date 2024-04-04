---
title: "Ammo Pickup BP Reference"
date: "2022-11-07"
categories: 
  - "fps-core"
  - "fps-core-api-reference"
tags: 
  - "api-reference"
---

0.1.4

The most recent confirmed working version for this guide

### Overview

`AmmoPickup` does exactly what it says on the tin - it provides a flexible ammo pickup class which handles updating the ammunition in the player character. It's designed to be very plug-and-play, and only requires setting up a single map of structs in order to handle all the interactions. It's also designed to be dynamic, so you can easily set this up to handle as many or as few ammunition pickup types and ammo amounts as you wish.

* * *

### Variables

- `Pickup Name` - Used to set the display name for each ammo type. **Deprecated since 0.1.4, please use `Ammo Data`.**

- `Ammo Data` - The main variable in control of `AmmoPickup`. This is where we set details such as the meshes to use, how much ammo they add, and their display name.

- `Draw Debug` - Whether to print debug statements whenever ammunition is picked up.

- `Pickup SFX` - The sound to play when ammunition is collected

* * *

### Functions

`Ammo Pickup` does not contain any user-implementable functions.

* * *

### Uses

`AmmoPickup` is a one-stop shop for any type of ammunition pickups. It handles visualisation in the editor through the use of construction script and integrates with `EAmmoType` in order to stay up to date with other changes in game design and function. All you need in order to use it is to fill out the map of models and variables that's editable when creating a child actor class in engine. After that, you can edit `AmmoAmount` and `AmmoType` in the editor and see the actor update in realtime.

<figure>

![Hnet-image](images/164740158-31dc8814-086e-4c42-81bf-2f1cc7b22d2c.gif)

<figcaption>

A demonstration of the in-editor realtime updates.

</figcaption>

</figure>
