---
layout: page
title: Post-Doctoral
permalink: /research/post-doctoral
date: 2019-03-10 16:51
author: pennyhow
comments: false
---
<p style="text-align:justify;">I was employed at the University of York as a post-doctoral researcher, working for the project <a href="https://archivalpolarphotography.wordpress.com" target="_blank" rel="noopener noreferrer"><span style="text-decoration:underline;"><strong>LEAPP (Leverhulme-funded Archival Polar Photography)</strong></span></a>. LEAPP is an interdisciplinary project between the Department of Environment and Geography and the Department of Computer Science, looking at extending records of past glacier change using archive photography.</p>


<hr />

<h4>Motivation</h4>
[caption id="attachment_61" align="alignleft" width="400"]<img class=" wp-image-61" src="https://archivalpolarphotography.files.wordpress.com/2018/12/p53_43_0432-master_copyright.jpg?w=300" alt="Archive image of Greenland from the SPRI Picture Library" width="400" height="323" /> <a href="https://www.spri.cam.ac.uk/picturelibrary/" target="_blank" rel="noopener noreferrer">SPRI Picture Library</a> image from the British Arctic Air Route Expedition (BAARE) of East Greenland in 1930-31 (Copyright: SPRI, University of Cambridge)[/caption]
<p style="text-align:justify;">Changes in ice sheets and glaciers are visible signals of climate change. This change is primarily monitored using satellite imagery, with the first earth observations using satellite technology in 1972. However, past glacier change is inherently difficult to observe before the satellite era. Therefore it is important to expand records of glacier change using other approaches.</p>
<p style="text-align:justify;">Historical photographs, captured on past expeditions and exploration attempts, are key to unlocking past records of glacier change as they could provide snapshots into past glacier conditions. The Scott Polar Research Institute (SPRI), Cambridge University, houses a Picture Library with one of the most comprehensive collections of polar imagery in the world that extends back to the Scott and Shackelton expeditions of the early 1900's. These records can be used to extend records of glacier change by several decades and would aid in more robust predictions of future glacier and climatic change.</p>
<p style="text-align:justify;">Measurements can be made from these historical photographs using photogrammetry and computer vision techniques, which are fields of computer science for obtaining useful information from optical imagery. The use of these techniques in Glaciological research has boomed in recent years with advancements in camera technology.</p>


<hr />

<h4 style="text-align:justify;">My project contribution</h4>
I focused on two points of interest in this research during my time with the LEAPP project:
<ol>
	<li>Extracting information from an image set of East Greenland collected in 1930-31 during the British Arctic Air Route Expedition (BAARE)</li>
	<li>Compiling and reviewing current photogrammetry and computer vision techniques used in Glaciology</li>
</ol>
[caption id="attachment_7585" align="alignleft" width="1409"]<img class="alignnone size-full wp-image-7585" src="https://pennyhow.files.wordpress.com/2019/03/baare_images.png" alt="BAARE image locations" width="1409" height="836" /> Determining the location of each image captured on one of BAARE's flight lines, marked by the red points plotted on the map. The green points denote ground control points, which are distinct features that have corresponding positions between the historical imagery and the real world scene[/caption]
<p style="text-align:justify;">Details of the Greenland coastline in 1930-1931 have been impressively preserved in the glass plate photography captured on BAARE, an expedition primarily focused on surveying the east coast of Greenland. Repeat photographs of certain glaciers could be used to reconstruct three-dimensional models that could inform us about changes in glacier thickness. In order to achieve this, I looked at determining the location of each historical image, and points in the scene that can be matched to known xyz coordinates in the scene (also referred to as ground control points).</p>
<p style="text-align:justify;">I also looked at reviewing the plethora of glaciological research that implements photogrammetry and computer vision approaches to best inform the LEAPP project of suitable techniques and pathways to extracting information from historical imagery. This included trawling through past literature and compiling common trends and perspectives between glaciology, photogrammetry and computer vision. The information gathered has been written up as a technical summary of the best approaches for deriving measurements and information from glacial imagery.</p>


[caption id="attachment_7586" align="alignnone" width="5997"]<img class="alignnone size-full wp-image-7586" src="https://pennyhow.files.wordpress.com/2019/03/pointseed2_fullframeall.jpg" alt="Point seeding in glacial imagery" width="5997" height="2789" /> Point seeding in glacial imagery to assess the benefit of using images that have been subjected to histogram equalisation. Two algorithms are used here (Harris corner detection and Shi-Tomasi corner detection) to detect distinct features on the surface of Kronebreen, a tidewater glacier in Svalbard. Images that have been subjected to histogram equalisation enhance the contrast of corner features in the image plane, and therefore more points can be seeded using the corner feature detection algorithms.[/caption]
