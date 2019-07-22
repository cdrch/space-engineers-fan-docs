# Modding Space Engineers - The Very Basics

This guide serves as a first introduction to modding in Space Engineers (SE). If you've never modded before, or never modded SE before, this is the place to start.

***

- [What can I mod?](#what-can-i-mod-)
  * [SBC modding](#sbc-modding)
  * [Scripting](#scripting)
  * [3D models and textures](#3d-models-and-textures)
- [Setting up a modding environment](#setting-up-a-modding-environment)
  * [Folder structure](#folder-structure)
  * [Required tools](#required-tools)

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

### Modding assets

#### 3D modelling

#### Texture modding

#### Audio modding

## Setting up a modding environment

### Folder structure

### Required tools

## Sample mod setup

## What now?