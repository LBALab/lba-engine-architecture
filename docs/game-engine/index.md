---
title: Game Engine
layout: home
nav_order: 2
permalink: /game-engine
---

# Game Engine

## Overview

Little Big Adventure (LBA) series engine was an evolution of the tooling created during the development of Alone in the Dark (AITD). They share a lot of the same core ideas but the team was able to innovate and evolve their technology.
Both games shared pre-rendered backgrounds with 3D software rendered characters, a technique use in the early 90s due to hardware constraints. AITD was the pioneer of pre-rendered backgrounds and use static images that were hand drawn on top of 3D wireframes of a 3D scene. Each image corresponding to a different camera view of the scene.

![AITD](/assets/aitd1.png)

LBA did it differently and use isometric sprite composition in order to create a scene and use a single isometric camera view  panning around the environment.

![LBA](/assets/lba1street.gif)

The isometric scenes were composed in a grid format with limited width,  depth and height. Various objects were composed by a number of sprites following a set of standard dimensions and then placed together to create scenes. They are also used for collision detection with slopes to make the height transition smoothly. 

![LBA1 Isometric Sprite](/assets/bench-sprite.png)
![LBA1 Isometric Scene](/assets/bench-iso.png)

The team continue the trend in Time Commando (TICO) and used pre-rendered backgrounds with video motion. A similar technique used in LBA movies but improved to be used not only as cut-scenes but in-game backgrounds with depth information attached. 

![TICO Pre-Rendered Background Motion](/assets/tico-prerendermotion.gif)

Another aspect that has been shared among all games is the use of 3d software rendering for the player character and non-player characters (NPC) with dedicated file formats. AITD uses 3d models with flat polygons with solid colours and dithering in some polygon types to give a more textures like feel. 

![AITD 3d model](/assets/aitd1-model.png)

LBA uses the same flat polygons but added the implementation of Gouraud Shading and Directional Lighting. 

![LBA 3d model](/assets/lba1-model.png)

LBA2 and TICO had another enhancement by adding texture mapping to their 3d model formats.

![LBA2 3d model](/assets/lba2-model.png) ![TICO 3d models](/assets/tico.jpg)

LBA2 also used the models for the outside 3d scenes, which had a further improvement from isometric only scenes in from LBA1.

![LBA2 3d Outside Scene](/assets/lba2-outside.jpeg)

