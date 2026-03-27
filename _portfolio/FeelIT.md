---
title: "FeelIT"
date: 2012-07-07
excerpt: "Haptic and VR interactive platform for visually impaired people — exploring tactile feedback for virtual objects.<br/><img src='/files/portfolio/FeelIT/FeelIT500x300.png'>"
collection: portfolio
tags: [haptics, accessibility, virtual-reality, hardware, assistive-technology]
---

A project that sought to create a digital environment with augmented reality — based on non-visual tactile feedback — to allow blind people to explore virtual objects through relief information and virtual touch.

This project was ultimately frozen due to hardware limitations and cost constraints, but the journey shaped my approach to interdisciplinary engineering.

The idea
======

While studying at the university, I had the opportunity to work with various technological hardware devices. One technology that powerfully captured my attention was related to devices that could complement or virtualize the human senses.

A small toy with pins is what started everything: the [3D Metal Pin Art Board](). Apply pressure against an object and you obtain an impression of its relief.

![img](/files/portfolio/FeelIT/00.jpg)

A deceptively simple device. I started wondering: what if you could *fix* the pin positions electronically? You could store a surface, recall it later — like a raised photograph. You could let someone who had never seen an object explore its shape through touch.

Of course, you could just sculpt a model and hand it to someone. But my idea was something *controllable and changeable* — a dynamic tactile display.

In my mind as an electronic engineer, the concept was not far from a screen: a structured array of independently controlled elements. Instead of pixel color intensity, you control the height of each pin.

Around 2010, I built a first 16-pin version (a humble 4x4 grid) with binary control — electromagnets switching each pin between resting and raised positions.

Then reality hit. The costs were high, miniaturization was complex. I improved the design to a few height levels, but could not push beyond a 10x10 array (100 independently controlled mechanisms in a small space). The project was frozen.

The motivation
------

My vision was a device with thousands of stored relief representations and a system that would transform digital images into relief versions, allowing a blind person to interact with digital objects. Text documents, emails, and messages could be presented in Braille format.

![img](/files/portfolio/FeelIT/02.jpg)

At that time, mass 3D printing was not yet available. Exploring existing solutions, I found very few devices with a similar approach:

Some focused on printing Braille text documents on embossed paper:

![img](/files/portfolio/FeelIT/comp1.jpg)
![img](/files/portfolio/FeelIT/comp2.jpg)

Others were software applications for magnifying screen content for people with low vision:

![img](/files/portfolio/FeelIT/comp3.jpg)
![img](/files/portfolio/FeelIT/comp4.jpg)

There were also interesting innovations for reproducing phone text messages on Braille lines — consistent with my prototypes but limited to two positions, without the mechanical resistance and resolution I was aiming for:

![img](/files/portfolio/FeelIT/comp5.jpg)
![img](/files/portfolio/FeelIT/comp5.png)
![img](/files/portfolio/FeelIT/comp6.jpg)

I researched miniaturized technologies and explored various materials and mechanisms, which led me to other projects. But hardware costs and limitations remained the blocking constraint.

Haptic devices
======

During my undergraduate thesis, I explored haptic devices — servo-motor-based systems that feed back force and resistance to movement. They function as 3D input devices that can simulate the physical sensation of touching objects: resistance to penetration, surface texture, and contact forces.

Through these devices, a user can interact with virtual objects in a 3D environment by feeling the resistance and shape of surfaces that exist only in software.

![img](/files/portfolio/FeelIT/h1.png)
![img](/files/portfolio/FeelIT/h2.png)
![img](/files/portfolio/FeelIT/h3.png)

The project
======

By combining haptic feedback with a virtual environment, we built a system where visually impaired users could explore 3D objects through touch alone. The visual interface was deliberately minimal — this was a *haptic* interface, not a visual one.

![img](/files/portfolio/FeelIT/s1.png)

The team
------

In the final phase of the project, Daniel and I continued searching for resources and testing possibilities.

![img](/files/portfolio/FeelIT/Team2.png)

Testing
======

The most rewarding part was watching users interact with the system for the first time — hands exploring shapes they could only previously imagine.

![img](/files/portfolio/FeelIT/t3.jpg)
![img](/files/portfolio/FeelIT/t4.jpg)
![img](/files/portfolio/FeelIT/t5.jpg)
![img](/files/portfolio/FeelIT/t7.jpg)
![img](/files/portfolio/FeelIT/t8.jpg)
![img](/files/portfolio/FeelIT/t9.jpg)
![img](/files/portfolio/FeelIT/t12.jpg)

## Lessons learned

Although FeelIT never reached a production-ready state, the project taught me two things that shaped my career: first, that the most meaningful engineering problems sit at the intersection of technology and human needs; and second, that hardware constraints are temporary — the miniaturization and cost barriers that stopped us in 2010 are falling every year.

*This project does not have a public repository. The hardware prototypes and software components remain in private archives.*
