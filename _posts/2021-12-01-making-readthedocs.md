---
title: "Making Readthedocs for a Python package"
date: 2021-12-01 12:17
categories:
  - blog
tags: 
  - programming
  - python
  - readthedocs
  - github
  - sphinx
  - auto-documentation
  - open-source
---

<p style="text-align:justify;">A <strong>readthedocs page</strong> is handy when you wish to auto-generate online documentation for a package, such as in package releases or submitting code for peer review. Setting up a readthedocs page is well-documented online, with many step-by-step walkthroughs and guides. However, sometimes it is not straightforward and troubleshooting problems can be time-consuming.</p>

<p style="text-align:justify;">I'm going to outline the steps and focus on the less intuitive aspects of setting up readthedocs pages, not only for others to benefit from, but also for myself when I have to do this again in the future. I would suggest reading this guide alongside the official walkthrough on the readthedocs webpages.</p>


<h3>Formatting script documentation</h3>

<p style="text-align:justify;">So the first thing is to make sure that your scripts, or package, are held in a repository on Github and all of the documentation in your scripts are compatible for importing into a readthedocs page. </p>

<p style="text-align:justify;">The standard style for the documentation is reStructuredText. I had previously used reStructuredText to write the documentation for a package I released called <a href="https://github.com/PennyHow/PyTrx">PyTrx</a>. Whilst it was reasonbly straightforward, it looks pretty ugly in local scripts. </p>

<pre><code># Example from PyTrx, https://github.com/PennyHow/PyTrx

def getOGRArea(pts):
    """Get real world OGR polygons (.shp) from xyz poly pts 
    with real world points which are compatible with mapping 
    software (e.g. ArcGIS).

    :param pts: UV/XYZ coordinates of a given area shape
    :type pts: arr 
    :returns: List of OGR geometry polygons
    :rtype: list                           
    """                                           
    ring = ogr.Geometry(ogr.wkbLinearRing)
    for p in pts:
        if np.isnan(p[0]) == False:
            if len(p)==2:
                ring.AddPoint(int(p[0]),int(p[1]))
            else:                  
                ring.AddPoint(p[0],p[1],p[2])
    poly = ogr.Geometry(ogr.wkbPolygon)
    poly.AddGeometry(ring)
    return poly
</code></pre>
   
<p style="text-align:justify;">I have used this before for auto-generated documentation and I would not recommend it. There are alternatives that look much nicer, such as <a href="https://numpydoc.readthedocs.io/en/latest/format.html#docstring-standard">Numpy docstrings</a>, which is what I used on my most recent project.</p>

<pre><code># Example from pyBiblyser

def fetchAltmetrics(doi):
    """Fetch altmetrics from DOI
    
    Parameters
    ----------
    doi : str                           
      DOI string to search with
    
    Returns
    -------
    result : dict
      Altmetrics result
    """
    api = 'https://api.altmetric.com/v1/doi/'
    response = requests.get(api + doi)
    if response.status_code == 200:
        result = response.json()
    return result 
</code></pre>

<p style="text-align:justify;">It looks a lot nicer in local scripts, and the set-up for auto-generating documentation from the Numpy docstrings style is relatively simple (which we will look at later). There is also the option to use Google docstrings, which is also another visually pleasing alternative (see an example <a href="https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html">here</a>), although it does not have all of the functionality of Numpy docstrings, such as generating example scripts within the documentation. </p>


<h3>Initialising and populating the documentation pages</h3>

<p style="text-align:justify;">There are different packages that can be used to initialise the local build of the readthedocs files, namely <a href="https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html">        Sphinx</a> and <a href="https://docs.readthedocs.io/en/stable/intro/getting-started-with-mkdocs.html"> MkDocs</a>. I have generally gone with Sphinx, but MkDocs looks relatively similar and the workflow feels familiar. </p>

<p style="text-align:justify;">In the case of using Sphinx, it firstly needs to be installed using pip, following which you can initialise the build. It is best to make a new folder called 'docs' in the active directory where your scripts can be found.

<pre><code>pip install sphinx

mkdir docs

sphinx quickstart
</code></pre>

<p style="text-align:justify;">There is a prompt for several set-up parameters when initialising the build. One that I couldn't find much information about was the option of having source and build as separate directories. I had not come across this a couple of years ago when using Sphinx, so I think this is a new feature - by opting out of separate directories, the source files are automatically placed in the top directory of the 'docs' folder. </p>

<p style="text-align:justify;">Now, I am sure this is fine, but I wasn't sure if this was a problem for me later on when auto-generating documentation. So I kept the source and build as separate directories on this occassion. Once initialised, you can populate the source directory with pages (as .rst reStructuredText files). An Index.rst file should be created, which will be the radthedocs front page of the package and is where links to all your pages can be outlined.</p>

<pre><code>.. Index.rst contents

pyBiblyser
==========

.. toctree::
   :maxdepth: 2
   :caption: Contents:
   
   installation
   guide
   diversityindex
   modules
   acknowledgements

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
</code></pre>

<p style="text-align:justify;">So in this case, the package is called <a href="https://github.com/GEUS-Glaciology-and-Climate/PyBiblyser">PyBiblyser</a>, and a contents page will link to a page on installation, a package guide, information about the diversity index, an outline of the package modules, and acknowledgements. Links to the auto-generating documentation index will appear below this, along with a search tool</p>


<h3>Configuring the build</h3>

<p style="text-align:justify;">The <a href="https://docs.readthedocs.io/en/stable/config-file/index.html">configuration file</a> is the main hub for your pages build. This is located at docs/source/conf.py (if source and build are in separate directories), or docs/conf.py (if source and build are together). Parameters can be added here to configure the readthedocs pages</p>


<p style="text-align:justify;">I would say the three main components I altered here were the paths for reading the documentation from, the <strong>html_theme</strong> parameter and the <strong>extensions</strong> parameter. Paths should be added to the scripts on which auto-documentation should be implemented -- so, in my case, I wanted the paths in the top directory of the git repository to be included, so added this.</p>

<pre><code># paths from conf.py
sys.path.insert(0, os.path.abspath('../../'))
sys.path.insert(0, os.path.abspath('.'))
</code></pre>

<p style="text-align:justify;">The <strong>html_theme</strong> parameter is linked to the style of the readthedocs pages - <a href="https://sphinx-themes.org">there are a number of themes to choose from</a>, with the <strong>sphinx_rtd_theme</strong> being the classic readthedocs style. Other Sphinx packages can be added with the extensions parameter in order to configure components such as how auto-documentation is generated.</p>

<pre><code> # Extensions from conf.py
extensions = [
    'sphinx.ext.autodoc',	     # To generate autodocs
    'sphinx.ext.mathjax',           # autodoc with maths
    'sphinx.ext.napoleon'           # For auto-doc configuration
]

napoleon_google_docstring = False   # Turn off googledoc strings
napoleon_numpy_docstring = True     # Turn on numpydoc strings
napoleon_use_ivar = True 	     # For maths symbology
</code></pre>

<p style="text-align:justify;">There are many extensions to Sphinx (see <a href="https://www.sphinx-doc.org/en/master/usage/extensions/index.html"here</a> for the list), but the autodoc extension is <strong>essential</strong> for generating auto-documentation - do not forget it! In my case, I opted for auto-documentation to be generated from Numpy docstrings in my scripts.</p>


<h3>Importing and building in readthedocs</h3>

<p style="text-align:justify;">To import from the Github respository to readthedocs, you need to connect the repository to your readthedocs and allow readthedocs to pull from the repository. This is largely straightforward (see guide <a href="https://docs.readthedocs.io/en/stable/intro/import-guide.html">here</a>) apart from if you are pulling from a private repository in a Github organisation (which is what I was doing). After reading around, it doesn't appear like this is possible at the moment, so I had to make the repository public. From here, I could <a href="https://docs.readthedocs.io/en/stable/integrations.html">generate a webhook</a> for the repository, which allows the contents to be pulled to readthedocs.</p> 

<p style="text-align:justify;">Successfully building the readthedocs from the Github repository was probably the mosy fiddly and time-consuming parts for me. The auto-documentation is generated by running the package on a virtual machine; therefore, you have to specify how to run the package with two files - a readthedocs (.yaml. or .yml) setup file in the top directory; and a file containing requirements</p>

<p style="text-align:justify;">The readthedocs.yaml file specifies the virtual machine build. I kept this quite simple, but I understand this can cause problems in the future - it is best to specify the build (for instance, the operating system) to best copy the environment that the package was built in, and there are plenty of options, as documented <a href="https://docs.readthedocs.io/en/stable/config-file/vs.html">here</a>.</p>

<pre><code># File .readthedocs.yaml

build:
  image: latest

python:
  version: 3.7

requirements_file: docs/requirements.txt
</code></pre>

<p style="text-align:justify;">So in this instance, I have specified to build a Python 3.7 environment (as this is what I had coded the package in) with a set of requirements that I have provided the path to. The requirements file can either be a .txt list, or an environment .yml/.yaml file. These requirements should be the same as your package dependencies. I didn't list the package versions as I was having problems with the virtual environment build, but generally you should specify the version, or the minimum version, of each package.</p> 
<pre><code> 
# File docs/requirements.txt

bs4
numpy
pandas
pip
gender-guesser
habanero
pybliometrics
scholarly
</code></pre>


<h3>Troublshooting</h3>

<p style="text-align:justify;">You can check the status and troubleshoot problems effectively by checking the build log, as described <a href="https://stackoverflow.com/questions/65487163/python-sphinx-autodoc-not-rendering-on-readthedocs">here</a>. A common problem is errors in the imported dependencies - I had this problem and found that I needed to also specify pip as a requirement otherwise pip install could not be used. </p>

<p style="text-align:justify;">Another common problem is that the auto-documentation does not generate because it "cannot see" your documented scripts, in which case you need to check the specified paths in the conf.py file.</p>

<p style="text-align:justify;">Continue to build the readthedocs pages until you see the auto-documentation populated in the index and module index. This can be time-consuming to wait for each build, troubleshoot, edit, and try again - at least, I found it time-consuming. However, it is worth it. </p>

<p style="text-align:justify;">From here on, whatever you change in your package documentation will be reflected in your readthedocs. Enjoy!</p>

<hr>

<h3>Further reading</h3>

<p><a href="https://docs.readthedocs.io/en/stable/">The readthedocs homepage</a>, including a simple walkthrough</p>

<p><a href="https://brendanhasz.github.io/2019/01/05/sphinx.html">This post by Brendan Hasz</a> nicely details the set-up</p>

<p><a href="https://towardsdatascience.com/how-to-set-up-your-python-project-docs-for-success-aab613f79626">Another detailed walkthrough</a></p>

<p><a href="https://numpydoc.readthedocs.io/en/latest/format.html#docstring-standard">Numpydoc style guide</a></p>

<p><a href="https://stackoverflow.com/questions/65487163/python-sphinx-autodoc-not-rendering-on-readthedocs">This Stack Overflow forum</a> on troubleshooting when autodoc is not rendering on readthedocs</p>

<p><a href="https://docs.readthedocs.io/en/stable/config-file/index.html">Specifications for the configuration file</a></p>
