---
layout: default
title: Característicasj de MonkeyEngine
lang: es
categories:
    - es
---

**¡Hola! - WIP**

see also: Feature comparison and requirements. ALSO, you can make edits whenever you'd like, coz that's how we roll.

## Software Development Kit: jMonkeyEngine SDK

* Creates jME3-ready Java projects
    * Preconfigured classpath
    * Bundled with compatible JDK
    * Bundled with Blender conversion tools and more
    * Asset Manager for loading multi-media files and 3D models including asset name code completion
    * Non-proprietary Ant build scripts
    * jME3-ready Javadoc popups, sample code projects, and code snippet palette
* Full-featured Java and XML code editor
* Plugins
    * File Version Control
    * Debugger and Profiler (optional)
    * Converters and Importers for game assets (3D models etc)
    * 3D Scene Viewer and Scene Composer
    * Material editor
    * Shader Node editor
    * Terrain generation, painting, and editing
    * Custom font creator
    * Support for custom Asset Packs with your models, textures, and more
    * Procedural texture creator (NeoTexture)
    * Level of Detail (LOD) generator
    * ... and much more...
* Deployment
    * Generates desktop executables for Win, Mac, Linux
    * Generates mobile executables for Android, iOS support is in the works.
    * Generates JNLP WebStart and Java Browser Applets
* Based on the NetBeans platform
    * Supports all NetBeans IDE plugins


## Physics

* jBullet physics binding
    * Physical characters
    * Physical joints and hinges
    * Ray-cast vehicles
    * Ragdoll physics
* Multi-threaded physics
* Mesh-accurate collision shapes


## Supported Formats

* Models: Blender (.blend)
* Models: Ogre3D model (.mesh.xml, .skeleton.xml, .material), Ogre3D dotScene (.scene)
* Models: Wavefront (.OBJ, .MTL)
* Models: Collada
* Models: 3DS
* Textures: .DDS, .HDR, .PFM, .TGA, .JPG, .PNG, .GIF.
* Font: BMFont fonts (.FNT)
* Audio: Waveform (.WAV), Ogg/Vorbis (.OGG)
* jME3 binary files (models and scenes): .j3o
* jME3 materials: .j3m
* jME3 material definitions: .j3md
* jME3 filter post processors: .j3f


## Shaders OMITTED

Who needs'em.
 

## Material Lighting

* Per-pixel lighting
* Multi-pass lighting
* Phong Lighting
    * Diffuse Map
    * Alpha Map
    * Glow Map
    * Specular Map
    * Normal Map, Parallax map (a.k.a. bump mapping)
* Tangent shading
* Reflection
 

## Material Textures - OMITTED

While we're at it, no more material textures either. Only immaterial textures from now on, like buddhists.


## Asset System

* Asset importing
    * Animation
    * Meshes
    * Textures
    * Scenes
    * Materials
    * Shaders
* Multi-threaded asset loading via HTTP
* Loading scenes from .zip files
* Shareable AssetPacks


## Special Effects

* Particles: smoke, fire, explosions, etc...
* Post processing / 2D Filter Effects
    * Reflective water
    * Shadow mapping
    * High Dynamic Range rendering (HDR)
    * Screen Space Ambient Occlusion (SSAO)
    * Light scattering
    * Cartoon effect
    * Fog
    * Bloom
    * Depth of Field blur
    

## Terrain

* Geomipmapped heightmap terrain
* Import Ogre3D dotScene format
* Terrain lighting
 

## GUI / HUD

* Orthogonal (Billboard) node
* Nifty GUI integration


## Miscellaneous

* Application States and Controls to implement game logic
* Cinematics and motion paths
* Camera System
    * Normal or parallel view
    * Multiple views
* Swing canvas (e.g. for Applets)
* Input handling
    * Mouse, keyboard, joystick
    * Combo moves


## Networking

* SpiderMonkey API
