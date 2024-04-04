---
title: "Ammo Pickup C++ Reference"
date: "2022-09-03"
categories: 
  - "fps-core"
  - "fps-core-api-reference"
tags: 
  - "ammo-pickup"
  - "class-overview"
---

0.1.4

The most recent confirmed working version for this guide

### Overview

`AmmoPickup` provides a single, integrated class which handles updating the ammunition for the player character. It uses a map of structs in order to hold all the necessary weapon data within a single variable. It's built to use the `EAmmoType` enumerator defined in `WeaponBase.h`, so you only need to add ammo types in one place in order to effect all of FPS Core's systems.

* * *

### Variables

- `EAmmoAmount` - The enum holding all possible amounts of ammunition that each pickup can have

- `FAmmoTypeData` - The struct that details the data for each type of ammunition, which includes the meshes for full/empty states and the amount of ammunition each state should award the player with.

- `TMap<EAmmoType, FText> PickupName` - The map that correlates the pickup names to ammo types. **This is now deprecated, please set pickup names in `AmmoData`**

- `TMap<EAmmoType, FAmmoTypeData> AmmoData` - The map that keeps track of all the data for each ammunition pickup.

- `EAmmoAmount AmmoAmount` - The instance editable amount of ammo, used to determine the model and the amount of ammo to give the player

- `EAmmoType AmmoType` - The instance editable type of ammo, used to determine the model and the type of ammo to give the player

- `bool bInfinite` - Whether the ammo box is able to be emptied (single use) or is infinite and is able to be used an unlimited amount of times

- `bool IsEmpty` - Keeps track of the state of the ammo box

- `bool bDrawDebug` - Whether we should display debug messages or not

- `USoundBase* PickupSFX` - The sound effect played when the ammo box is picked up

* * *

### Functions

- `virtual void Interact() override;` - An override for the `Interact()` function found within [`SInteractInterface`](https://github.com/whoisEllie/isolation-game/wiki/SInteractInterface-class-overview). Within it we implement all the pickup logic required for this class.

- `virtual void OnConstruction(const FTransform& Transform) override;` - An override for the construction script. This is called every time a variable is changed, the asset is moved, etc., and allows you to preview the asset in the editor.

- `void SetEmptyMesh();` - A simple function that updates the mesh to it's empty variant and `bIsEmpty` to `true`

* * *

### Uses

`AmmoPickup` is a one-stop shop for any type of ammunition pickups. It handles visualisation in the editor through the use of construction script and integrates with `EAmmoType` in order to stay up to date with other changes in game design and function. All you need in order to use it is to fill out the map of models and variables that's editable when creating a child actor class in engine. After that, you can edit `AmmoAmount` and `AmmoType` in the editor and see the actor update in realtime.

<figure>

![Hnet-image](images/164740158-31dc8814-086e-4c42-81bf-2f1cc7b22d2c.gif)

<figcaption>

A demonstration of the in-editor realtime updates.

</figcaption>

</figure>
