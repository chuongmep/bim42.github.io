---
id: 818
title: Automatic Modeling
date: 2015-04-19T21:07:51+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=818
permalink: /2015/04/automatic-modeling/
categories:
  - Revit
tags:
  - Automation
  - Coordination
  - Documentation
  - Revit
---
Most questions I encounter these days turn around using building information modeling for producing construction drawings, schedules or clash detection reports. These features are important, of course, but they remain centered around using a more or less complete building model. But a largely overlooked use of building information model is the ability to automatically model building elements. In fact, object-oriented modeling should allow us to simply describe our solutions and let the computer implement them in our building model, and even warn us when something doesn't fit.

Lead by this thought, and a problem raised by one of my colleague, I started looking again toward slab insulations. Before BIM, slab insulation was simply annotated on the drawing, and taken into account when creating a building section. Now, for coordination purpose, we have to spend large amount of time modeling everywhere a fairly simple element like insulation, without real added value.

There is nothing new with this problem, and I was already trying to find a solution for modeling insulation layers on the upper face of a series of spaces with [my latest version of RoomFinishes](http://bim42.com/2014/08/room-finishes-update/), without finding a decent solution.

But while looking for something totally different, I came across [this article in AUGI](https://www.augi.com/library/using-rooms-spaces-for-leverage-in-revit-mep) about room and spaces in Revit. So after five years working with Revit, I realized than by checking this small checkbox in the "Area and Volume Computations", the room continues up until it fit a room bounding element, a ceiling or a floor.

![VolumeComputation](/assets/2015/04/VolumeComputation.png)

Energized by this nice discovery, I created a small application for automatically modeling insulation. This application retrieves every faces of a given room, and uses the higher ones as references for modeling floors and walls as insulations.

![Insulation](/assets/2015/04/Insulation.png)

The only problem here is framing. They are not room bounding elements, and the upper face of the room does not fit the shape of the beam. I solved temporary this problem by creating a small floor under the beam.

![beam](/assets/2015/04/beam.png)

While doing this, I realized there is a lot of tricky cases, where insulation have to be modeled as wall or slab regarding of the configuration.

The entire code for this application can be found [here](http://pastebin.com/Xzm90tdi). It is quite messy, but I hope it can help you anyway.

This small example illustrates one of the possibilities of working with building information models, where information can actually help us focus more on the actual design of the building and less on the representation of this design in the model.