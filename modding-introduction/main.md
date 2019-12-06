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
    + [General](#general)
      - [Space Engineers ModSDK](#space-engineers-modsdk)
      - [Microsoft Visual Studio Community](#microsoft-visual-studio-community)
      - [Space Engineers Workshop Tool (SEWT)](#space-engineers-workshop-tool--sewt-)
    + [Scripting](#scripting-1)
    + [3D modelling](#3d-modelling-1)
      - [Blender](#blender)
      - [3Ds Max](#3ds-max)
      - [Eikester's MWM Builder (MwmB)](#eikester-s-mwm-builder--mwmb-)
      - [Havok Content Tools](#havok-content-tools)
      - [FBXImporter](#fbximporter)
      - [Balmung's Blender Plugin](#balmung-s-blender-plugin)
    + [Texture modding](#texture-modding-1)
      - [Gimp](#gimp)
      - [Adobe Photoshop](#adobe-photoshop)
      - [Gimp DDS Plugin](#gimp-dds-plugin)
      - [Intel Textureworks Plugin](#intel-textureworks-plugin)
      - [TexConv](#texconv)
    + [Audio modding](#audio-modding-1)
      - [Audacity](#audacity)
      - [Adobe Audition](#adobe-audition)
- [What now?](#what-now-)

***

* use examples
* pictures
* hyperlinks to more detail
* scripting: pb scripts
* update folder structure with tools MwmB etc. and texconv
* switch script example to something of digi's https://github.com/THDigi/SE-ModScript-Examples/tree/master/Data/Scripts/Examples/BasicExample_GameLogicAndSession
* possibly give alternative to VS
* link to discord for sure

## What can I mod?
As newcomers to modding a specific game, oftentimes people will not be aware of what can and cannot be modded in the first place. And what use are the greatest plans for a mod if the game developer has disallowed access to the key files needed to make those plans reality? This chapter will expand on the different "dimensions" of modding, which each require their own expertise and tools. Knowing about these different dimensions will allow you to better understand which are relevant for your plans, and which you'd be interested in learning.

### SBC modding
* mention which tools
SBC modding is the by far most universal form of modding. "SBC" refers to the file format that most files containing game data are saved in. They are easily readable and very simple to adjust. Most mods will contain SBC files and thus involve SBC modding, even if they primarily fall into one of the other dimensions of modding.

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

***

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

***

### Modding assets
This dimension includes all the shiny things - the things that make good screenshots and that look and sound cool in the game. While it doesn't require as much prior knowledge to produce usable results with, this dimension does instead oftentimes require a lot of different applications to produce content with. While the industry standard is generally very expensive, there are usually alternative applications available that can produce similar results for free - albiet they may require you to clear a couple additional hurdles in the process.

#### 3D modelling
3D modelling is not an easy skill to learn but there are many applications and much more tutorials available on the internet. 3D modelling is creating objects in SE. Be it blocks, tools, components or even player characters - they were all created in a 3D modelling application.

This is a screenshot of the user interface inside the application called "Blender", which is what you'll most likely be using to do your 3D modelling for SE.

![](./pictures/blender.png?raw=true "Blender")

As you can see, the colors aren't quite right and the model is not properly aligned but that is a Beacon block in there.

___

#### Texture modding
Textures are what give objects in games, and thus SE, color. They can be edited separately from 3D models and require a separate set of applications to mod. This is one of the easier disciplines and a pretty good point to start with should you want to look into modding the game's visuals.

Below is a screenshot of a texture within Adobe Photoshop. This is likely not what you'll be using as it's a paid application, but it still illustrates the setup fairly well.

![](./pictures/photoshop.png?raw=true "Adobe Photoshop")

The picture may look like the texture contains random shapes, but once these are applied to a 3D model, it will look very different.

___

#### Audio modding
Audio modding is often forgotten (to be honest, I nearly forgot it myself when writing this guide - even though I've done quite a bit of it) but is nevertheless an important aspect. Creating and editing sound effects requires another separate set of tools, but is fairly straightforward.

This is a screenshot of the application "Audacity". It's what you'll likely be using to edit and create sound effects for SE.

![](./pictures/audacity.png?raw=true "Audacity")

This particular project file contains multiple sound effects.

## Setting up a modding environment
Now that we've got an overview over the different dimensions of modding, the next step is to set up a folder structure to make modding easy and streamlined. While you can do modding in a more unorganized fashion perfectly well, structuring everything from the beginning will help you keep an overview and save you a lot of time in the long run.

### Folder structure
First off, you need to decide where on your PC you want to keep your modding files. This can be anywhere - on your main drive or any additional ones - as long as it has enough space. Once you have decided on a location, create a folder and name it something along the lines of `SE Modding`.

Now, download **[this file](https://drive.google.com/open?id=1hvbhJbYkfUP8KwGLcytOTs9YrMcZAejp)** and extract it into your new folder. It contains the various subfolders which will make up the structure of the modding folder. It should now look like this:
```
[Your SE Modding folder]\audio
[Your SE Modding folder]\models
[Your SE Modding folder]\render
[Your SE Modding folder]\scripts
[Your SE Modding folder]\textures
[Your SE Modding folder]\tools
[Your SE Modding folder]\tutorials
```
With many of them having additional subfolders within them.

This modding folder is your new sandbox. This is where you will work on many of the more complex files that go into your mod to then copy them into the individual mods' folders for testing and upload to the workshop. Now right-click on your SE Modding folder and click `Pin to Quick access`. This will add the folder to the folder tree on the left side of Windows Explorer like so:

![](./pictures/quickaccess.png?raw=true "Quick Access")

As you can see, in my case the folder is just named `SE`.

Next up is making getting to the relevant folders more convenient. Outside of this one, there are four locations that you will have to navigate to very frequently: Your Space Engineers game folder, the Space Engineers folder in AppData, the Space EngineersModSDK folder and finally the folder where Steam saves all downloaded Workshop mods to. We're going to make navigating to them easier by creating shortcuts to each:

1. Right-click into your SE Modding folder and go to `New --> Shortcut` in the context menu.
2. In the window that opens up, click `Browse` and browse to the location of your Space Engineers game installation. This is generally located in `C:\Program Files (x86)\Steam\steamapps\common\SpaceEngineers`. I'm going to assume that if you relocated the installation folder, you're able to find it again.
3. Click `Next` and name your shortcut `SpaceEngineers Game Folder`, then select `Finish`.

Now you are able to simply click on that shortcut to get to the Space Engineers installation folder. Then, after finding what you need in there you can simply select your SE Modding folder from the Quick access bar to go back.

Let's now do the same for the next shortcut: Create the shortcut, but then enter `%APPDATA%\SpaceEngineers` into the text field next to `Browse`. Name the shortcut `SpaceEngineers AppData`.

The ModSDK link we'll have to skip for now because you likely haven't installed that yet. We'll come back to creating the shortcut for that later.

Lastly, the link to the folder where Steam saves downloaded workshop mods to. This one is located in `C:\Program Files (x86)\Steam\steamapps\workshop\content\244850` by default. Adjust the link as needed and enter it into the text field next to `Browse`. Name the shortcut `Workshop Mods`.

Your folder should now look like this:

![](./pictures/moddingfolder.png?raw=true "SE Modding Folder")

Let's now take a quick tour through this folder to expand on why it is set up like it is.

* **audio** - This is where, you guessed it, audio modding is going to happen. The idea is to use the main folder, `\audio\`, to save your finished files into, while the `\audio\source\` folder holds various source sound files that you use to build the finished audio files. `\audio\projects\` is used to hold the "audio projects" file that audio editing applications usually save in by default. Using those projects allows you to go back into editing the same audio later without having to redo everything or somehow edit the previously finished file.

* **models** - This is where you'll be saving all your 3D model-related files. Within this main folder you'll be saving your "project" files such as `.blend` in the case of Blender usage, as well as any files needed to generate SE's 3D model format (`.mwm`). `models\reference\` is where I recommend placing any reference model files that you use to build your own 3D models with. Having them in one place makes them easy to access. `models\Textures\` and its subfolders is where we'll be placing SE texture files so that we can easily reference them within the 3D modelling application. This folder structure is important, because having the folders set up like this will ensure the game also knows where to find these texture files. `\models\utility` is where we'll place various files related to ease the creation of 3D models for SE.

* **render** - This folder is where we'll be saving 3D renders of our new models to. These renders are essential to creating the HUD / GUI icons of our new blocks, items, etc.

* **scripts** - This will be our working folder to create scripts for SE in. Not really much more to say here.

* **textures** - This is where we'll be working on our own textures (as opposed to `models\Textures\`, where we place SE's existing textures). In this folder we'll save both the finished texture files as well as the work-in-progress files to. `textures\reference\` is where you should save any reference images for your textures. Having them all in one place will make sorting through them for reference and general inspiration much easier.

* **tools** - This is the folder into which we're going to install and place various tools to handle SE files. We'll get back to this in a bit.

* **tutorials** - This folder is not strictly necessary but I do recommend it: If you find guides and tutorials for modding online, save them to this folder via shortcuts or printing them as PDF (or just mark them with bookmarks in your browser). The important part is to keep an overview over what is available and to make sure you can find it again later, should you need it.

***

### Required tools
With the folders set up, the next step is to expand on the tools that you'll be using for different parts of the modding process. At this point it'll also make sense for you to decide on what dimension you'll want to dive in. If you don't have any plans to do scripting, for example, don't bother with the tools listed for scripting. No matter which you choose, be sure to acquire all the tools listed under `General` though.

#### General
The following tools are used for pretty much any mod you want to put together. Hence it'll make sense for you to get them no matter which modding dimension you want to focus on.

##### Space Engineers ModSDK
The official Space Engineers ModSDK contains various tools and data that you'll need when working on your mods. There is no direct download link for it as you'll need to install it via Steam:

Go to your library, then at the top click on `Games` next to the search-field and select `Tools` from the dropdown menu. Then browse down to the entry named `Space Engineers  - Mod SDK` and install it. Once it's installed, create a shortcut to the folder it is located in and place it in your SE Modding folder. For easy access.

##### Microsoft Visual Studio Community
**[Download](https://visualstudio.microsoft.com/vs/)**

While you can edit `XML`-based files such as `SBC`s in pretty much any text editor, that's really just making things harder for yourself. Visual Studio offers the full package, for free. It will also serve as the application you'll do your scripting in, should you choose that route. Be sure to download the "Community" edition of the application via the dropdown menu, that's the free one.

##### Space Engineers Workshop Tool (SEWT)
**[Download](https://github.com/Gwindalmir/SEWorkshopTool/releases)**

While it may seem a little daunting and is not absolutely needed, I still heavily recommend getting this one. SEWT makes uploading and updating your mods very easy, provided we do a little setup beforehand. For now, download the latest release (click on `Assets` and download the `ZIP` file), then extract it into your `[Space Engineers Game folder]\Bin64\`-directory.

___

#### Scripting
* separate SDK thingy?
* PB SDK thingy
* VST

___

#### 3D modelling
If you're a student, you can get access to 3Ds Max for free. Even if you are though, you might prefer Blender as the vast majority of SE modders use it over 3Ds Max. There is better plugin support for it, so you can skip some steps when creating models for SE. Though the time saved is not large, it adds up over multiple models.

##### Blender
**[Download](https://store.steampowered.com/app/365670/)**

Blender is a free, open source 3D modelling application. While the industry standard is still 3Ds Max, it is gaining popularity quickly. Its interface takes some time to get used to, but there are thousands of tutorials available for Blender, so you'll have a lot of opportunities to learn the application's intricacies.

You can download and install Blender via Steam, but make sure you install the latest 2.79 version - not 2.8. Unfortunately the plugin necessary to work with SE has not been updated to the newest version.

##### 3Ds Max
**[Download](https://www.autodesk.com/education/free-software/3ds-max)**

3Ds Max is the industry standard in the games industry. It's a huge thing, incredibly complex and powerful but there are also countless tutorials available for it, some directly from within the application. If you're a student, you can get 3Ds Max for free via the above link, provided you use it non-commercially. Choosing this will mainly make sense if you have previous modelling knowledge in one of the Autodesk products. This application also requires a bit less setup compared to Blender, as it includes a lot of the needed functionality by default, whereas with Blender you'll have to install plugins for it.

##### Eikester's MWM Builder (MwmB)
**[Download](https://forum.keenswh.com/threads/mwmbuilder-fixes.7391806/)**

MwmB is the tool used to convert models you've created in your 3D application into the format used by the game. It is contained within the ModSDK, but Eikester maintains an improved version of the tool which provides more debug output to tell you if something went wrong - and what.

Download it and place the contents within the `[SE Modding folder]\tools\MwmB\`-directory. 

##### Havok Content Tools
**[Download 32bit](https://drive.google.com/file/d/0B5eyoHq4QGl3NUtDT0dwSTg5ZzQ/view) / [Download 64bit](https://drive.google.com/file/d/0B5eyoHq4QGl3N3ZnVnVtWkZ1bHM/view)**

The Havok Content Tools is what we need to use to create the collision models for our new 3D models. They contain a standalone application, but we'll mainly be using them from within Blender or 3Ds Max. Note that the Havok only supports fairly outdated 3Ds Max versions though (3Ds Max 2014 being the latest supported one).

Download the version corresponding with your operating system type and install it into the `[SE Modding folder]\tools\Havok\`-directory.

##### FBXImporter
**[Download](https://drive.google.com/file/d/1JIaMWpY4pLGrcuAiEbd2ZBBBt6W1vkEb/view)**

This plugin you will only require if you plan to use Blender. Blender does not support the `FBX` format out of the box, as such you will need to get this plugin to enable that.

Download and place the `.exe` into the `[SE Modding folder]\tools\`-directory.

##### Balmung's Blender Plugin
**[Download](https://github.com/hotohori/se-blender/releases/tag/0.9.1)**

This plugin is what makes creating models for SE with Blender much easier. It was originally created by Harag, but Balmung has forked it and maintains it. 

Download the `.zip` file and place it into the `[SE Modding folder]\tools\`-directory without unpacking it.
___

#### Texture modding
For texture modding the situation is a bit different from 3D modelling: While Gimp is the free option, it also involves more of a hassle in usage as Adobe Photoshop has much better support for the file formats involved. But there unfortunately isn't really a student version of Photoshop or something along those lines, and the subscription needed is fairly pricey.

##### Gimp
**[Download](https://www.gimp.org/downloads/)**

Gimp is free and open source. It doesn't have as much functionality as Photoshop out of the box, but there are countless plugins available for it that introduce this missing functionality. Gimp does not support `DDS` texture files in the compression that SE uses (`BC7`), so we'll have to rely on an external application to convert textures back and forth from DDS to a Gimp-readable format.

##### Adobe Photoshop

Adobe Photoshop is a solid but expensive choice. It doesn't support DDS import or export out of the box, but there's a plugin for it that enables that functionality. We're going to cover that a bit further down.

##### TexConv
**[Download](https://github.com/Mirzipan/TexConvGUI/blob/master/TexConvGUI/bin/x64/Release/TexConvGUI.exe)**

TexConv is needed to convert textures from the game format to a format usable by Gimp, 3DsMax and Blender. It is included within the ModSDK: Find it in the `SpaceEngineersModSDK\Tools\TexturePacking\Tools`-directory, and copy the `texconv.exe` into your `[SE Modding folder]\tools\TexConv\`-folder. Also download the above-linked `TexConvGUI.exe` - it offers a graphical user interface to work with texconv.exe - without it we'd have to work with command lines. You technically do not need this if you work with Photoshop only.

##### Intel Textureworks Plugin
**[Download](https://software.intel.com/en-us/articles/intel-texture-works-plugin)**

This is an official Intel plugin for Photoshop. It allows Photoshop to both import and export to the DDS format used by SE directly. Download and install it is you use Photoshop.
___

#### Audio modding
Audio modding doesn't really require any additional tools beyond the software to work with sound itself. While SE sound files used to use a specific format, the current version supports `.wav`, so it's very simple to work with.

##### Audacity
**[Download](https://www.audacityteam.org/)**

Audacity is a great, free program to work with sounds of all kind. I've used it for quite a while and it works perfectly well to create SE sounds, provided you know how to work the program itself of course.

##### Adobe Audition
Adobe Audition is the Adobe Creative Suite option for sound modding. Once again, it's paid, thus there will be less people that can use it, but it's also the superior option as a result of being paid. It contains much more functionality than Audacity, but for modding SE either works fine most of the time.

## What now?

* notes file
