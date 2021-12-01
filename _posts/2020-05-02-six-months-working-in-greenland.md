---
title: "Six months working in Greenland"
date: 2020-05-02 19:07
categories:
  - blog
tags:
  - ArcticDEM
  - asiaq
  - ESA
  - Greenland
  - ice-marginal lakes
  - python
  - remote sensing
  - satellite
  - Sentinel
  - supraglacial lake
  - supraglacial lake drainage
---
<p style="text-align:justify;">Since starting work in Greenland, we have had a handful of interesting projects which started before I arrived . Thankfully these projects have been related to the cryosphere, so I have been able to throw myself into them. As I was hired primarily for my knowledge of programming, my main tasks in these projects thus far have been automating and running batch processing for big satellite data.</p>

<p style="text-align:justify;">Firstly, we have been finalising an ESA project looking at <strong>ice-marginal lakes in Greenland</strong>, creating an inventory for the whole of Greenland as well as generating time-series datasets for a select few ice-marginal lakes in SW Greenland. <strong>A remote sensing approach is used to identify these lakes</strong>, using three different methods for validation from Sentinel-1 (radar) imagery, Sentinel-2 (optical) imagery, and ArcticDEM (3D elevation model).</p>

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/greenland_iml_01.jpg?raw=true" alt="Unnamed IML in Greenland" width="520" height="520" align="aligncenter" /> <br>*The second largest ice-marginal lake in Greenland (unnamed), which lies on the SW margin of the ice sheet. The lake was 88.5 sq km in 2017, fed from various glacial outlets. The largest ice-marginal lake in Greenland is located on the NE margin, called Romer Sø, which is where the well-known piedmont glacier, <a href="https://earthobservatory.nasa.gov/images/85303/elephant-foot-glacier" target="_blank" rel="noopener">Elephant Foot Glacier</a> flows into.*

<p style="text-align:justify;">I came into the ice-marginal lakes project just as the pan-Greenland dataset was being refined, so could assist with the data quality check and metadata generation. I also took over the optical image processing scripts, modifying them for generating the time-series dataset. <strong>Re-engineering scripts so that big data processing  can be facilitated at the press of a button has been a highlight for me</strong> - it's a achievement when you know you have processes that are slick, efficient and require little effort to produce valuable datasets.</p>

<p style="text-align:justify;">The second project I have been working on is another ESA project, looking at <a href="http://esa-icesheets-greenland-cci.org/index.php?q=SGL" target="_blank" rel="noopener">detecting supraglacial lakes from optical satellite imagery</a>. Unlike the former project where we were delivering a dataset, the supraglacial lake component was to serve as a research/exploration part of the project - we were to explore and analyse the dataset as well as produce it.</p>

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/greenland_iml_01.jpg?raw=true" alt="Supraglacial lakes in the Sermeq Kujalleq catchment" width="520" height="520" align="aligncenter" /> <br>*Supraglacial lakes in the Sermeq Kujalleq catchment (also known by its Danish name Jakobshavn Isbræ), near Ilulissat, West Greenland. This particular scene was captured in June 2019, close to the beginning of the melt season when supraglacial lakes in the lower catchment fill and drain. Lakes tend to fill and drain in the upper catchment later on in the melt season, with this pattern comonly known as a upglacier-propagating drainage regime.*

<p style="text-align:justify;">I came on to this project just as the kick-off meeting happened, so was thrown into the processing scripts to write from scratch. Whilst I wouldn't say I had a strong background in remote sensing before coming to Asiaq, <strong>I have found that most of the scripting felt similar to those I made during my PhD for processing terrestrial time-lapse imagery </strong>(a Python toolset called <a href="https://github.com/PennyHow/PyTrx" target="_blank" rel="noopener">PyTrx</a>). They felt essentially rooted in the same theory and therefore, although the task felt daunting at first, it was a good feeling to see something familiar.</p>

<p style="text-align:justify;">On top of all this, <strong>I have been trying to streamline our data management. This is part of a longer-term strategy to optimise common routines and save time in projects.</strong> I have been working on making batch download scripts for some of the main satellite platforms - namely Sentinel-1, Sentinel-2, Landsat, MODIS and ArcticDEM. Whilst these tasks might seem straightforward, a lot of time has gone into data file structures and Asiaq-wide storage solutions. Equally, limitations with particular databases has meant  finding alternative databases for downloading from - a key example is the <a href="https://scihub.copernicus.eu/userguide/LongTermArchive" target="_blank" rel="noopener">Long Term Archive (LTA)</a> for Sentinel-2 imagery, and finding alternative databases to <a href="https://scihub.copernicus.eu/" target="_blank" rel="noopener">Copernicus SciHub</a> for older Sentinel-2 imagery.</p>

<p style="text-align:justify;">So, all in all, it has been quite a programming-heavy time since I started work in Greenland. I still feel lost and overwhelmed with the move to Greenland, but we have some really interesting projects that I've found really gel well with the skills that I have. We have submitted a handful of proposals and hope to hear some good news from them soon. I'm also looking at fleshing out some project ideas I have, which will likely go into future proposals. <strong>It's been a very intense time, but the opportunity to live and work in Greenland far outweighs it all. </strong></p>
