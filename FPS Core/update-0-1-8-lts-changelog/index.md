---
title: "Update 0.1.8 LTS Changelog"
date: "2023-04-21"
categories: 
  - "updates"
  - "fps-core"
tags: 
  - "0-1-8-lts"
  - "update-2"
---

While FPS Core v2 is in development, I'll be pushing updates via the LTS branch on GitHub, which will provide extended support for v0.1.X with bug fixes and minor features. Unlike previous changelogs, which described new changes and migration guides in more detail, and were separate per update, this changelog functions as an aggregate for all changes made to 0.1.8 LTS, datemarked by the time they went live on the marketplace. All changes are **non-breaking**, so you shouldn't hesitate to update when one appears.

* * *

### 20th April 2023

- Fixed a bug that caused recoil to repeat the first-shot value for all shots

- Fixed a bug that caused the half-height of the capsule to not be set properly, defaulting to 88

- Exposed additional `InventoryComponent` functions to Blueprints

* * *

### 10th May 2023

- Fixed a bug that caused muzzle particles to spawn oriented toward the centre of the map

- Added the `GunFired()` function to allow custom code to be run on each shot

- Added the ability to toggle automatic reloads when you run out of ammo, and to automatically start firing after reloading if the firing button is still being held down

- Added a 'Last Shot' animation that plays on the weapon only if it is the last shot in the magazine

* * *

### 7th July 2023

- Added the ability to select whether ADS is possible for each movement state

- Added the `StartReload()` and `FinishReload()` blueprint implementable functions to allow custom code to be executed at these moments

- Added support for ADS-specific firing animations
