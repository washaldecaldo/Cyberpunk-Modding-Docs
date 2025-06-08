---
description: >-
  How to add bulge detector support to dynamic Archive XL
---

# Dynamic Appearances: Add support for Bulge Detector

## Summary
This page is an extension of [ItemAdditions: Dynamic Appearances](./) and explains how to add Bulge Detector support.

## Before getting started

This guide assumes you already have a working Dynamic AXL garment. It will walk you through adding Bulge Detector support to your existing project. It also assumes you have two meshes -- one with a bulge and one without.

## From the Outside In

We will start from the yaml resource file and end with the mesh entity. 

### Yaml Resource File

The yaml file requires one change: `appearanceName` needs to be prepended with either `no_bulge` or `has_bulge`, whichever is the default in your mod. The shown examples will use `no_bulge` as default.

```yml
Items.wash_rrc_comfy_shorts_$(color):
  $base: Items.GenericLegClothing
  placementSlots:
    - !append OutfitSlots.LegsInner
  $instances: &ComfyUnderwearVariants
  entityName: wash_rrc_comfy_underwear_dynamic
  appearanceName: no_bulge_rrc_comfy_shorts_!$(color)
```

Remember: Only use `no_bulge` or `has_bulge`, not both. 

### Root entity file

In the root entity file, duplicate the appearance and add a prefix to each `name` so that you have both  `no_bulge` and `has_bulge` appearances. Leave `appearanceName` blank.

![image](https://github.com/user-attachments/assets/48fea6c9-fb11-4459-80f5-5d224e139c0e)

### App file

To make the Bulge Detector work, you must have two appearances with `componentOverrides`. The `componentOverrides` will define both the components for the bulge and no bulge appearances and set the chunkmask. You will likely need to add this from scratch.

In the app file, open the existing appearance.

Click on `partsOverride` in the left pane, then the yellow plus (+) symbol in the right pane to add a new element.
![image](https://github.com/user-attachments/assets/325882f1-acde-40e9-9d8b-45a7d2ac0c78)


Click into the [0] element and on `componentOverrides`. As before, click the yellow plus (+) symbol in the right pane to add a new element.
![image](https://github.com/user-attachments/assets/4b47698c-d868-4246-aa8b-5c634f7a2ff0)

Click into the new [0] `componentOverride` element, and give it the name you will use for the mesh entity; in this example, `l1_rrc_comfy_shorts_no_bulge`.
![image](https://github.com/user-attachments/assets/36253288-91c5-4378-8cec-41145283b309)



Duplicate the appearance and add a prefix to each `name` so that you have the same  `no_bulge` and `has_bulge` appearances that you defined in the root entity.
