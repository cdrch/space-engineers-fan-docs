# Modding Space Engineers - The Very Basics

This guide serves as a first introduction to modding in Space Engineers (SE). If you've never modded before, or never modded SE before, this is the place to start.

***

- [What can I mod?](#what-can-i-mod-)
  * [SBC modding](#sbc-modding)
  * [Scripting](#scripting)
    + [Visual Scripting](#visual-scripting)
  * [Modding assets](#modding-assets)
    + [3D modelling](#3d-modelling)
    + [Texture modding](#texture-modding)
    + [Audio modding](#audio-modding)
- [Setting up a modding environment](#setting-up-a-modding-environment)
  * [Folder structure](#folder-structure)
  * [Required tools](#required-tools)
- [Sample mod setup](#sample-mod-setup)
- [What now?](#what-now-)

***

* use examples
* pictures
* hyperlinks to more detail

## What can I mod?
As newcomers to modding a specific game, oftentimes people will not be aware of what can and cannot be modded in the first place. And what use are the greatest plans for a mod if the game developer has disallowed access to the key files needed to make those plans reality? This chapter will expand on the different "dimensions" of modding, which each require their own expertise and tools. Knowing about these different dimensions will allow you to better understand which are relevant for your plans, and which you'd be interested in learning.

### SBC modding
SBC modding is the by far most universal form of modding. "SBC" stands for the file format that most files containing game data are saved in. They are easily readable and very simple to adjust. Most mods will contain SBC files and thus involve SBC modding, even if they primarily fall into one of the other dimensions of modding.

What follows is an example of how the inside of an SBC file looks like. In this case, it's an excerpt of `Components.sbc`, which defines the `Steel Plate`-component.
```xml
    <Component>
      <Id>
        <TypeId>Component</TypeId>
        <SubtypeId>SteelPlate</SubtypeId>
      </Id>
      <DisplayName>DisplayName_Item_SteelPlate</DisplayName>
      <Icon>Textures\GUI\Icons\component\steel_plate_component.dds</Icon>
      <Size>
        <X>0.5</X>
        <Y>0.5</Y>
        <Z>0.01</Z>
      </Size>
      <Mass>20</Mass>
      <Volume>3</Volume>
      <Model>Models\Components\steel_plate_component.mwm</Model>
      <PhysicalMaterial>Metal</PhysicalMaterial>
      <MaxIntegrity>100</MaxIntegrity>
      <DropProbability>0.9</DropProbability>
      <Health>53</Health>
    </Component>
```
As you can see, the formatting is fairly straightforward and understandable. Of course there will be some - or many - things you don't yet understand, but it's fairly easy to keep an overview and once you know the different terms and what they mean, it's not hard to imagine this being easy to work with.

### Scripting
Scripting is what is used to implement new gameplay possibilities and functionality into the game. It is done in C# ("C sharp"), a fairly universal programming language that is used for many other things outside of scripting for SE. If you have prior knowledge of programming, this is a pretty good place to start. If you do not, you may want to reconsider starting with this dimension. Learning a programming language and the algorithms and logic to successfully create a script for SE is not something that can be learned in just a month or two. The good news is, however, that there are a lot of C# tutorials available for free online.

This is an example of how a script in SE looks like. It's an excerpt of a script used to control the color of the glowing parts on blocks.
```cs
public class Container : MyGameLogicComponent
    {
        IMyThrust m_block;

        private string EMISSIVE_MATERIAL_NAME = "Emissive";
        private Color GREEN = new Color(0, 255, 0);
        private Color RED = new Color(255, 0, 0);
        private Color lastColor;


        bool IsWorking
        {
            get
            {
                return m_block.IsWorking;
            }
        }

        public override void Init(MyObjectBuilder_EntityBase objectBuilder)
        {
            NeedsUpdate |= MyEntityUpdateEnum.EACH_10TH_FRAME;

            m_block = Entity as IMyThrust;
        }
```

#### Visual Scripting
Visual Scripting is a form of scripting that does not require the user to write actual code. The code is rather represented in the form of a network of nodes that are connected to each other. As a result, it's much more approachable for newbies, but the tool used to create these visual scripts - Visual Scripting Tool (VST) - is unfortunately still somewhat buggy. Furthermore, while it does not require the user to write actual code, knowledge of algorithms and the logic under which programs operate is still absolutely essential.

Below is a screenshot of the VST with a script loaded into it. You can see the different nodes represented in various colors with the lines connecting them together.
![](./pictures/vst.png?raw=true "VST")

### Modding assets
This dimension includes all the shiny things - the things that make good screenshots and that look and sound cool in the game. While it doesn't require as much prior knowledge to produce usable results with, this dimension does instead oftentimes require a lot of different applications to produce content with. While the industry standard is generally very expensive, there are usually alternative applications available that can produce similar results for free - albiet they may require you to clear a couple additional hurdles in the process.

#### 3D modelling
3D modelling is not an easy skill to learn but there are many applications and much more tutorials available on the internet. 3D modelling is creating objects in SE. Be it blocks, tools, components or even player characters - they were all created in a 3D modelling application.

This is a screenshot of the user interface inside the application called "Blender", which is what you'll most likely be using to do your 3D modelling for SE.
![](./pictures/blender.png?raw=true "Blender")
As you can see, the colors aren't quite right and the model is not properly aligned but that is a Beacon block in there.

#### Texture modding
Textures are what give objects in games, and thus SE, color. They can be edited separately from 3D models and require a separate set of applications to mod. This is one of the easier disciplines and a pretty good point to start with should you want to look into modding the game's visuals.

Below is a screenshot of a texture within Adobe Photoshop. This is likely not what you'll be using as it's a paid application, but it still illustrates the setup fairly well.
![](./pictures/photoshop.png?raw=true "Adobe Photoshop")
The picture may look like the texture contains random shapes, but once these are applied to a 3D model, it will look very different.

#### Audio modding
Audio modding is often forgotten (to be honest, I nearly forgot it myself when writing this guide - even though I've done quite a bit of it) but is nevertheless an important aspect. Creating and editing sound effects requires another separate set of tools, but is fairly straightforward. 

## Setting up a modding environment

### Folder structure

### Required tools

## Sample mod setup

## What now?