# SMG30 Starter Guide

Hi! Thanks so much for picking up the SMG30, and welcome to this starter guide! Here, you'll learn about the basic features of the SMG30 pack, how to use them, and where to learn how to make more advanced changes!

If you'd like, this tutorial is also available as a video, which you can find here: https://youtu.be/E-lEGuygToE.
# File Structure

Let's start out by getting a lay of the SMG30's file structure! 
After importing the SMG-30, you'll find all the files within the `SMG_30_Weapon_Pack` folder! 

Inside, you'll find two folders: `Demo` and `SMG-30`.

`Demo` contains files that Epic considers not a part of the main product, and those used for demonstration. Inside, you'll find a set of FPS Hands, derived from those supplied with the [Unreal Engine Mannequins Pack](https://www.unrealengine.com/marketplace/en-US/product/mannequins-asset-pack). For the purpose of animation, these were re-rigged in Blender with the help of the [UEFY](https://www.rakiz.com/uefy/) plugin, then re-imported into Unreal Engine. You'll also find a demonstration map, which showcases all the textures and animations provided with the SMG-30.

Let's look at the `DemoMap` folder first:

```
DemoMap
├── BP_AnimationDemo
├── DemoMap
├── DemoMap_BuiltData
└── M_DemoMapFloor

1 directory, 4 files
```

As you can see from this overview, it's quite small, containing a simple blueprint (`BP_AnimationDemo`) which allows for the synchronised demonstration of weapon and hand animations, a material used for the floor of the demo map (`M_DemoMapFloor`), and the demo map itself (`DemoMap`, predictably). You may wish to open the map before getting started, as it will force Unreal to build shaders and such for a large amount of the assets included with this pack.

The `FirstPersonHands` folder is of a little more long term interest. Inside you'll find a set of meshes, textures, materials and blueprints that make the FPS hands tick, and allow for retargeting with other Epic-skeleton compatible assets.

```
FirstPersonHands
└── Character
    ├── Blueprints
    │   ├── ABP_FirstPersonHands_PostProcess
    │   ├── CR_FirstPersonHands
    │   ├── CR_FirstPersonHands_Procedural
    │   └── IKR_FirstPersonHands
    ├── Materials
    │   ├── Functions
    │   │   ├── CA_Mannequin
    │   │   ├── ChromaticCurve
    │   │   ├── MF_Diffraction
    │   │   ├── MF_logo3layers
    │   │   └── ML_BaseColorFallOff
    │   ├── Instances
    │   │   └── Manny
    │   │       ├── MI_Manny_01
    │   │       └── MI_Manny_02
    │   └── M_Mannequin
    ├── Mesh
    │   ├── FirstPersonHands
    │   ├── FirstPersonHands_PhysicsAsset
    │   └── FirstPersonHands_Skeleton
    └── Textures
        ├── Manny
        │   ├── T_Manny_01_ASAOPMASK_MSK
        │   ├── T_Manny_01_BN
        │   ├── T_Manny_01_CCRCCPlastic_MSK
        │   ├── T_Manny_01_D
        │   ├── T_Manny_01_MSR_MSK
        │   ├── T_Manny_01_N
        │   ├── T_Manny_01_Tan
        │   ├── T_Manny_02_ASAOPMASK_MSK
        │   ├── T_Manny_02_BN
        │   ├── T_Manny_02_CCRCCPlastic_MSK
        │   ├── T_Manny_02_D
        │   ├── T_Manny_02_MSR_MSK
        │   ├── T_Manny_02_N
        │   └── T_Manny_02_Tan
        └── Shared
            └── T_UE_Logo_M

11 directories, 30 files
```

Unless you're retargeting or going in to change the materials of the hands, you shouldn't need to look in here. If you *are* retargeting , you'll find the dedicated [[SMG-30 Retargeting Guide]] more helpful, and I'll direct you there.

With the `Demo` folder out of the way, let's get to the actual meat of the pack - the SMG-30 itself. You'll find all the relevant assets, predictably, in the `SMG-30` folder.

```
SMG-30
├── Animations
├── Materials
├── Mesh
└── Textures

4 directories
```

Let's start with the `Animations` subfolder:

```
Animations
├── Hands
│   ├── AM_SMG-30_Empty_Reload.uasset
│   ├── AM_SMG-30_Equip.uasset
│   ├── AM_SMG-30_Reload_Montage.uasset
│   ├── AM_SMG-30_Unequip.uasset
│   ├── AS_SMG-30_ADS_Idle.uasset
│   ├── AS_SMG-30_ADS_Walk_Backwards.uasset
│   ├── AS_SMG-30_ADS_Walk_Forward.uasset
│   ├── AS_SMG-30_ADS_Walk_Left.uasset
│   ├── AS_SMG-30_ADS_Walk_Right.uasset
│   ├── AS_SMG-30_Chamber.uasset
│   ├── AS_SMG-30_Empty_Reload.uasset
│   ├── AS_SMG-30_Equip.uasset
│   ├── AS_SMG-30_Fire.uasset
│   ├── AS_SMG-30_Idle.uasset
│   ├── AS_SMG-30_Reload.uasset
│   ├── AS_SMG-30_Sprint.uasset
│   ├── AS_SMG-30_Unequip.uasset
│   ├── AS_SMG-30_Walk_Backwards.uasset
│   ├── AS_SMG-30_Walk_Forward.uasset
│   ├── AS_SMG-30_Walk_Left.uasset
│   ├── AS_SMG-30_Walk_Right.uasset
│   ├── BS_Walk.uasset
│   └── BS_Walk_ADS.uasset
└── Weapon
    ├── AS_SMG-30_Gun_Chamber.uasset
    ├── AS_SMG-30_Gun_Empty_Fire.uasset
    ├── AS_SMG-30_Gun_Empty_Reload.uasset
    ├── AS_SMG-30_Gun_Fire.uasset
    └── AS_SMG-30_Gun_Reload.uasset

3 directories, 28 files
```

`Animations` is where, predictably, you'll find all your animations! You'll notice that these are divided between the `Hands` and the `Weapon`, which denotes which of the two meshes the animation is designed to be played on. Usually, you'll only be playing an animation on the hands mesh, but there are exceptions - most notably reloading animations - which require you to play both the hand and weapon animations in sync. In this case, you're best off playing the animations simultaneously in order to ensure that they sync up properly and look correct.

`Materials` next:

```
Materials
├── M_SMG30_Base.uasset
├── M_Sight_Base.uasset
└── Material_Instances
    ├── MI_CrosshairSight.uasset
    ├── MI_DotSight.uasset
    ├── MI_HolographicSight.uasset
    ├── MI_SMG30_BareMetal_4k.uasset
    ├── MI_SMG30_BareMetal_8k.uasset
    ├── MI_SMG30_Dark_4k.uasset
    ├── MI_SMG30_Dark_8k.uasset
    ├── MI_SMG30_Industrial_4k.uasset
    ├── MI_SMG30_Industrial_8k.uasset
    ├── MI_SMG30_Light_4k.uasset
    ├── MI_SMG30_Light_8k.uasset
    ├── MI_SMG30_Wood_4k.uasset
    ├── MI_SMG30_Wood_8k.uasset
    └── MI_TriangleSight.uasset

2 directories, 16 files
```

In `Materials`, you'll find all the materials associated with the SMG-30. You'll notice that most of the files are found in the `Material_Instances` folder. These are, logically, the material instances of the base materials, `M_SMG30_Base` and `M_Sight_Base`. Here, you'll find all the materials used both for the sights and the SMG-30 itself. For the SMG-30, you get the option to select either a 4k or 8k texture set. Whichever you choose, it may be worth deleting the textures for the one you're *not* using, as these texture sets use up a lot of space.

If you're going to be creating your own materials (or importing ones such as those provided with the [supporter texture pack](https://ko-fi.com/s/c2e4c23a8a)), I would recommend using the provided base materials and making material instances off of them - use the existing material instances as inspiration! If you're still having issues, don't hesitate to ask for help in the [discord server]( https://discord.gg/MzxdZd2WqR).

The `Mesh` folder is super straightforward!

```
Mesh
├── PA_SMG-30.uasset
├── SKEL_SMG-30.uasset
└── SK_SMG-30.uasset

1 directory, 3 files
```

Inside, you'll find the SMG-30 mesh that you'll use to show off the weapon in game, alongside it's skeleton and physics asset :)

The `Textures` folder is not quite as important in your day-to-day usability of the SMG-30, but let's take an overview anyways.

```
Textures
├── BareMetal
│   ├── 4k
│   │   ├── T_SMG30_BaseMetal_BaseColor_4k.uasset
│   │   ├── T_SMG30_BaseMetal_Emissive_4k.uasset
│   │   ├── T_SMG30_BaseMetal_Normal_4k.uasset
│   │   └── T_SMG30_BaseMetal_OcclusionRoughnessMetallic_4k.uasset
│   └── 8k
│       ├── T_SMG30_BaseMetal_BaseColor_8k.uasset
│       ├── T_SMG30_BaseMetal_Emissive_8k.uasset
│       ├── T_SMG30_BaseMetal_Normal_8k.uasset
│       └── T_SMG30_BaseMetal_OcclusionRoughnessMetallic_8k.uasset
├── Dark
│   ├── 4k
│   │   ├── T_SMG30_Dark_BaseColor_4k.uasset
│   │   ├── T_SMG30_Dark_Emissive_4k.uasset
│   │   ├── T_SMG30_Dark_Normal_4k.uasset
│   │   └── T_SMG30_Dark_OcclusionRoughnessMetallic_4k.uasset
│   └── 8k
│       ├── T_SMG30_Dark_BaseColor_8k.uasset
│       ├── T_SMG30_Dark_Emissive_8k.uasset
│       ├── T_SMG30_Dark_Normal_8k.uasset
│       └── T_SMG30_Dark_OcclusionRoughnessMetallic_8k.uasset
├── Industrial
│   ├── 4k
│   │   ├── T_SMG30_Industrial_BaseColor_4k.uasset
│   │   ├── T_SMG30_Industrial_Emissive_4k.uasset
│   │   ├── T_SMG30_Industrial_Normal_4k.uasset
│   │   └── T_SMG30_Industrial_OcclusionRoughnessMetallic_4k.uasset
│   └── 8k
│       ├── T_SMG30_Industrial_BaseColor_8k.uasset
│       ├── T_SMG30_Industrial_Emissive_8k.uasset
│       ├── T_SMG30_Industrial_Normal_8k.uasset
│       └── T_SMG30_Industrial_OcclusionRoughnessMetallic_8k.uasset
├── Light
│   ├── 4k
│   │   ├── T_SMG30_Light_BaseColor_4k.uasset
│   │   ├── T_SMG30_Light_Emissive_4k.uasset
│   │   ├── T_SMG30_Light_Normal_4k.uasset
│   │   └── T_SMG30_Light_OcclusionRoughnessMetallic_4k.uasset
│   └── 8k
│       ├── T_SMG30_Light_BaseColor_8k.uasset
│       ├── T_SMG30_Light_Emissive_8k.uasset
│       ├── T_SMG30_Light_Normal_8k.uasset
│       └── T_SMG30_Light_OcclusionRoughnessMetallic_8k.uasset
├── Sights
│   ├── T_CrosshairSight.uasset
│   ├── T_DotSight.uasset
│   ├── T_HolographicSight.uasset
│   └── T_TriangleSight.uasset
└── Wood
    ├── 4k
    │   ├── T_SMG30_Wood_BaseColor_4k.uasset
    │   ├── T_SMG30_Wood_Emissive_4k.uasset
    │   ├── T_SMG30_Wood_Normal_4k.uasset
    │   └── T_SMG30_Wood_OcclusionRoughnessMetallic_4k.uasset
    └── 8k
        ├── T_SMG30_Wood_BaseColor_8k.uasset
        ├── T_SMG30_Wood_Emissive_8k.uasset
        ├── T_SMG30_Wood_Normal_8k.uasset
        └── T_SMG30_Wood_OcclusionRoughnessMetallic_8k.uasset

17 directories, 44 files
```

Inside, you'll predictably find all the textures used by the SMG-30, which include the 4k and 8k PBR maps for all 5 of the materials included with the asset, as well as the 4 alpha masks used to power the sights! The only time you really need to look in here is if you're wanting to organise textures that you're using with the SMG-30, such as alternative sight pictures for example.

# Getting started

So, you've downloaded the SMG-30, where do you begin?

For this guide, I'll be assuming a default FPS template, just because this makes things a lot simpler to reproduce if you're starting a project for the first time, and for those of you using the SMG-30 in a custom project, this should give you a good idea of what direction to take. If you're using [FPS Core](https://www.unrealengine.com/marketplace/en-US/product/1e2dd9aadb6f46db9a42a201177d4cdd), you can follow the dedicated [[FPS Core setup guide]].

## Setting up the player character correctly

For our animations to work correctly, we need to set up the player character correctly.

Let's head to our player character, which you can find in `Content -> FirstPerson -> Blueprints`.

![](Screenshot%202024-02-16%20at%2017.16.44.png)

Firstly, we need to add a new skeletal mesh for the SMG-30 to use. To do this, let's first select the `FirstPersonMesh`, or whatever you're calling your hands mesh.

![](Screenshot%202024-02-16%20at%2017.52.28.png)

Then, we can add a new component, which will be a Skeletal Mesh Component. In my case, I'll name it `SMG-30` for clarity.

![](Screenshot%202024-02-16%20at%2017.52.48.png)

With this added, we need two more things to complete the basic setup required for our animations to appear correctly: Setting our weapon and our attachment socket. By setting the correct attachment socket, we can ensure that the weapon motion in the animations. To do this, simply go over to the `parent socket` property of our skeletal mesh and set it to `ik_hand_gun`.

![](Screenshot%202024-02-16%20at%2017.53.59.png)
![](Screenshot%202024-02-16%20at%2017.53.10.png)

Finally, we can set our mesh to be our SMG-30. To do so, just go down to the `Skeletal Mesh Asset` and select the `SK_SMG-30`.

![](Screenshot%202024-02-16%20at%2017.54.20.png)

You can now play any of the animations supplied with the SMG-30!