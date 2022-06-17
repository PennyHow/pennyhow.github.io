---
title: "PhD update: June 2016"
date: 2016-07-02 22:18
categories:
  - blog
tags: 
  - cameras
  - glaciology
  - kronebreen
  - PhD
  - PyTrx
  - research
  - supraglacial lake drainage
  - Svalbard
  - time-lapse
---
<h5 style="text-align:justify;">I have spent this month focused on developing PyTrx, our analysis software for oblique time-lapse image sequences. In particular, I have been working on a set of functions that will automatically detect areal features in glacial environments, such as surface lakes and submarine plumes, and transform pixel regions to real world areas. I have been testing this on an image sequence from Kronebreen glacier in Svalbard, where we captured several surface lakes filling and draining over a summer melt season.</h5>

<p style="text-align:justify;">June kicked off to bad start when I agitated an old knee injury whilst at the gym. I've had bad knees for a large part of my life and thought most of the problem had been sorted after surgery in 2008. Unfortunately I am now looking at intensive physiotherapy and perhaps another round of surgery after rupturing a ligament... so I have been off my feet for a lot of this month.</p>

<p style="text-align:justify;">But, turning a negative into a positive, it has meant that I have been able to concentrate on developing an additional module to PyTrx. PyTrx is the software that I have been developing as part of my PhD to obtain measurements from oblique time-lapse imagery - 'Py' signifying that it is coded in Python, an open access computing language; and 'Trx' to indicate that the software can be used to track measurements through sequential images in time. This was initially implemented to obtain velocity measurements from a time-lapse images of a glacier in Svalbard. These time-lapse images also showed several lakes pooling at the surface of the glacier, which simultaneously drained. What is unknown is how the drainage of these lakes affect the velocity of the surrounding region. A separate set of functions was needed to measure the surface area of these lakes.</p>

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/krone_lakes_01.gif?raw=true" alt="Supraglacial lakes filling and draining in the upper section of Kronebreen glacier, Svalbard. The sequence covers June to July 2015, one image per day." width="557" height="371" align="aligncenter" /><br> *Supraglacial lakes filling and draining in the upper section of Kronebreen glacier, Svalbard. The sequence covers June to July 2015, one image per day.*

<p style="text-align:justify;">Lakes are distinguished in an image based on the intensity of each pixel, which is determined by the three colour channels - red, blue and green - also referred to as the RGB values. Given an RBG range of the 'lightest' and 'darkest' regions of the lakes, they can be automatically distinguished and masked. Knowing where the camera is located and its pose, the pixel location of the lakes in the image can be translated to their position in the real world. For their position in the real world, we can determine their surface area.</p>

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/krone_lakes_02.gif?raw=true" alt="The lake extents, as seen in real world coordinates from above, filling and draining as they move downglacier (to the left of the image)" width="606" height="428" align="aligncenter" /><br> *The lake extents, as seen in real world coordinates from above, filling and draining as they move down-glacier (to the left of the image).*

The software effectively runs, showing the main lakes from the front of the time-lapse image sequence growing and connecting to cover a 100 m area (approximately). There are still two problems that need rectifying though:

1. The lake areas are quite noisy, with 'false' lakes detected in some of the images. The next step will be to apply a filter to exclude areas that are too small to be lakes

2. Part of this sensitivity is due to changes in illumination from image to image. The most apparent illumination differences can be seen, with spikes in the total surface lake area associated to detection of these 'false' lakes. Unfortunately it is very difficult to change this in the software as it relies on the RGB value of the pixels, which are affected by the change in illumination. The only options are to either select images with more consistent illumination or apply an averaging algorithm to smooth out irregular area data.

<a href="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/krone_lakes_03.jpg?raw=true" alt="Plot showing the surface area of all the surface lakes from image to image (02/06 - 13/07/2016)" width="800" align="aligncenter" /></a><br> *Plot showing the surface area of all the surface lakes from image to image (02/06 - 13/07/2016). The three spikes in the data show where 'false' lakes have been detected due to changes in image illumination.*

There have also been a couple of issues with the translation from pixel areas to real world areas (which is done here using a process called georectification), which has been ongoing for a while now. This process is not only used to determine real world areas, but also other real world measurements such as distance and velocity. It is hoped that when these problems are solved then PyTrx will be made freely available for others to use. Despite these limitations, I'm quite happy with this part of PyTrx and hopefully next month it can be used to measure the area of other glacial features, such as submarine plume extent.

So. Broken knees, working code... and Brexit (I wrote a blog post on my thoughts regarding the EU referendum <a href="https://pennyhow.github.io/blog/a-phd-students-views-on-the-eu-referendum/">here</a>). That sums up my month. It's not been the greatest month but I've tried to make the most of it. Hopefully July will go a little better.
