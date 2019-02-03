# Emissives, A.K.A. Glowing Bits

Emissives, A.K.A. Glowing bits; there are 4 emissive names for materials. Use of these names (Emissive, Emissive1, Emissive2, Emissive3) results in these materials being colored by the 'EmissiveColors' data file entries. And for functional blocks, such as Reactors, Batteries, and Jump Drives, this is what handles those "charge levels" you see.

If you name a material these names, it will automatically by used by such blocks for their charge levels. However, the number of these emissives used varies by block, some use 3, some 4. As well, the colors vary, and can be changed by editing or creating new entries in the "EmissiveColors" data file, and then switching your block's emissive-set, which is defined in the end of the "CubeBlocks" entry.

Example, being a reactor with "Emissive" will glow red when disabled, and green when powered with default Emissive-settings, this 'color', is applied to the texture being used by the Material called "Emissive", as in if the material's texture(s) is, say, "White_CM", it will glow green perfectly. If it is say "BlackMetal", it will attempt to color the black texture Green. And fail miserably.

Emissives, do not use the "NG" or "ADD" texture slots in the Material - in fact, will crash or fail to function with said slots being used; it does not help.

Now for emissives that glow, but DO NOT care or are otherwise affected by the 'states' of the block, you simply take your material, name it anything but "Emissive", pick your "CM", and pick an "ADD" (and only an ADD, not an NG), that handles glows such as "Emissive_ADD" (this one however has lines in it), and your texture will glow.

You can make the color black glow, or any texture, if valid, generally glow with this. Key word is 'generally'.

## Emissives in a nutshell

![alt text](/tutorials/images/emissive-colors-example-kreeg.png "Emissive Colors Example By Kreeg")

For creating custom entries in the 'EmissiveColors' for use in the above.

The example is of a Jump Drive's "Extended" set, and a custom color.

A = Alpha, in these cases.
R = Red
B = Blue
G = Green.

Keen's only sane color system.

---

**Author:** Kreeg

**Editor:** cdrch
