---
layout: page
title: Early work
date: 2015-06-11 09:27
author: pennyhow
comments: true
categories: []
---
<hr />

<h4>Examining short-term controls on glacier movement using time-lapse photography</h4>
<i>MSc (by research) supervised by Peter Wynn, Mike James and Hugh Tuffen (Lancaster University)</i>
<h5>Time-lapse in glaciology</h5>
<p style="text-align:justify;">The application of time-lapse cameras in glaciology has boomed over the past 10 years because of the rapid development in camera technology, which enables worldwide monitoring of glacier dynamics using high-resolution, consistent image databases. The specific applications to glaciology are currently limited, with a large focus on measuring glacier velocity and monitoring calving dynamics. The techniques involved in extracting quantitative data from images need to be improved to continue the development of time-lapse applications.</p>
<p style="text-align:justify;">Pointcatcher is a Matlab-based software, which was originally developed to calculate the velocity of lava flows. Its semi-automated tracking is useful for maintaining accurate tracks throughout a sequence. Here, it is used to determine surface velocities at a slow-moving glacier in Iceland. Sólheimajökull is an outlet of the Mýrdalsjökull ice cap, which overlies Katla volcano. Katla provides a set of additional influences on glacier movement, namely an additional source of meltwater at the glacier bed which could enhance basal sliding. The velocities from the time-lapse are used to examine the short-term influences on glacier movement, including the influence of subglacial geothermal activity.</p>


[caption id="attachment_324" align="aligncenter" width="1000"]<a href="https://pennyhow.files.wordpress.com/2015/06/24and12hour_tracks.jpg" target="blank" rel="noopener noreferrer"><img class="wp-image-324" src="https://pennyhow.files.wordpress.com/2015/06/24and12hour_tracks.jpg?w=1000" alt="Glacier features tracks on Sólheimajökull (green taken from a 24-hour interval sequence, and yellow taken from a 12-hour interval sequence" width="1000" /></a> Glacier features tracks on Sólheimajökull (green taken from a 24-hour interval sequence, and yellow taken from a 12-hour interval sequence)[/caption]
<h5>The processes behind time-lapse photography</h5>
<p style="text-align:justify;">Deriving measurements of glacier velocity from a time-lapse sequences is a two-step process: glacier feature tracking and image registration. Velocities are determined using glacier feature tracking, tracing common surface features (such as crevasses or dirt cones) by matching pixel texture through image pairs. This is semi-automated, using normalised cross-correlation to automatically track features, and manual interaction to update the correlation template and adjust point positions where needed. This ensures sub-pixel tracking on an evolving surface over long timescales.</p>
<p style="text-align:justify;">False movement may be introduced where there are changes in the camera or sensor parameters, such as camera position and pointing direction. This is commonly small camera rotations resulting from wind vibration, thermal effects or settling of the installation. Such changes in the reference image coordinate system can be determined by identifying and tracking image features in areas of static topography. The camera location and the camera model (representing the camera's lens distortion and sensor alignment) are used to transform these two-dimensional tracks into three-dimensional rotations around the camera's horizontal (omega), vertical (phil) and optic axes (kappa). The rotations can then be used to correct for false movement in the glacier feature tracks.</p>
<p style="text-align:justify;">The velocities derived from the glacier feature tracking can be transformed to real world measurements (e.g. metres per day) using a 3D model of the target surface (e.g. a digital elevation model - DEM). Relative (pixel) velocities are adequate for the purpose of this study as the aim is to examine the short-term drivers of glacier movement.</p>

<h5>Findings</h5>
<p style="text-align:justify;">Images were collected over two consecutive summers in 2012 and 2013. The velocities derived from these images were compared to air temperature and precipitation to examine the influence of top-down forcing (i.e. production of water at the surface which is delivered to the bed and causes sliding via cavity/channel overpressurisation). Bottom-up forcing refers to sliding induced by meltwater produced at the bed, which is associated with geothermal activity from Katla in this instance. It is difficult to directly measure geothermal basal melting, so it is indirectly monitored through seismic activity and the water depth and conductivity from the main river outlet. An increase in water with a high solute content (i.e. high conductivity) may indicate enhanced geothermal basal melting.</p>


[caption id="attachment_334" align="aligncenter" width="1024"]<a href="https://pennyhow.files.wordpress.com/2015/06/2013_figure-e1434449452449.jpeg" target="_blank" rel="noopener noreferrer"><img class="size-large wp-image-334" src="https://pennyhow.files.wordpress.com/2015/06/2013_figure-e1434449452449.jpeg?w=1024" alt="Results from summer 2013. Over the 2013 season,  Sólheimajökull moved approx. 13m down glacier. (Movement data obtained from feature tracking, uncertainty accounts for RMS error after registration, river water depth and conductivity data collected from the glacial outlet Jökulsá á Sólheimasandi by the Icelandic Met Office, seismic activity data collected from inside  the ice cap water shed and ice shed of Sólheimajökull, temperature and precipitation data collected from an in-situ TinyTag sensor and Pluvimate rain gauge)." width="1024" height="521" /></a> Results from summer 2013. Over the 2013 season, Sólheimajökull moved approx. 13m down glacier. (Movement data obtained from feature tracking, uncertainty accounts for RMS error after registration, river water depth and conductivity data collected from the glacial outlet Jökulsá á Sólheimasandi by the Icelandic Met Office, seismic activity data collected from inside the ice cap water shed and ice shed of Sólheimajökull, temperature and precipitation data collected from an in-situ TinyTag sensor and Pluvimate rain gauge).[/caption]
<p style="text-align:justify;">An inverse relationship between water volume and conductivity is common in a glacial system with no geothermal influence. Here, the conductivity of the water coming out of Sólheimajökull fluctuates independent of changes in water depth. This suggests that geothermal melting at the glacier bed is producing a solute-rich injection of melt into the subglacial system that is causing sliding via overpressurisation. Little supporting evidence can be gained from the seismicity data as there are few unifying links between tremors and glacier movement.</p>
<p style="text-align:justify;">Top-down forcing appears to be the prevailing influence on glacier movement at Sólheimajökull, routing water from the surface to the bed and inducing sliding through elevated water pressure. This is based on the strong links between the relative glacier movement derived from the time-lapse sequences, air temperature and precipitation. Bottom-up forcing could not be observed from the available data, but fluctuations in water conductivity and supporting observations in meltwater isotopes (Wynn et al., 2015) suggest that the geothermal activity from Katla does play a part in the dynamics of Sólheimajökull.</p>

<h5>Further Reading</h5>
<span style="text-decoration:underline;"><strong><a href="https://www.cambridge.org/core/services/aop-cambridge-core/content/view/23EC92804DE7C5EED7229D0ACE31D90B/S0022143016000277a.pdf/pointcatcher_software_analysis_of_glacial_timelapse_photography_and_integration_with_multitemporal_digital_elevation_models.pdf" target="_blank" rel="noopener noreferrer">James, How and Wynn (2016) J. Glaciol.</a>
</strong></span><i>- The associated publication with this work</i>

<span style="text-decoration:underline;"><strong><a href="http://www.lancaster.ac.uk/staff/jamesm/software/pointcatcher.htm" target="_blank" rel="noopener noreferrer">Pointcatcher</a></strong></span>
<i>- Mike James' Pointcatcher software, freely available</i>

<strong><span style="text-decoration:underline;"><a href="http://www.sciencedirect.com/science/article/pii/S0009254114006135" target="_blank" rel="noopener noreferrer">Wynn et al. (2015) Chem. Geol.</a></span></strong>
<i>- Paper showing geothermal signal in meltwater isotopes at Sólheimajökull</i>

<hr />

<h4>Explosive cyclicity from the 2011 eruption of Puyehue-Cordón Caulle, Chile</h4>
<i>Internship supervised by Hugh Tuffen and Mike James (Lancaster University)</i>
<h5>The eruption of the Puyehue-Cordón Caulle Volcanic Complex (PCCVC)</h5>
<p style="text-align:justify;">The Puyehue-Cordón Caulle Volcanic Complex (PCCVC) recently erupted in June 2011, with huge Plinian columns of emissions filling the stratosphere that grounded many flights in the southern hemisphere for several days. Both pyroclastic and effusive behaviours were observed, which is a unique type of eruption that has rarely been seen. The eruption dramatically altered the surrounding area, coating the landscape in a thick layer of ash.</p>
<p style="text-align:justify;">The volcanic activity later calmed to semi-continual ash jetting punctuated with abrupt Vulcanian phases, causing violent explosions of larger tephra and lava bombs. This activity occurred at several minor vents in the crater rather than one single vent, and was captured on video in January 2012. These videos are very valuable as direct observations of volcanic eruptions are often difficult and dangerous to obtain. The videos were used here to examine the explosive behaviour of PCCVC at first-hand.</p>

<h5>Current understanding of vent dynamics</h5>
<p style="text-align:justify;">A volcanic vent is generally defined as an opening in the Earth's crust where magma and volcanic gases escape. Magma rises to the vent opening through the magma chamber, which periodically empties in repeated cycles of eruptions. Explosive activity occurs when gases within the magma are trapped beneath the surface, allowing pressure to build up till a given threshold where the material can no longer be contained by the surrounding bedrock. Secondary vents and multiple vent systems exist where these high pressures exploit weaknesses in the bedrock to form networks of vent systems.</p>
<p style="text-align:justify;">It is suspected that PCCVC has a vent architecture that allows both explosive and effusive behaviours, which has not been documented before now. Efficient degassing occurs through clusters of tuffisite veins, which act as 'volcanic valves' that can interchangeably open and close to allow degassing from the main magma chamber. These produce a near-constant emission of material as they can withstand significant overpressures. Explosive activity occurs when the overpressure threshold is exceeded, producing volcanic bombs and ash-rich emissions.</p>


[caption id="attachment_263" align="aligncenter" width="680"]<a href="https://pennyhow.files.wordpress.com/2015/06/schipper_timeline.jpg" target="_blank" rel="noopener noreferrer"><img class="wp-image-263 size-full" src="https://pennyhow.files.wordpress.com/2015/06/schipper_timeline.jpg" alt="Timeline of vent activity from video sequence: (a) is a video still of the crater with the annotated vent clusters; (b) shows the activity at each vent cluster (taken from Schipper et al., 2013)" width="680" height="683" /></a> Timeline of vent activity from video sequence: (a) is a video still of the crater with the annotated vent clusters; (b) shows the activity at each vent cluster (from Schipper et al., 2013)[/caption]
<h5>Findings</h5>
<p style="text-align:justify;">Close examination of the videos shows that the vein architecture is responsible for the type of volcanic activity, with the strength and frequency of explosive episodes controlled by their efficiency in de-gassing.</p>
<p style="text-align:justify;">Short-term cycles in explosive activity are evident, which are controlled by progressive vein evolution. Short-term links between the vents exist, which are associated with effusive activity. This regime lasts for a few minutes, steadily progressing from light gas emissions to dark ash emissions. Incandescent explosive activity follows, as an abrupt overhaul in the vein architecture occurs in response to over-pressure buildup. The effusive regimes change each time after an architecture overhaul, which is why the vents appear to open and close like valves as they become active and dormant with each regime.</p>
<p style="text-align:justify;">Infrared footage was used to track lava bomb trajectories, which could be traced back to the vent source. A front cluster and back cluster was distinguished, which commonly behave independent of one another during effusive phases. Activity from these two clusters coincided during marked incandescent phases, suggesting that highly explosive activity originates from a source deep in the vein architecture.</p>

<h5>Further Reading</h5>
<strong><span style="text-decoration:underline;"><a href="http://www.sciencedirect.com/science/article/pii/S0377027313001790" target="_blank" rel="noopener noreferrer">Schipper et al. (2013) J. Volcanol. Geoth. Res.</a></span></strong>
<i>- Publication related to this project</i>

<strong><span style="text-decoration:underline;"><a href="http://www.bbc.co.uk/programmes/p00v4wkb" target="_blank" rel="noopener noreferrer">BBC Volcano Live segment on Puyehue</a></span></strong>
<i>- Hugh Tuffen talking about PCCVC with footage of the eruption</i>

<strong><span style="text-decoration:underline;"><a href="http://onlinelibrary.wiley.com/doi/10.1029/2011GL050404/full" target="_blank" rel="noopener noreferrer">Taddeucci et al. (2012) Geophys. Res. Lett. </a></span></strong>
<i>- A great example of lava bomb tracking at a Strombolian eruption</i>

<hr />
