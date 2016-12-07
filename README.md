
<!-- README.md is generated from README.Rmd. Please edit that file -->
marean
======

marean (`ma`ke `re`produdicible `an`alysis) is a package that builds a framework to create a reproducible package. It is inspired by devtools, and [projectTemplate](http://projecttemplate.net/), the idea being to automate many of the steps that might get in the way of making an analysis reproducible, in this case, really focussing on creating filestructures so that you can focus on writing your paper. A key feature of marean is the use of a makefile to run analysis and storing the output. The idea being to save you time by not needing to re-run the analysis again.

This structure was initially created when I wrote a Bayesian analysis that took 2-3 hours to run. I kep everything inside one giant rmarkdown document, which works great. Except when I occassionally fatfingered something and the analysis had to cook again.

I created the makefile so I could perform the analysis once, and only once, and then focus on writing my paper.

What does it do?
================

Currently, marean is only really suitable for forking, but I've listed the commands below to create this repository with the thought that this might turn into a package. However, I think that I need to write more papers that are fully reproducible before I can go ahead and do that.

<!-- There's also a bunch of other really great papers and projects about this -->
<!-- - rOpenSci links... -->
commands used to create marean (so far)

``` r

# Create rproj first
devtools::create(".") # select 1 to overwrite
devtools::use_mit_license()
devtools::use_readme_rmd()
dir.create("analysis")
file.create("analysis/Makefile")
dir.create("analysis/00_explore")
dir.create("analysis/01_tidy")
dir.create("analysis/02_fit")
dir.create("analysis/03_process")
dir.create("analysis/04_diagnostics")
dir.create("analysis/05_paper")
# step to create make or remake file
dir.create("data")
dir.create("R")
```

To Do
=====

-   Use / copy the templating system from devtools to create a bunch of templates for the rmarkdown files when using `use_vignette`, and Makefile.
-
