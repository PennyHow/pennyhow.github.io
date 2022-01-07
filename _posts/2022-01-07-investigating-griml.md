---
title: "Investigating Greenland's ice marginal lakes under a changing climate (GrIML)"
date: 2022-01-07 14:00
categories:
  - blog
tags: 
  - ice marginal lakes
  - glacier dynamics
  - hydrology
  - GLOF
  - greenland
  - ESA
---

<p style="text-align:justify;">I have recently started a new 2-year project on ice-marginal lakes in Greenland, as a follow on to previous work where we derived an ice-marginal lake ]inventory](https://www.nature.com/articles/s41598-021-83509-1) for all of Greenland for the year 2017. </p>

## Ice-marginal lakes in Greenland

<p style="text-align:justify;">Reservoirs that form at the fringes of the ice sheet are known as ice marginal lakes. The outflow from an ice marginal lake is typically dammed or restricted, either by a moraine or by the ice itself. </p>

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/greenland_iml_01.jpg?raw=true" alt="Unnamed ice marginal lake in SW Greenland" width="600" align="aligncenter" /><br> *An example of an ice marginal lake in Greenland. This particular lake is an unnamed ice marginal lake (88.5 sq km according to the 2017 inventory) on the SW margin of the Greenland Ice Sheet, fed from various glacial outlets*

<p style="text-align:justify;">These lakes have the potential to burst when the dam fails or is breached, causing catastrophic flooding events, which are typically referred to as <strong>Glacial Lake Outburst Floods (GLOFs)</strong> or <strong>jökulhlaups</strong> (the Icelandic term). GLOFs have been documented and studied closely at certain locations in Greenland, such as at Lake [Catalina](https://www.nature.com/articles/s41598-017-07960-9) in East Greenland. </p>

<p style="text-align:justify;">Our [inventory](https://catalogue.ceda.ac.uk/uuid/7ea7540135f441369716ef867d217519) from 2017 revealed <strong>over 3000 ice marginal lakes</strong> around the Greenland Ice Sheet and surrounding ice caps. We detected each lake using three independent remote sensing methods, utilising optical images, radar images and derived digital elevation models from satellites. In this new project, we aim to extent this study and examine ice marginal lakes in other years. With this new data, we can investigate how ice marginal lakes are changing across Greenland at a highly detailed level. </p>

<div class="wp-block-image"><figure class="aligncenter"><img src="https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41598-021-83509-1/MediaObjects/41598_2021_83509_Fig2_HTML.png?raw=true" alt="" width="800" /><figcaption>Figure 2 from <strong><span style="text-decoration:underline;"><a href="https://www.nature.com/articles/s41598-021-83509-1" target="_blank" rel="noreferrer noopener">How et al. (2021)</a></span></strong> showing ice marginal lakes over a selected region of the southwestern sector of the ice sheet margin. Panel A shows lake area, B shows lake shape, and C shows the detection method. The largest lake of this region is Kangaarssuup Tasersua, which is labelled 'KT' in Panel B.</figcaption></figure></div>

## The GrIML project

<p style="text-align:justify;"><em>Aim: To examine ice marginal lake changes across Greenland using a multi-method and multi-sensor remote sensing approach</em></p>

<p style="text-align:justify;">Ice marginal lake changes will be investigated in two manners, which are differentiated by their spatial and temporal resolution. </p>
<ol>
  <li>Annual inventories of ice marginal lakes will be generated to assess large scale changes in ice marginal lakes across Greenland (i.e. analysis covering a large spatial area at a coarse temporal resolution)</li>
  <li>Individual lakes will be selected and monitored more intensively over a time-series analysis to examine evolving GLOF dynamics (i.e. focused areas at very-high temporal resolution)</li>
</ol>

## Programming in GrIML

<p style="text-align:justify;">GrIML will build upon existing workflows programmed in Python, refined here to form a unified processing chain that I intend to package and share openly on Github and pip.</p>

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/griml_workflow.png?raw=true" alt="The proposed GrIML workflow." width="1500" align="aligncenter" /><br> *The proposed GrIML programming workflow*

Key Python packages I intend to use in the workflow:
+ [xarray](https://xarray.pydata.org/en/stable/) -- for large data handling and parralel processing
+ [rasterio](https://rasterio.readthedocs.io/en/latest/) -- for raster processing
+ [geopandas](https://geopandas.org/en/stable/) -- for vector data handling

<p style="text-align:justify;">For the satellite data retrieval, I have a big hope to move away from heavy clunky data downloads by utilising data retrieval from URLs (using readily available functions like [this](https://rasterio.readthedocs.io/en/latest/api/rasterio.html?highlight=URL#rasterio.open/)). This is a big "if" though, as I am not sure how heavy this will be on computer memory. </p>

<p style="text-align:justify;">I intend to also have an add-on module to interact with the [SentinelHub](https://sentinelhub-py.readthedocs.io/en/latest/) APIs, a cloud processing platform that can be used to retrieve and process data from many satellite products. This should be a fun component of the project, as pushed scripts to the API are advised to be in Javascript -- a programming language I have some experience with, but want to be better at.

<p style="text-align:justify;">By having the option to retrieve data from URL or SentinelHub, I envisage that the workflow can be used by all regardless of whether they have a paid license for SentinelHub or not.</p> 


