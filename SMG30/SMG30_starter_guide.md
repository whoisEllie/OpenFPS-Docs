# SMG30 Starter Guide

Hi! Thanks so much for picking up the SMG30, and welcome to this starter guide! Here, you'll learn about the basic features of the SMG30 pack, how to use them, and where to learn how to make more advanced changes!

If you'd like, this tutorial is also available as a video, which you can find here: **TODO**.

# File Structure

Let's start out by getting a lay of the SMG30's file structure! When importing, you'll see two main directories, `FirstPersonHands` and `SMG-30`.

Let's discuss `FirstPersonHands` first. Here, you'll find the hands asset that ships with the SMG30. If you're just getting started with your project and are planning to use the SMG-30 as your base rig, you don't really need to touch anything in this folder. If you've got existing weapons, hands and animations and are aiming to use them alongside the SMG-30, you'll need to handle retargeting, which is covered in the [[SMG30_Retargeting_Guide]].

```
Content/FirstPersonHands
└── Character
    ├── Blueprints
    │   ├── ABP_FirstPersonHands_PostProcess.uasset
    │   ├── CR_FirstPersonHands.uasset
    │   ├── CR_FirstPersonHands_Procedural.uasset
    │   └── IKR_FirstPersonHands.uasset
    ├── Materials
    │   ├── Functions
    │   │   ├── CA_Mannequin.uasset
    │   │   ├── ChromaticCurve.uasset
    │   │   ├── MF_Diffraction.uasset
    │   │   ├── MF_logo3layers.uasset
    │   │   └── ML_BaseColorFallOff.uasset
    │   ├── Instances
    │   │   └── Manny
    │   │       ├── MI_Manny_01.uasset
    │   │       └── MI_Manny_02.uasset
    │   └── M_Mannequin.uasset
    ├── Mesh
    │   ├── FirstPersonHands.uasset
    │   ├── FirstPersonHands_PhysicsAsset.uasset
    │   └── FirstPersonHands_Skeleton.uasset
    └── Textures
        ├── Manny
        │   ├── T_Manny_01_ASAOPMASK_MSK.uasset
        │   ├── T_Manny_01_BN.uasset
        │   ├── T_Manny_01_CCRCCPlastic_MSK.uasset
        │   ├── T_Manny_01_D.uasset
        │   ├── T_Manny_01_MSR_MSK.uasset
        │   ├── T_Manny_01_N.uasset
        │   ├── T_Manny_01_Tan.uasset
        │   ├── T_Manny_02_ASAOPMASK_MSK.uasset
        │   ├── T_Manny_02_BN.uasset
        │   ├── T_Manny_02_CCRCCPlastic_MSK.uasset
        │   ├── T_Manny_02_D.uasset
        │   ├── T_Manny_02_MSR_MSK.uasset
        │   ├── T_Manny_02_N.uasset
        │   └── T_Manny_02_Tan.uasset
        └── Shared
            └── T_UE_Logo_M.uasset
```


The `SMG-30` directory is where you will find most of the assets you will actually want to be using on a daily basis, including the SMG-30 itself, it's animations and materials.

`SMG-30/Animations` is where you'll find all your animations! You'll notice that these are divided between the `Hands` and the `Weapon`, which denotes which of the two meshes the animation is designed to be played on. Usually, you'll only be playing an animation on the hands mesh, but there are exceptions - most notably reloading animations - which require you to play both the hand and weapon animations in sync. We'll go into more detail on this later on :)

In `SMG-30/Materials`, you'll find all the materials associated with the SMG-30. You likely want to use some of the material instances found inside the `SMG-30/Materials/Material_Instances/` directory, as opposed to the base materials that you'll spot first. These instances give you the flexibility to modify the materials without the worry of affecting every instance of that material in the world!

In `SMG-30/Mesh`, you'll find the SMG-30 mesh that you'll use to show off the weapon in game!

```
Content/SMG-30
├── Animations
│   ├── Hands
│   │   ├── BS_Walk.uasset
│   │   ├── BS_Walk_ADS.uasset
│   │   ├── SMG-30_ADS_Idle.uasset
│   │   ├── SMG-30_ADS_Walk_Backwards.uasset
│   │   ├── SMG-30_ADS_Walk_Forward.uasset
│   │   ├── SMG-30_ADS_Walk_Left.uasset
│   │   ├── SMG-30_ADS_Walk_Right.uasset
│   │   ├── SMG-30_Empty_Reload.uasset
│   │   ├── SMG-30_Empty_Reload_Montage.uasset
│   │   ├── SMG-30_Equip.uasset
│   │   ├── SMG-30_Equip_Montage.uasset
│   │   ├── SMG-30_Fire.uasset
│   │   ├── SMG-30_Idle.uasset
│   │   ├── SMG-30_Reload.uasset
│   │   ├── SMG-30_Reload_Montage.uasset
│   │   ├── SMG-30_Sprint.uasset
│   │   ├── SMG-30_Unequip.uasset
│   │   ├── SMG-30_Unequip_Montage.uasset
│   │   ├── SMG-30_Walk_Backwards.uasset
│   │   ├── SMG-30_Walk_Forward.uasset
│   │   ├── SMG-30_Walk_Left.uasset
│   │   └── SMG-30_Walk_Right.uasset
│   └── Weapon
│       ├── SMG-30_Gun_Empty_Fire.uasset
│       ├── SMG-30_Gun_Empty_Reload.uasset
│       ├── SMG-30_Gun_Fire.uasset
│       └── SMG-30_Gun_Reload.uasset
├── Materials
│   ├── M_SMG30_Base.uasset
│   ├── M_Sight_Base.uasset
│   └── Material_Instances
│       ├── MI_CrosshairSight.uasset
│       ├── MI_DotSight.uasset
│       ├── MI_HoloSight.uasset
│       ├── MI_SMG30_BareMetal_4k.uasset
│       ├── MI_SMG30_BareMetal_8k.uasset
│       ├── MI_SMG30_Dark_4k.uasset
│       ├── MI_SMG30_Dark_8k.uasset
│       ├── MI_SMG30_Industrial_4k.uasset
│       ├── MI_SMG30_Industrial_8k.uasset
│       ├── MI_SMG30_Light_4k.uasset
│       ├── MI_SMG30_Light_8k.uasset
│       ├── MI_SMG30_Wood_4k.uasset
│       ├── MI_SMG30_Wood_8k.uasset
│       └── MI_TriangleSight.uasset
├── Mesh
│   ├── SMG-30.uasset
│   ├── SMG-30_Physics.uasset
│   └── SMG-30_Skeleton.uasset
└── Textures
    ├── BareMetal
    │   ├── 4k
    │   │   ├── SMG30_BaseMetal_BaseColor_4k.uasset
    │   │   ├── SMG30_BaseMetal_Emissive_4k.uasset
    │   │   ├── SMG30_BaseMetal_Normal_4k.uasset
    │   │   └── SMG30_BaseMetal_OcclusionRoughnessMetallic_4k.uasset
    │   └── 8k
    │       ├── SMG30_BaseMetal_BaseColor_8k.uasset
    │       ├── SMG30_BaseMetal_Emissive_8k.uasset
    │       ├── SMG30_BaseMetal_Normal_8k.uasset
    │       └── SMG30_BaseMetal_OcclusionRoughnessMetallic_8k.uasset
    ├── Dark
    │   ├── 4k
    │   │   ├── SMG30_Dark_BaseColor_4k.uasset
    │   │   ├── SMG30_Dark_Emissive_4k.uasset
    │   │   ├── SMG30_Dark_Normal_4k.uasset
    │   │   └── SMG30_Dark_OcclusionRoughnessMetallic_4k.uasset
    │   └── 8k
    │       ├── SMG30_Dark_BaseColor_8k.uasset
    │       ├── SMG30_Dark_Emissive_8k.uasset
    │       ├── SMG30_Dark_Normal_8k.uasset
    │       └── SMG30_Dark_OcclusionRoughnessMetallic_8k.uasset
    ├── Industrial
    │   ├── 4k
    │   │   ├── SMG30_Industrial_BaseColor_4k.uasset
    │   │   ├── SMG30_Industrial_Emissive_4k.uasset
    │   │   ├── SMG30_Industrial_Normal_4k.uasset
    │   │   └── SMG30_Industrial_OcclusionRoughnessMetallic_4k.uasset
    │   └── 8k
    │       ├── SMG30_Industrial_BaseColor_8k.uasset
    │       ├── SMG30_Industrial_Emissive_8k.uasset
    │       ├── SMG30_Industrial_Normal_8k.uasset
    │       └── SMG30_Industrial_OcclusionRoughnessMetallic_8k.uasset
    ├── Light
    │   ├── 4k
    │   │   ├── SMG30_Light_BaseColor_4k.uasset
    │   │   ├── SMG30_Light_Emissive_4k.uasset
    │   │   ├── SMG30_Light_Normal_4k.uasset
    │   │   └── SMG30_Light_OcclusionRoughnessMetallic_4k.uasset
    │   └── 8k
    │       ├── SMG30_Light_BaseColor_8k.uasset
    │       ├── SMG30_Light_Emissive_8k.uasset
    │       ├── SMG30_Light_Normal_8k.uasset
    │       └── SMG30_Light_OcclusionRoughnessMetallic_8k.uasset
    ├── Sights
    │   ├── CrosshairSight.uasset
    │   ├── DotSight.uasset
    │   ├── HoloSight.uasset
    │   └── TriangleSight.uasset
    └── Wood
        ├── 4k
        │   ├── SMG30_Wood_BaseColor_4k.uasset
        │   ├── SMG30_Wood_Emissive_4k.uasset
        │   ├── SMG30_Wood_Normal_4k.uasset
        │   └── SMG30_Wood_OcclusionRoughnessMetallic_4k.uasset
        └── 8k
            ├── SMG30_Wood_BaseColor_8k.uasset
            ├── SMG30_Wood_Emissive_8k.uasset
            ├── SMG30_Wood_Normal_8k.uasset
            └── SMG30_Wood_OcclusionRoughnessMetallic_8k.uasset

24 directories, 89 files
```
