---
title: 'python-ags4: A Python library to read, write, and validate AGS4 geodata files'
tags:
  - Python
  - geodata
  - geotechnical
  - geoenvironmental
  - geophysics
  - geoscience
authors:
  - name: Asitha I. Senanayake
    orcid: 0000-0001-7525-1160
    affiliation: 1
  - name: Edward Lewis
    orcid: 0000-0003-2685-383X
    affiliation: 2   
affiliations:
 - name: Fugro USA Marine, Inc.
   index: 1
 - name: British Geological Survey, Keyworth, UK
   index: 2  
date: 03 April 2022
bibliography: paper.bib
---

# Summary

Data gathered from geotechnical, geoenvironmental, and geophysical
investigations can be broadly described as "geodata". The AGS4 data format
[@AGS:2017; @AGS:2021] is one of the most widely used data transmittal formats
for geodata and is used across the world. It is a plain text format consisting
of multiple tables of comma-separated values, tied together with a robust
data schema and a comprehensive suite of validation rules.

``python-ags4`` is a Python library that provides functionality to read, write,
and validate AGS4 files. It provides users access to the full power of the
Python ecosystem to explore, analyze, and visualize geodata. Pandas DataFrame
[@reback2020pandas] is the primary data structure used within the library,
therefore it can handle relatively large datasets reasonably fast. The
data validation module checks the file for compliance with the validation rules
and provides a detailed error report.

# Statement of Need

This library fulfills the following needs of the engineering and scientific
community that uses AGS4 geodata files:

- Provide a transparent and easily accessible tool to validate AGS4 geodata
  files.
- Provide access to the Python ecosystem to users of AGS4 geodata.
- Provide a cross-platform tool to work with AGS4 geodata files.

Having a free an open-source tool that can validate AGS4 files will ensure the
quality of geodata that is produced. It also lowers the barrier to entry for
those who are not familiar with this data format and fosters data sharing and
collaboration. `python-ags4` has already been adopted by the British Geological
Survey to work with its large repository of publicly available AGS4 geodata
files.

Python has a rich ecosystem of packages that can be utilized to analyze and
visualize data in general. The ability to easily import geodata from AGS4 files
would greatly enhance the ability of engineers and scientists to gain insights
from that data. A Jupyter Notebook with examples of how to import data to Pandas
and GeoPandas [@jordahl:2020] for statistical and spatial analyses and visualize
using Matplotlib [@Hunter:2007] is provided in the git repo of this library. We 
provide an example for users in the git repo - https://gitlab.com/ags-data-format-wg/ags-python-library/-/blob/main/examples/ags.ipynb [@Lewis:2021].   

The command-line interface included with the library is a convenient and easy
use tool to work with AGS4 geodata files. It is cross-platform and has been
tested in Linux, Windows, and Mac environments.

# Ongoing Projects

`python-ags4` has been implemented in two Free Open Source Software projects, 
making the library more accessible to non technical users.  
- https://gitlab.com/ags-data-format-wg/ags-checker-desktop-app  
  - Windows application offering the functionality of the library
- https://github.com/BritishGeologicalSurvey/pyagsapi
  - API and GUI (https://agsapi.bgs.ac.uk/) offering the functionality of the 
    library on the web. 

# Acknowledgements
The authors acknowledge the work done by the AGS Data Format Working Group to
develop the AGS4 data format and the support it has extended to develop this
library.

# References
