---
title: "Making a PyPI package"
date: 2020-02-02 20:35
categories: 
  - Programming
tags:
  - academia
  - Anaconda
  - conda
  - github
  - pip
  - Programming
  - PyPI
  - python
  - PyTrx
  - research
  - TestPyPI
  - velocity
---
<p style="text-align:justify;">Recently, I have had a paper accepted which presents PyTrx, a new Python toolset for use in glacial photogrammetry. Over the course of getting this published, it has been suggested by co-authors and reviewers alike to use a package manager for easy download and implementation of PyTrx. <strong>I therefore wanted to package the toolset up for distribution via PyPI ('pip'),</strong> thus making is easily accessible to other Python users with the simple command <code>pip install pytrx</code>. Whilst I found the tutorials online informative, there were some pitfalls which I found hard to solve with the given information. So here is an account of how I got my package on PyPI. The associated files for the PyTrx package are available on a branch of <a href="https://github.com/PennyHow/PyTrx/tree/distribution" target="_blank" rel="noopener"><strong><span style="text-decoration:underline;">PyTrx's GitHub </span><span style="text-decoration:underline;"><strong>repository</strong>,</span></strong></a> if you want to see this walkthrough in action.</p>

<h2>Defining the package files</h2>
<p style="text-align:justify;">First and foremost, the file structure of the toolset is crucial to it being packaged up correctly. The top directory should contain <strong>a folder</strong> containing your package, and several other files containing the necessary setup information:</p>

<pre><code> master_folder
   - PyTrx
   - LICENSE.txt
   - README.md
   - setup.py </code></pre>
<p style="text-align:justify;">This is one of the first slip-ups I made, putting all my toolset scripts in the tol directory rather than a folder of its own. If the Python scripts that make your package are not placed in their own folder then they will not be found when it comes to compiling the package.</p>
<p style="text-align:justify;">So let's go through each of these elements, beginning with the folder that contains the Python scripts we wish to turn into a PyPI package. <strong>An initialisation file needs to be created</strong> in this folder in order to import the directory as a package. This is simply an empty Python script called <code>__init__.py</code>, so our folder structure will look a bit like this now:</p>

<pre><code> master_folder
   - PyTrx
       - __init__.py
   - LICENSE.txt
   - README.md
   - setup.py </code></pre>
<p style="text-align:justify;">Moving on to the <code>LICENSE.txt</code> file, <strong>it is important to define a license with any Python package</strong> that is publicly distributed in order to inform the user how your package can be used. This can simply be a text file containing a copied license. A straightforward and popular license for distributing code is the <span style="text-decoration:underline;"><strong><a href="https://opensource.org/licenses/MIT" target="_blank" rel="noopener">MIT license</a></strong></span> which allows code to be used and adapted with appropriate credit, but there are greate guides for choosing a license appropriate for you online (e.g. <span style="text-decoration:underline;"><strong><a href="https://choosealicense.com/" target="_blank" rel="noopener">choosealicense.com</a></strong></span>). This file has to be called 'license' or 'licence' (uppercase or lowercase) so that it is recognised when it comes to compiling the package.</p>
<p style="text-align:justify;">Similarly with the <code>README.md</code> file, this has to be called 'readme' specifically so that it is recognised when it comes to compiling the package. This file contains a long description of the Python package. It might be the case that you already have a <code>README.md</code> file if you have hosted your scripts on GitHub, in which case you can merely adopt this as your readme. Just remember that this should be hardcoded in HTML code, and <strong>the readme file will form the main description of your package that people will read when they navigate to the package's PyPI webpage</strong>.</p>
<p style="text-align:justify;">And finally the <code>setup.py</code>. <strong>The setup file is probably the trickiest file to define, but the most important</strong> as here we outline all of the metadata associated with our Python package; including the package's recognised pip name (i.e. the one used in the command <code>pip install NAME</code>), its version, author and contact details, keywords, short package description, and dependencies. Here is PyTrx's <code>setup.py</code> file to serve as an example:</p>

<pre><code>import setuptools

with open("README.md", "r") as fh:
    long_description = fh.read()

setuptools.setup(
    name="pytrx", 
    version="1.1.0",
    author="Penelope How",
    author_email="pennyruthhow@gmail.com",
    description="An object-oriented toolset for calculating velocities, surface areas and distances from oblique imagery of glacial environments",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/PennyHow/PyTrx",
    keywords="glaciology photogrammetry time-lapse",
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Development Status :: 5 - Production/Stable",
        "Intended Audience :: Science/Research",
        "Natural Language :: English",
        "Operating System :: OS Independent",
    ],
    install_requires=['glob2', 'matplotlib', 'numpy', 'opencv-python&gt;=3', 'pillow', 'scipy'],
    python_requires='&gt;=3',
)</code></pre>
<p style="text-align:justify;">Most of the variables are straightforward to adapt for your own package <code>setup.py</code> file. The ones to watch out for are the <code>classifiers</code> variable where metadata flags are defined, and the <code>install_requires</code> variable where the package's dependencies are. PyPI offers a good resource that lists all of the possible classifiers you can add to the <code>classifiers</code> variable.</p>
<p style="text-align:justify;">Finding out how to define dependencies was a little trickier though, as the <span style="text-decoration:underline;"><strong><a href="https://packaging.python.org/tutorials/packaging-projects/" target="_blank" rel="noopener">main PyPI tutorial</a></strong></span> does not address this. <span style="text-decoration:underline;"><strong><a href="https://python-packaging.readthedocs.io/en/latest/dependencies.html" target="_blank" rel="noopener">This page</a></strong></span> gave a brief outline of how to define them with the <code>install_requires</code> variable, but I found that I still had problems in the subsequent steps with package incompatibilities. My main problem was that I had largely worked with conda rather than pip for managing my Python packages, so there were a number of discrepancies between the two in configuring dependencies with PyTrx. My main challenge was finding a balance with OpenCV and GDAL, two notoriously difficult packages to find compatible versions for - I had managed this with conda, finding two specific versions of these packages to configure a working environment. In pip, I found this proved much harder. <strong>The package versions used in conda were not the same for pip</strong>, and there wasn't an official repository for OpenCV, only an unofficial repository called <span style="text-decoration:underline;"><strong><a href="https://pypi.org/project/opencv-python/" target="_blank" rel="noopener">opencv-python</a></strong></span>. We'll learn more about testing dependency set-ups a bit later on, but for now, just be aware to check that each PyPI package dependency is available and use the <code>&gt;=</code> or <code>&lt;=</code> to define if the package needs to be above or below a certain version. <strong>It is generally advised not to pin a dependency to a specific version</strong> (i.e. <code>==</code>), I guess because it reduces the flexibility of the package installation for users.</p>

<h2>Generating the distribution files</h2>
<p style="text-align:justify;">Once we have all of our files, we can now compile our package and generate the distribution files that will be eventually uploading to <strong><span style="text-decoration:underline;"><a href="https://test.pypi.org/" target="_blank" rel="noopener">TestPyPI</a></span></strong> and <span style="text-decoration:underline;"><strong><a href="https://pypi.org/" target="_blank" rel="noopener">PyPI</a></strong></span>. <strong>It is advised to use TestPyPI to test your package distribution before doing the real deal on PyPI</strong>, and I found it incredibly useful as an apprehensive first-time uploader.</p>
<p style="text-align:justify;"><strong>If you do decide to test your package on TestPyPI, it is good etiquette to change the name of your package</strong> (defined in <code>setup.py</code>) to something very unique - there are many test packages on TestPyPI, and although they delete test packages on a regular basis, there are plenty of package names that yours could clash with. In the case of PyTrx, I defined the package name as <span style="text-decoration:underline;"><strong><a href="https://test.pypi.org/project/pytrxhow/" target="_blank" rel="noopener">pytrxhow</a></strong></span> (the package name with my surname), that way there was no chance of using a name that had already been taken. Additionally, you should take your dependencies out of the <code>setup.py</code> file as often the same packages do not exist on TestPyPI and therefore are not an accurate reflection of how your package dependencies will look on PyPI.</p>
<p style="text-align:justify;">To generate the distribution files, two packages need to be installed into your Python environment, <code>setup-tools</code> and <code>wheel</code>. I already had versions of these packages in my conda environment, but I updated them using the same command (in Anaconda Prompt) as if I wanted to install them:</p>

<pre><code>conda install setup-tools wheel</code></pre>
<p style="text-align:justify;">After these are installed, navigate to the directory where all of your files are (i.e. in master_folder) using the <code>cd</code> command, and run the following command to build your distribution files for TestPyPI:</p>

<pre><code>python3 setup.py sdist bdist_wheel</code></pre>
<p style="text-align:justify;">This should generate two folders containing files that look something like this:</p>

<pre><code>master_folder
   - PyTrx
       - __init__.py
   - LICENSE.txt
   - README.md
   - dist
       - pytrx-1.1.0-py3-none-any.whl
       - pytrx-1.1.0.tar.gz
   - pytrx.egg-info
       - PKG-INFO
       - SOURCES.txt	
       - dependency_links.txt	
       - requires.txt	
       - top_level.txt
   - setup.py </code></pre>
<p style="text-align:justify;">The <code>dist</code> and <code>egg-info</code> folder should contain all of the information inputted into the <code>setup.py</code> file, so it's a good idea to check through these to see if the files are populated correctly. The <code>SOURCES.txt</code> file should contain a list of the paths to all of the relevant files for making your packages. If you have taken out your dependencies, then the <code>requires.txt</code> file should be empty.</p>

<h2>Testing the distribution</h2>
<p style="text-align:justify;"><strong>There are two ways to test that the distribution files work: 1. using TestPyPI to trial the distribution and the 'look' of the PyPI entry, and 2. using the setup.py file to test the package installation in your local environment (including dependency solving).</strong> Beginning with the test on TestPyPI, start by creating an account on TestPyPI and creating an <strong><span style="text-decoration:underline;"><a href="https://test.pypi.org/manage/account/#api-tokens" target="_blank" rel="noopener">API token</a></span></strong>, so you can securely upload the package (there is a great set of instructions for doing this <strong><span style="text-decoration:underline;"><a href="https://packaging.python.org/tutorials/packaging-projects/" target="_blank" rel="noopener">here</a></span></strong>). Make sure to write down all of the information associated with the token as you will not be able to see it again.</p>
<p style="text-align:justify;">Next, make sure that you have an up-to-date version of the twine package in your environment. Twine is a Python package primarily for uploading packages, which can easily installed/upgraded in a conda environment with the following command:</p>

<pre><code>conda install twine</code></pre>
<p style="text-align:justify;">Now, Twine can be used to facilitate the upload of your package to TestPyPI with this command (making sure that you are still in your master_folder directory:</p>

<pre><code>python3 -m twine upload --repository-url https://test.pypi.org/legacy/ dist/*</code></pre>
<p style="text-align:justify;">Once the command has run, there will be a link to your TestPyPI repository at the bottom which you can click on to take you to it. You can use this to test install your package with no dependencies. In the case of PyTrx (pytrxhow, my test version), this could be done with the following command (just change 'pytrxhow' to specify a different package):</p>

<pre><code>pip install -i https://test.pypi.org/simple/ pytrxhow </code></pre>
<p style="text-align:justify;"><strong>This is all well and good for testing how a package looks on PyPI and testing it can install, however, I was more anxious about the package dependencies</strong> knowing the issues I had with OpenCV and GDAL previously in my conda environment. After checking your TestPyPI installation (and this may take a few tries, updating the version number every time), put your dependencies back into your <code>setup.py</code> file, run the distribution file generation again, and test the dependency configuration with the following command that will attempt to install your package locally:</p>

<pre><code>python setup.py develop</code></pre>
<p style="text-align:justify;">This may take some time to run, but should give you an idea as to whether the dependencies can be resolved. I cloned my base conda environment in order to do this, giving a (relatively) blank environment to run off, and tested the installation by attempting to import the newly installed package in Spyder.</p>
<p style="text-align:justify;">I found that I could not solve the environment, no matter what I specified in <code>setup.py</code>, and therefore had to play around with which package was causing the majority of the problems. I found that GDAL was the main cause of PyTrx unsuccessfully installing, so took it out of my dependencies, instead opting to install it after with conda. This seems to work much better, and although may not be a perfect solution, it will create fewer problems for users.</p>

<h2>Uploading the distribution to PyPI</h2>
<p style="text-align:justify;">So at this point you should feel confident in the look and feel of your package, and its installation in your environment. Before proceeding with the final steps, just run through the following checklist to make sure you have everything:</p>

<ul>
	<li style="text-align:justify;">Check that all the information is correct in the <code>setup.py</code>, changing the name (e.g. 'pytrxhow' to 'pytrx') and dependencies if you have been uploading to PyPI previously</li>
	<li style="text-align:justify;">If you change anything in the <code>setup.py</code> file, then run the distribution file generation again</li>
	<li>Check your TestPyPI page to make sure all the information uploaded is correct and nothing is missing</li>
	<li style="text-align:justify;">Check on PyPI that there is no other package with the same name as yours</li>
</ul>
<p style="text-align:justify;"><strong>A thorough check is needed at this stage because an upload to PyPI cannot be changed.</strong> Further package versions can be uploaded if there is a major problem, but versions that you have uploaded cannot be edited or altered. Therefore it is best to try and get it right the first time. No pressure!</p>
<p style="text-align:justify;">For uploading to PyPI, you need to create an account on PyPI. This account creation is separate to TestPyPI, so another username and password unfortunately. Again, create an API token in the same manner as done previously with TestPyPI, making sure to write down all of the details associated with it. To upload your package to PyPI, we are using Twine again and the following command:</p>

<pre><code>twine upload dist/*</code></pre>
Once run, there will be a link to click through to your PyPI page and <strong>voila, your package is online and easy for anyone to download</strong> with the old classic command (in the case of PyTrx):
<pre><code>pip install pytrx</code></pre>
<p style="text-align:justify;">In the case of PyTrx, our PyPI page is available to view <span style="text-decoration:underline;"><strong><a href="https://pypi.org/project/pytrx/" target="_blank" rel="noopener">here</a></strong></span>, and our <strong><span style="text-decoration:underline;"><a href="https://github.com/PennyHow/PyTrx/tree/distribution" target="_blank" rel="noopener">GitHub repository</a> </span></strong>contains all of PyTrx's scripts and the distribution files used for the PyPI upload, which might be useful for some. <strong>Hope this helps someone who has suffered any of the pitfalls of PyPI packages! </strong></p>
<img class="  wp-image-7659 aligncenter" src="https://pennyhow.files.wordpress.com/2020/02/img_5065.jpg" alt="Icebergs in Nuuk" width="536" height="402" />

<hr />

<strong>Useful resources:</strong>

<span style="text-decoration:underline;"><strong><a href="https://packaging.python.org/tutorials/packaging-projects/" target="_blank" rel="noopener">A broad overview and use of Test PyPI</a></strong></span>

<span style="text-decoration:underline;"><strong><a href="https://packaging.python.org/guides/distributing-packages-using-setuptools/" target="_blank" rel="noopener">Uploading to PyPI</a></strong></span>

<strong><span style="text-decoration:underline;"><a href="https://python-packaging.readthedocs.io/en/latest/dependencies.html" target="_blank" rel="noopener">More information about specifying dependencies and testing package installations</a></span></strong>

<strong><span style="text-decoration:underline;"><a href="https://pypi.org/classifiers/" target="_blank" rel="noopener">More information about PyPI classifiers</a></span></strong>

PyTrx's <span style="text-decoration:underline;"><strong><a href="https://pypi.org/project/pytrx/" target="_blank" rel="noopener">PyPI page</a></strong></span>, <span style="text-decoration:underline;"><strong><a href="https://github.com/PennyHow/PyTrx/" target="_blank" rel="noopener">GitHub repository</a></strong></span>, and <span style="text-decoration:underline;"><strong><a href="https://www.frontiersin.org/articles/10.3389/feart.2020.00021/abstract" target="_blank" rel="noopener">publication</a></strong></span>
