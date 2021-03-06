
<!-- README.md is generated from README.Rmd. Please edit that file -->
marean
======

marean (`ma`ke `re`produdicible `an`alysis) is a repository with a framework facilitating reproducible analyses. It is inspired by [devtools](https://github.com/hadley/devtools), and [projectTemplate](http://projecttemplate.net/). The idea is to automate many of the steps that might get in the way of making an analysis reproducible, in this case, really focussing on creating filestructures so that you can focus on writing your paper. A key feature of marean is the use of a makefile to run analysis and storing the output to save time by not needing to re-run the analysis again.

This structure was initially created when I wrote a Bayesian analysis that took 2-3 hours to run. I kep everything inside one giant rmarkdown document, which works great. Except when I occassionally fatfingered something and the analysis had to cook again. I created the makefile so I could perform the analysis once, and only once, and then focus on writing my paper.

What does it do?
================

Currently, marean is only really suitable for forking, but I've listed the commands below to create this repository with the thought that this might turn into a package. However, I think that I need to write more papers that are fully reproducible before I can go ahead and do that.

<!-- There's also a bunch of other really great papers and projects about this -->
<!-- - rOpenSci links... -->
commands used to create marean (so far). These may turn into more sensible commands that pull from templates.

``` r

# Create rproj first
devtools::create(".") # select 1 to overwrite
devtools::use_mit_license()
devtools::use_readme_rmd()
dir.create("analysis")
dir.create("analysis/00_explore")
dir.create("analysis/01_tidy")
dir.create("analysis/02_fit")
dir.create("analysis/03_process")
dir.create("analysis/04_diagnostics")
dir.create("analysis/05_paper")
dir.create("analysis/06_supplementary")
file.create("analysis/Makefile")

# create Rmd docs
file.create("analysis/00_explore/00_explore.Rmd")
file.create("analysis/01_tidy/01_tidy.Rmd")
file.create("analysis/02_fit/02_fit.Rmd")
file.create("analysis/03_process/03_process.Rmd")
file.create("analysis/04_diagnostics/04_diagnostics.Rmd")
file.create("analysis/05_paper/05_paper.Rmd")
file.create("analysis/06_supplementary/06_supplementary.Rmd")

# step to create make or remake file
dir.create("data")
dir.create("R")
```

Perhaps these could be commands like:

-   `use_tidy`
-   `use_fit`
-   `use_process`
-   `use_paper`
-   `use_diagnostics`
-   `use_supplementary`

also, perhaps `use_paper` could include some templates to a journal, or something?

To Do
=====

Create templates for: - writing / saving / reading data from each analysis step - makefile

Create an example lightweight and heavyweight analysis examples.

Use / copy the templating system from devtools to create a bunch of templates for the rmarkdown files when using `use_vignette`, and Makefile.
