---
title: "PyTrx"
permalink: /pytrx/
author_profile: true
---

<a href='https://pytrx.readthedocs.io/en/latest/?badge=latest'> <img src='https://readthedocs.org/projects/pytrx/badge/?version=latest' alt='Documentation status' /></a> <a href="https://badge.fury.io/py/pytrx"><img src="https://badge.fury.io/py/pytrx.svg" alt="PyPI status" height="18"></a><br>

<p style="text-align:justify;">PyTrx (short for 'Python Tracking') is a Python object-oriented toolset created for the purpose of calculating real-world measurements from oblique images and time-lapse image series. Its primary purpose is to obtain velocities, surface areas, and distances from imagery of glacial environments. </p>

<p style="text-align:justify;">PyTrx is freely available to use, either by cloning the repository from <a href="https://github.com/PennyHow/PyTrx">Github</a> or using <a href="https://pypi.org/project/pytrx/">pip install</a>. Documentation for using the toolset is available at <a href="https://pytrx.readthedocs.io/">readthedocs</a>.</p>

<hr>

<h2> About PyTrx </h2>

<p style="text-align:justify;">PyTrx has been developed with object-oriented design, meaning that the core functions are wrapped in callable-objects, which make it <strong>accessible to beginners in programming</strong> whilst also serving those more experienced. </p>

<img class="alignnone size-full wp-image-7666" src="https://pennyhow.files.wordpress.com/2020/02/krone_dense_velos.jpeg" alt="Ice velocities from Kronebreen" width="800" align="aligncenter" /><br> *Demonstration of PyTrx's dense feature-tracking and georectification capabilities (<a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">from our Frontiers publication</a>). The sequence shows an early season speed-up at the terminus of the glacier*

<p style="text-align:justify;">The following main functions can be performed with the toolset: <strong>dense template matching and sparse Optical Flow methods for deriving velocities</strong>, <strong>automated detection of area features</strong> (such as supraglacial lakes), <strong>manual delineation of area and line features</strong> (e.g. meltwater plume footprints, terminus position), and <strong>camera calibration and optimisation</strong> for refining the georectification of measurements from the images.</p>

<hr>

<h2> The origin of PyTrx </h2>

<p style="text-align:justify;"><strong>PyTrx came about as we wanted to derive measurements from time-lapse imagery</strong>, which I had collected from tidewater glaciers in Svalbard as part of my PhD. However, <strong>we couldn't find any openly available toolset that met our needs.</strong> There are a handful of toolsets for processing ice velocities from time-lapse imagery (see <a href="http://imgraft.glaciology.net/" target="_blank" rel="noopener">ImGRAFT</a>, <a href="https://www.lancaster.ac.uk/staff/jamesm/software/pointcatcher.htm" target="_blank" rel="noopener">Pointcatcher</a> and <a href="https://tu-dresden.de/bu/umwelt/geo/ipf/photogrammetrie/forschung/forschungsprojekte/emt/?set_language=en" target="_blank" rel="noopener">EMT</a> - three great examples), but we wanted to also process other types of measurements, such as meltwater plume footprint extents, supraglacial lake areas, and changes in terminus position. </p>

<img class="alignnone size-full wp-image-7668" src="https://pennyhow.files.wordpress.com/2020/02/plume_projections.jpg" alt="Delineating meltwater plume footprints using PyTrx" width="800" align="aligncenter" /><br> *Example showing changes in meltwater plume extent distinguished from time-lapse imagery of Kronebreen using PyTrx (<a href="https://dx.doi.org/10.3389/feart.2020.00021" target="_blank" rel="noopener">from our Frontiers publication</a>). The surface expression of the meltwater plume has been tracked through images captured on 5 July 2014 at 18:00 (A), 20:00 (B), and 22:00 (C) to demonstrate part of its diurnal recession. Each plot shows the plume definition in the image plane (top) and its translation to real-world coordinates and plotted onto a coinciding Landsat 8 satellite image (bottom)*

<p style="text-align:justify;">Additionally, most toolsets that we came across were programmed in a limited range of programming languages. We felt there was a need for a toolset in an open-source programming language for those who wanted an alternative that did not rely upon a licensed software. <strong>Before long, we realised there was a need for this toolset in the public domain, with growing interest from others</strong>; hence why we began focusing on finalising PyTrx as an operational package that anyone could use.</p>

<hr>

<h2> PyTrx citations </h2>

<p style="text-align:justify;">We are happy for others to use and adapt PyTrx for their own processing needs. If used, please cite the following key publication and Digital Object Identifier:</p>

<p style="text-align:justify;"><b>How et al. (2020) PyTrx: a Python-based monoscopic terrestrial photogrammetry toolset for glaciology. Frontiers in Earth Science 8:21, <a href="https://dx.doi.org/10.3389/feart.2020.00021">doi:10.3389/feart.2020.00021</a></b></p>
  
<p style="text-align:justify;">PyTrx has also been used in many applications in glaciology. Please see our <a href="https://github.com/PennyHow/PyTrx/blob/master/README.md">Github repository readme</a> for more information on other publications, permission and acknowledgements.</p>
