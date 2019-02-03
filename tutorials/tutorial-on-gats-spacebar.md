# Rat-A-Tat-Tat: A Tutorial On Gats
A tutorial on gatling guns.

You'll have 2 separate models for this.

Your base that doesn't move...

![alt text](/tutorials/images/gats-spacebar-1.png "Gatling Gun Example 1 By Spacebar")

...and your "barrels" that do.

![alt text](/tutorials/images/gats-spacebar-2.png "Gatling Gun Example 2 By Spacebar")

You can use different scenes for this; just make sure you name them something easy to remember.

So on the base you'll need an empty, named subpart_Barrel, where you want the spinning bits to be. Use the arrows empty because that determines which way your barrels point.

![alt text](/tutorials/images/gats-spacebar-3.png "Gatling Gun Example 3 By Spacebar")

The empty will need to link to your barrels file like this:

![alt text](/tutorials/images/gats-spacebar-4.png "Gatling Gun Example 4 By Spacebar")

Your barrel model may have to point the opposite direction of your base model for whatever stupid reason Keen does it.

On your barrel model, once you get it set up where you want it to spin, select all the meshes and apply location under ctrl+A. I find it easier to make your barrel mesh in the same scene as your base mesh, then copy/paste it to a new scene, then move your barrel mesh to another layer so you don't get double barrels.

On the barrel scene you'll need an muzzle_projectile empty, roughly where you want the bullets to come out, again using the arrows empty.

![alt text](/tutorials/images/gats-spacebar-5.png "Gatling Gun Example 5 By Spacebar")

![alt text](/tutorials/images/gats-spacebar-6.png "Gatling Gun Example 6 By Spacebar")

Then export both of your models to the same folder then you can start your data files setup.
