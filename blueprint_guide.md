# Unreal Engine Blueprints User Guide

## Table of Contents

- [Introduction](#introduction)
- [Set Up](#set-up)
- [Blueprints Overview](#blueprints-overview)
- [Get Started on your blueprint](Get-Started-on-your-blueprint)
- [Common Issues](Common-Issues)

## Introduction

Welcome to the Unreal Engine (UE) Blueprint Guide. This will outline how to get started on making blueprints in UE using both blueprints and C++ and is made for game developers who aspire to get started on making something cool in UE.

## Set Up

Follow [this linked setup guide](install_UE.md) to get UE installed on your computer.

*Note: Depending on what version you have (or will have) installed, the experience may be different and some instructions in this tutorial may not be 1:1 with your version. Please consult other guides, tutorials, and internet searches for the best outcome.*

## Blueprints Overview

For this guide, we will be working with the latest version at the time of writing which is 5.5.4. The rest of this guide will outline a simple and easy tutorial for UE blueprints. If you want to see the full developer documentation you can head to the [developer guides on the Epic website.](https://dev.epicgames.com/documentation/en-us/unreal-engine/blueprints-visual-scripting-in-unreal-engine)

### What is a blueprint

A blueprint is a visual scripting system to achieve gameplay scripting through nodes-based functionality- all within UE.

You can create unique gameplay by C++ alone or also coupled with the blueprints feature. It makes creating gameplay easy and accessible without the need to know everything about writing in C++ code.
Here is a preview of a blueprint that we will walk through the components and logic for.

![alt text](<ue blueprint image.png>)

In this image, the boxes are called nodes and they all connect to each other in some logical way through the curved lines attached to them. So, lets get started!

### Intention for this guide

We will start by making changes and configuring settings in the level, then using C++ to add preliminary logic, and lastly we will build out the details in the blueprint to acheieve the blueprint pictured above.

## Get started on your blueprint

### Launch UE and configure your project

![alt text](<Screenshot 2025-05-07 173604.png>)

1. Select the following project preferences:

    1. Select Game (Left hand side)
    1. Select Top Down
    1. On the right, you can toggle blueprint or C++. Select Blueprint and we will add C++ later on.
    1. Target Platform is Desktop
    1. Check Starter Content box
    1. Change the project location if needed and create a name for the project. The default name would be MyProject
    1. Click Create

Your level should load and next we will want to add a playable character to this level.

### Add a playable character

Depending on if you chose an earlier version, such as in UE4, it may come with this already loaded in the level. If so, you can then skip to the [Implementing C++ environment](#implementing-c-environment) section below. Otherwise continue with the following steps:

1. Select Content Drawer in the bottom left corner
1. Click Add (with green plus)
1. Select add feature or content pack
1. A new window will open. Select Third Person. This enabled player movability features
1. Now change the default game mode by going to Edit in the top left panel
1. Select project settings
1. Click maps and modes
1. Under default mode, select third person (listed as BP_ThirdPersonGameMode)
1. You can close the excess windows that are open (leaving open the main viewport window) and press the green play button. This will trigger the playable character to move around.
1. Click anywhere in the level and drag your mouse in the direction you want the character to move
1. Press red stop button when you are done

![alt text](<UE5 third person level with actor.png>)

The next step is to add physics to our actor(s) already in in the level so we will be required to set up our C++ environment.

### Implementing C++ environment

We will need to configure a new C++ environment to create some logic for our actor(s). If you are new to programming, do not worry as this will not be intensive and you dont need to know very much.

However, this will be a learning experience and is a good entry point into working with C++ and blueprints combined- a useful skill in game development and Unreal Engine.

1. Navigate to Project Settings: You can use the Settings button in the top right corner then click Project Settings... or go to Edit > Project Settings...
1. In the Project Settings window, under Platforms, choose the operating system (OS) you are currently using. For this tutorial, we will be using Windows OS
1. Scroll down on the right side of the window and Under ToolChain select Visual Studio 2022. Older versions will mostly be deprecated so try to just use the newest version if 2022 suddenly becomes deprecated. Close out of the Project Settings window
1. In the top most tray of the editor, go to Tools > New C++ Class. Depending on your version, you also will find this by going to the content browser in the bottom left corner > Right clicking in the empty space > Then choose New C++ Class
1. A new window will open to choose a parent class and will also provide the option to download Visual Studio here.

![alt text](<add a c++ class.png>)

From here you can continue below to install Visual Studio or skip to the following section of [creating an actor parent class in C++](#creating-an-actor-parent-class-in-c)

#### Downloading Visual Studio

This section is continuing on from the end of the previous section.

1. While the Add C++ Class window open, in the bottom right corner click Install Visual Studio (*year*).
1. Follow the computer pop-ups to finish installation of Visual Studio
1. When it is finished installing you may need to close and re-open UE to proceed with choosing a C++ parent class. The engine will then recognize the newly installed IDE and the "No compiler" error message will disappear.
1. Proceed to the next section

#### Creating an actor parent class in C++

With the Add C++ Class window open, you will see a list of available classes.

1. Select "Actor" as our parent class
1. Click next
1. Specify a different actor name or leave it as MyActor
1. Click create class. The default code in this class will be compiled and will open in a Visual Studio window
1. From here we will be looking at C++ code. You should see two tabs open: MyActor.cpp and MyActor.h

    *Note: C++ code generated from previous versions of Unreal Engine such as in UE4 will have code that looks slightly different but will still achieve the same result we are looking for*

![alt text](<MyActor.cpp bare actor code; no errors.png>)
![alt text](<MyActor.h bare actor code; no errors.png>)

#### Writing code in Visual Studio

1. . From here we want to add logging that we can track in UE:
    1. In the MyActor.cpp file, under the method ```void AMyActor::BeginPlay()``` we want to add a line of code after ```Super::BeginPlay();```. Space down under this line
    1. Copy this code and paste into the space```UE_LOG(LogActor, Warning, TEXT("*** Hello from UE5 ***"));```

        *Note: This is case sensitive so please take note of any text in all caps*
1. Now we need to initialize or define our logging:
    1. In the MyActor.cpp file you will find at the beginning ```#include MyActor.h```. Space down from this line and include this code:

## Common issues

If you are running into technical issues and maybe are stuck with troubleshooting, here are some common issues that may save you a trip to Google:

### Missing build tools

[Back to the top](#unreal-engine-blueprints-user-guide)
