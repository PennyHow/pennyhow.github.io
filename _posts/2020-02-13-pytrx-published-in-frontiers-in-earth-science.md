---
title: "PyTrx published in Frontiers in Earth Science"
date: 2020-02-13 11:09
categories:
  - blog
tags: 
  - academia
  - camera
  - Frontiers
  - github
  - ice velocity
  - meltwater plume
  - open-source
  - photogrammetry
  - photography
  - pip install
  - Programming
  - publication
  - PyPI
  - python
  - PyTrx
  - readthedocs
  - research
  - Svalbard
  - terminus position
  - tidewater glacier
  - time-lapse
---
<p style="text-align:justify;"><a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">Frontiers in Earth Science recently published our work on PyTrx</a>, the Python toolset developed during my PhD for processing oblique time-lapse imagery of glacial environments. The toolset is freely available via <a href="https://pypi.org/project/pytrx/" target="_blank" rel="noopener">pip install</a> and <a href="https://github.com/PennyHow/PyTrx" target="_blank" rel="noopener">GitHub</a>, and <strong>this paper serves as its companion piece to inform users of its capabilities and applications</strong>.</p>

<img class="alignnone size-full wp-image-7666" src="https://pennyhow.files.wordpress.com/2020/02/krone_dense_velos.jpeg" alt="Ice velocities from Kronebreen" width="3524" height="2626" align="aligncenter" /> <a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener"><br>*<a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">Figure 5 from our Frontiers publication</a>, demonstrating PyTrx's dense feature-tracking and georectification capabilities. Velocities were determined from oblique time-lapse image pairs between 14 June and 7 July 2014 at Kronebreen, a tidewater glacier in Svalbard. Templates (represented here as points) were defined over a 50x50 m grid, which were matched between image pairs using normalised cross-correlation and filtered by correlation (i.e. templates were retained where the correlation of the match was above 0.8). The sequence shows an early season speed-up at the terminus of the glacier, where velocities increase from an average of 2.5 m/day (14-16 June, first panel) to 4.7 m/day (5-7 July, last panel).*

<p style="text-align:justify;"><strong>PyTrx came about as I wanted to derive measurements from time-lapse imagery</strong>, which I had collected from Kronebreen and Tunabreen, two tidewater glaciers in Svalbard. However, <strong>I couldn't find any openly available toolset that met my needs.</strong> There are a handful of toolsets for processing ice velocities from time-lapse imagery (see <a href="http://imgraft.glaciology.net/" target="_blank" rel="noopener">ImGRAFT</a>, <a href="https://www.lancaster.ac.uk/staff/jamesm/software/pointcatcher.htm" target="_blank" rel="noopener">Pointcatcher</a> and <a href="https://tu-dresden.de/bu/umwelt/geo/ipf/photogrammetrie/forschung/forschungsprojekte/emt/?set_language=en" target="_blank" rel="noopener">EMT</a> - three great examples), but I wanted to also process other types of measurements, such as meltwater plume footprint extents, supraglacial lake areas, and changes in terminus position. Additionally, most toolsets that I came across were programmed in a limited range of programming languages, mainly Matlab, and I felt there was a need for a toolset in an open-source programming language for those who wanted an alternative that did not rely upon a licensed software.</p>

<p style="text-align:justify;">We set about making PyTrx just for our own processing needs at first, programmed in Python and largely utilising OpenCV, a Python package that handles complex computer vision operations on optical imagery. <strong>Before long, we realised there was a need for this toolset in the public domain, with growing interest from others</strong>; hence why we began focusing on finalising PyTrx as an operational package that anyone could use.</p>

<img class="alignnone size-full wp-image-7668" src="https://pennyhow.files.wordpress.com/2020/02/plume_projections.jpg" alt="Delineating meltwater plume footprints using PyTrx" width="2269" height="1165" align="aligncenter" /> <br>*<a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">Figure 8 from our Frontiers publication</a>, showing changes in meltwater plume extent distinguished from time-lapse imagery of Kronebreen using PyTrx. The surface expression of the meltwater plume has been tracked through images captured on 5 July 2014 at 18:00 (A), 20:00 (B), and 22:00 (C) to demonstrate part of its diurnal recession. Each plot shows the plume definition in the image plane (top) and its translation to real-world coordinates and plotted onto a coinciding Landsat 8 satellite image (bottom).*

<p style="text-align:justify;">PyTrx has been developed with object-oriented design, meaning that the core functions are wrapped in callable-objects, which make it <strong>accessible to beginners in programming</strong> whilst also serving those more experienced. The following main functions can be performed with the toolset: <strong>dense template matching and sparse Optical Flow methods for deriving velocities</strong>, <strong>automated detection of area features</strong> (such as supraglacial lakes), <strong>manual delineation of area and line features</strong> (e.g. meltwater plume footprints, terminus position), and <strong>camera calibration and optimisation</strong> for refining the georectification of measurements from the images.</p>

<p style="text-align:justify;">There were many stumbling blocks when it came to publishing PyTrx. I struggled as the feedback, although positive, was a large undertaking that made me question PyTrx's worth and I doubted my own capabilities in delivering a sound toolset to the glaciology community. <strong>Overall though, the review process brought about big changes to PyTrx, which were absolutely essential to improving and finalising the toolset. </strong>I have a lot to thank for the review process, without which the toolset would not have reached its full potential and be what it is today.</p>

<img class="aligncenter  wp-image-7675" src="https://pennyhow.files.wordpress.com/2020/02/tuna_terminusprofiles2.jpg" alt="Terminus lines derived with PyTrx" width="363" height="362" align="aligncenter" /> <br>*<a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">Figure 9 from our Frontiers publication</a>, demonstrating PyTrx's ability in extracting terminus profiles from Tunabreen, a tidewater glaciers in Svalbard. Terminus lines were manually traced from sequential time-lapse images, and subsequently georectified to provide a record of terminus retreat.*

<hr>

<h3>Links</h3>

<a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">PyTrx publication in Frontiers</a>- our paper, describing the toolset and its applications using time-lapse imagery of tidewater glaciers in Svalbard

<a href="https://github.com/PennyHow/PyTrx" target="_blank" rel="noopener">PyTrx GitHub repository</a> - where PyTrx can be downloaded from (the master branch is where the raw scripts are, whilst the distribution branch holds the package files and readthedocs materials

<a href="https://pytrx.readthedocs.io/en/latest/" target="_blank" rel="noopener">PyTrx readthedocs</a> - PyTrx guide and code documentation

<a href="https://pytrx.readthedocs.io/en/latest/" target="_blank" rel="noopener">PyTrx on PyPI</a> - PyTrx's package distribution via pip
