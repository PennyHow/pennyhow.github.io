---
title: "pypromice"
permalink: /pypromice/
author_profile: true
---

<a href='https://badge.fury.io/py/pypromice'> <img src='https://badge.fury.io/py/pypromice.svg' alt='PyPI version' /></a> <a href='https://anaconda.org/conda-forge/pypromice'> <img src='https://anaconda.org/conda-forge/pypromice/badges/version.svg' alt='Anaconda-Server Badge' /></a> <a href='https://anaconda.org/conda-forge/pypromice'> <img src='https://anaconda.org/conda-forge/pypromice/badges/platforms.svg' alt='Anaconda-Platform Badge' /></a> <a href='https://www.doi.org/10.22008/FK2/3TSBF0'> <img src='https://anaconda.org/conda-forge/pypromice/badges/version.svg' alt='Anaconda-Server Badge' /></a> <a href='https://www.doi.org/10.22008/FK2/3TSBF0'> <img src='https://img.shields.io/badge/Dataverse DOI-10.22008/FK2/3TSBF0-orange' alt='Dataverse DOI' /></a> <a href='https://doi.org/10.21105/joss.05298'> <img src='https://joss.theoj.org/papers/10.21105/joss.05298/status.svg' alt='JOSS DOI' /></a> <a href='https://pypromice.readthedocs.io/en/latest/?badge=latest'> <img src='https://readthedocs.org/projects/pypromice/badge/?version=latest' alt='Documentation Status' /></a><br>


<p style="text-align:justify;">I am one of the developers of <a href="https://github.com/GEUS-Glaciology-and-Climate/pypromice">pypromice</a>, which is designed for processing and handling <a href="https://promice.org">PROMICE (Programme for Monitoring of the Greenland Ice Sheet) and GC-Net (Greenland Climate Network)</a> automated weather station data.</p>

<p style="text-align:justify;">It is envisioned for pypromice to be the go-to toolbox for handling and processing PROMICE and GC-Net data, along with other weather station datasets. New releases of pypromice are uploaded alongside PROMICE weather station data releases to our <a href="https://dataverse.geus.dk/dataverse/PROMICE">Dataverse</a> portal for transparency purposes and to encourage collaboration on improving our data. Please visit the pypromice <a href="https://pypromice.readthedocs.io/en/latest/?badge=latest">readthedocs</a> for more information.</p>

<hr>

<h2> How pypromice came to be </h2>

<p style="text-align:justify;">pypromice first came to be in June 2022 as an merge of repositories that handled and processed data from automated weather stations. Lots of floating code suddenly had a home under a unifying source. </p>

<p style="text-align:justify;">There were a couple of motivations to do this, the main one being that our department had recently <a href="https://eng.geus.dk/about/news/news-archive/2020/december/geus-takes-over-american-climate-stations-on-the-greenland-ice-sheet">assumed responsibility of a new set of weather stations</a> called GC-Net, which are a different station design. Our current processing only accomodated for our current PROMICE weather stations, and therefore the workflow needed to be built out in order to process data from these new additions.</p>

<p style="text-align:justify;">Another motivation was that the general users of the PROMICE weather station data were those from the scientific research community, mainly cryospheric sciences. Yet, weather observations are incredibly valuable datasets across many disciplines. We needed a better handle of our processing workflow and the outputted data formatting in order to reach other discipines and increase the usability of our data.</p>

<p style="text-align:justify;">Finally, one of the big long-term goals with the PROMICE weather station network was for observations to be processed in near-real-time. In order to do so, the current processing needed to be repackaged into something that was easily deployable and computationally efficient.</p>

<hr>

<h2> What pypromice can do </h2>

<p style="text-align:justify;">The main thing that pypromice can do is perform all of the processing steps to transform, correct, flag and derive measurements from a weather station's raw, original data. We process in three steps, from the raw, original data (which we call Level 0) to a user-friendly and finalised data product (called Level 3).</p>

<img class="alignnone size-full wp-image-7666" src="https://github.com/GEUS-Glaciology-and-Climate/geus-glaciology-and-climate.github.io/blob/master/assets/images/pypromice_process_design.png?raw=true" alt="pypromice processing workflow" width="800" align="aligncenter" /><br> *The workflow for pypromice's Level 0 to Level 3 weather station data processing*

<p style="text-align:justify;">In addition, pypromice has automated quality control functionality which flags and fixes weather station data, and post-processing capabilities to format weather station data for input to international weather observation and forecasting databases. Up-to-date PROMICE and GC-Net weather station datasets can also be called through pypromice's data fetching routines. This ensures that a user has the most recent PROMICE and GC-Net weather observations.</p>

<hr>

<h2> Features of pypromice </h2>

<ul>
	<li>Object oriented design for fast processing and handling different types of weather station (i.e. one-boom vs. two-boom, on ice vs. on bedrock</li>
	<li>Powered by .toml file configurations to adequately describe a weather station and its processing procedures</li>
	<li>Continuous integration with module unit testing and a "dress-rehearsal" of operational processing, which is triggered when any new changes are suggested through a pull request</li>
	<li>Thorough documentation through the scripts, with auto-doc generation hosted at <a href='https://pypromice.readthedocs.io/en/latest/?badge=latest'>readthedocs</a></li>
	<li>Distributed as a Python package through <a href="https://pypi.org/project/pypromice/">pypi</a> and <a href="https://anaconda.org/conda-forge/pypromice">conda-forge</a></li>
	<li>All pypromice releases backed up and citeable through the <a href='https://www.doi.org/10.22008/FK2/3TSBF0'>GEUS Dataverse</a></li>
</ul>

<hr>

<h2> Citing pypromice </h2>

<p style="text-align:justify;">If you intend to use our automated weather station datasets and/or pypromice in your work, please cite these publications below, along with any other applicable PROMICE publications where possible:</p>

<p style="text-align:justify;"><b>Fausto, R.S., van As, D., Mankoff, K.D., Vandecrux, B., Citterio, M., Ahlstrøm, A.P., Andersen, S.B., Colgan, W., Karlsson, N.B., Kjeldsen, K.K., Korsgaard, N.J., Larsen, S.H., Nielsen, S., Pedersen, A.Ø., Shields, C.L., Solgaard, A.M., and Box, J.E. (2021) Programme for Monitoring of the Greenland Ice Sheet (PROMICE) automatic weather station data, Earth Syst. Sci. Data, 13, 3819–3845, <a href="https://doi.org/10.5194/essd-13-3819-2021">https://doi.org/10.5194/essd-13-3819-2021</a></b></p>

<p style="text-align:justify;"><b>How, P., Wright, P.J., Mankoff, K., Vandecrux, B., Fausto, R.S. and Ahlstrøm, A.P. (2023) pypromice: A Python package for processing automated weather station data, Journal of Open Source Software, 8(86), 5298, <a href="https://doi.org/10.21105/joss.05298">https://doi.org/10.21105/joss.05298</a></b></p> 

<p style="text-align:justify;"><b>How, P., Lund, M.C., Nielsen, R.B., Ahlstrøm, A.P., Fausto, R.S., Larsen, S.H., Mankoff, K.D., Vandecrux, B., Wright, P.J. (2023) pypromice, GEUS Dataverse, <a href="https://doi.org/10.22008/FK2/3TSBF0">https://doi.org/10.22008/FK2/3TSBF0</a></b></p>  
