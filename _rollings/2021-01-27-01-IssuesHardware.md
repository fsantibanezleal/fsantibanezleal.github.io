---
title: ' Hardware Issues ' 
date: 2021-01-27-01
permalink: /rollings/2021/01/Hardware-Issues/
tags:
  - Hardware
  - Outliers
  - Hyperspectral Cameras
  - Hyperspectral Data
---

Our SWIR hyperspectral camera have some consistent Outliers XD.

The Issue
======

It could be the outcome of some little object of sand in the lens or in the spectograph

This situation generates some outliers in the form of dead pixels in specific spectral bands.
Our sensors are scanlines obtained by a spectrograph projecting filtered ligh on a square clasic imaging sensor

Identification
------

![img](/files/personal-blog/2021-01-27-01/01.png)


Solution
------

Hard work for this summer !!!

Cleaning of Optics and Hardware

![Hyperspectral classification pipeline](/images/projects/hsi_mineral_classification.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Dead pixel correction:</strong><br/>
I_corrected(x,y,λ) = median(neighborhood) when I(x,y,λ) deviates > 3σ from local statistics
</div>
