---
id: 275
title: Level Of Development
date: 2012-11-21T18:16:44+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=275
permalink: /2012/11/level-of-development/
publicize_twitter_user:
  - bim42
publicize_reach:
  - 'a:3:{s:7:"twitter";a:1:{i:278469;i:33;}s:2:"fb";a:1:{i:278468;i:130;}s:2:"wp";a:1:{i:0;i:2;}}'
categories:
  - General BIM
tags:
  - BIM Manager
  - Coordination
  - General
  - Normalization
---
One of my current project made me think of talking about the so-called LOD of a building model.

The LOD (Level Of Development or Level Of Detail) was first described on the Model Progression Specification (MPS) development by Vico Software in 2004. This document aimed to create a framework in order to define standards for any building model delivery. It answers, for each phase of a project, the following questions :

* How accurately the model should be detailed ?
* Who is responsible for modeling a particular element ?
* What information should be integrated in the model ?

In 2008, the American Institute of Architect  after further developments on this project, released their official version, the E-202 “Building Information Modeling Protocol Exhibit”.

![aia_e202](http://bim42.com/wp-content/uploads/2012/11/aia_e202.jpg)This paper divided the Levels Of Development in five categories, each one describing the elements expected in the model, the corresponding state of development of the project and the possibilities for producing construction documents and building analysis. They are defined as follows:

### LOD 100: Conceptual design

The model represent the general massing of the building, with area, volume, orientation and so on.

This model can be used for solar and early energy analysis.

### LOD 200: Design development

All systems are modeled with their general size, location, orientation and approximate quantities.

It can be used for general performance analysis and early calculations.

### LOD 300: General construction documents

In this model, elements are accurately integrated, with their actual size and location. It is suitable for producing general assembly and construction drawings.

This model allow precise analysis and simulations on every element and system. It can also be used for coordination and clash detection.

### LOD 400: Fabrication information

Every element is modeled for fabrication purpose.

The model is suitable for shop drawings

It can be used for direct production and construction scheduling.

### LOD 500: As-Built model

The BIM equivalent of As-Built drawings. In these models, elements are represented with all technical information needed for maintenance and procurement.

These descriptions are indicative, and do not prevent the BIM Manager from describing model deliverables more exhaustively. They are more like guidelines for creating an accurate BIM Implementation Plan, with precise indication for each actor about his responsibilities in the development of the model. To do so, these guidelines come with a Model Element Table like this one :

(From [http://www.acec.org](http://www.acec.org/))

![modelelementtable](http://bim42.com/wp-content/uploads/2012/11/modelelementtable.jpg)

This table defines the required level of detail for each element of a building model at each phase/LOD of the project.

I am unsure whether or not this “Building Information Modeling Protocol Exhibit” can be used as it for any project, especially in France, where construction practices may differ from what the AIA first defined. However, it is a great tool for creating an accurate BIM Implementation Plan. It describes well the expected state of the model for each phase and may come in handy when working with companies which have not yet integrated all requirements of a BIM workflow.