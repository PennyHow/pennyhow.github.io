---
title: "pypromice available through conda"
date: 2023-11-14 00:00
categories:
  - blog
tags: 
  - greenland
  - pypromice
  - python
---

October has been a chaotic month with many parts of my job converging. Firstly, we reached a big milestone with [pypromice](https://github.com/GEUS-Glaciology-and-Climate/pypromice), the Python package for all our automated weather station (AWS) processing in the [PROMICE and GC-Net](https://promice.org/) network. **Milestone reached: pypromice is now on conda-forge**. This means that pypromice is installable through [conda](https://anaconda.org/conda-forge/pypromice) like so:

```
conda install pypromice -c conda-forge
```

This has been a long process that began as a suggestion in the [review of pypromice](https://github.com/openjournals/joss-reviews/issues/5298) through the [Journal of Open Source Software (JOSS)](https://joss.theoj.org/papers/10.21105/joss.05298). Although it was not necessary for the review, we wanted to put pypromice on conda-forge - it was something I had never done before and was curious to see what the process was like.

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/nuk_b_oct23.jpg?raw=true" alt="The newly-installed NUK-B station" width="1500" align="aligncenter" /><br> *An example of one of our weather stations in the PROMICE network. This is the newly installed NUK-B weather station, which we installed at the beginning of the month. NUK-B (NUK bedrock) forms a transect with our two other stations on the nearby Qamanaarsuup Sermia, NUK-U (NUK upper) and NUK-L (NUK lower)*

The first step was to ensure that all pypromice's dependencies were also available as conda packages. This was fine for all but one package - [pyDataverse](https://pydataverse.readthedocs.io/en/latest/). We use Dataverse to store and mint all of our AWS datasets with citeable DOIs (see our data [here](https://doi.org/10.22008/FK2/IW73UU)), so pyDataverse is used in our package to access up-to-date versions of our AWS datasets through the Dataverse API. Getting [pyDataverse on conda-forge](https://anaconda.org/conda-forge/pydataverse) was straightforward and fun to work with the developers.

After that, we started working on readying pypromice for conda-forge. The main thing was just generating the build from the already-existing pypi distribution of pypromice. In order to do so, the meta .yaml file can be generated initially using the `grayskull` Python package, like this:

```
grayskull pypi pypromice
```

There were some hiccups with the build as pypromice has CLI functionality, which previously was mapped in the package using a `bin/` directory that was defined in the `setup.py` package build. However, after a first review this needed to be changed to map the CLI functionality with `entry_points`. This took some time, as I also took the opportunity to do some directory and file restructuring in pypromice.

<img src="https://github.com/PennyHow/pennyhow.github.io/blob/master/assets/images/nuk_b_icebergs_oct23.jpg?raw=true" alt="Icebergs and bergy bits in Nuuk Fjord" width="1500" align="aligncenter" /><br> *Icebergs and bergy bits in Nuuk Fjord. This was the majority of the view in the helicopter back from installing NUK-B at the top of the fjord*

Once accepted, we then had to wait for the [conda-forge feedstock for pypromice](https://github.com/conda-forge/pypromice-feedstock) to be generated. This feedstock automatically generates new builds from new pypromice versions, which can be reviewed and accepted through pull requests. Once merged, the feedstock updates with the new build. It's a slick workflow that requires minimal effort on my side - just a quick check.
