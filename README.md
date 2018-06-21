# Urho3D Lightmap
  
---
### Description
Lightmap generator for Urho3D based on **Hugo Elias's Radiosity**. Unlike typical Hugo's implementations that you encounter, this implementation is simplified and uses brute force pixel processing method and uses hemisphere instead of hemicube.
Indirect lighting process is **blazing fast** using Urho3D's tech., and the default scene completes in **~5 sec.**

#### Generates Textures:
* lightmap - used for dynamic environment.
* unlit - used for static environment.

---  
### Setup:
* the default lightmap texture size is set to 64x64. Override in **LightmapCreator::QueueNodesForIndirectLightProcess(), BeginIndirectLighting()**.
* the default unlit baked texture size is set to 512x512. Override in **LightmapCreator::BakeIndirectLight(), BakeIndirectLight()**.
* the direct render texture size is set to 1024x1024 by default to reduce the shadow jaggedness, but it's till not smooth as it's desired. Setup is in **LightmapCreator::BakeDirectLight()**.
* output files are placed in the **Lightmap/BakedTextures** folder.
  
---  
### Known Problem with Baked Textures:
Baking the unlit textures on the GPU produces some black edges. Changing the render texture filter settings didn't help, and I'm not aware of any tricks that can be applied to fix the problem.

---
### Screenshots
#### Direct Light
![alt tag](https://github.com/Lumak/Urho3D-Lightmap/blob/master/screenshot/directlight.png)  

#### Direct + Light Bounce 1
![alt tag](https://github.com/Lumak/Urho3D-Lightmap/blob/master/screenshot/lightbounce1.png)  

#### Direct + Light Bounce 2
![alt tag](https://github.com/Lumak/Urho3D-Lightmap/blob/master/screenshot/lightbounce2.png)  
*Light bounces are shown shaded with DiffLightMap and NoTextureLightMap techniques.*  

#### Unlit Baked Scene
![alt tag](https://github.com/Lumak/Urho3D-Lightmap/blob/master/screenshot/UnlitBakedImage.png)  
*Lightmap/bakedScene.xml shown in the editor with zero lights and zero shadowmaps.*  

---
### To Build
To build it, unzip/drop the repository into your Urho3D/ folder and build it the same way as you'd build the default Samples that come with Urho3D.
**Built with Urho3D 1.7 tag.**
  
---  
### License
The MIT License (MIT)







