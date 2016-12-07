# Makefile marean
# your name (from description?)
# perhaps import the description here.

# set parameters ---------------------------------------------------------------

# tidy -------------------------------------------------------------------------
01_tidy/01_tidy.html: 01_tidy/01_tidy.Rmd
	Rscript -e 'rmarkdown::render("$<")'

01_tidy: 01_tidy/01_tidy.html data

# fit --------------------------------------------------------------------------
02_fit/02_fit_fev1.html: 02_fit/02_fit.Rmd 01_tidy/01_tidy.html
	Rscript -e 'rmarkdown::render("$<")'

#### Fit all
02_fit: 02_fit/02_fit.html

# process the results-----------------------------------------------------------

03_process/03_process.html: 03_process/03_process.Rmd 02_fit/02_fit.html
	Rscript -e 'rmarkdown::render("$<")'

#### post-process-all
03_process: 03_process/03_process.html

# diagnostics ------------------------------------------------------------------

#### fev1
04_diagnostics/04_diagnostics.html: 04_diagnostics/04_diagnostics.Rmd 03_post_process/03_post_process_fev1.html
	Rscript -e 'rmarkdown::render("$<")'

#### all diagnostics
04_diagnostics: 04_diagnostics/04_diagnostics.html

# generate paper ---------------------------------------------------------------

# make it as PDF
04_paper/04_paper.pdf: 04_paper/04_paper.Rmd 03_process/03_process.Rmd \
	Rscript -e 'rmarkdown::render("$<", "pdf_document")'

# make it as HTML
04_paper/04_paper.html: 04_paper/04_paper.Rmd 03_process/03_process.Rmd \
	Rscript -e 'rmarkdown::render("$<", "html_document")

paper: 04_paper/04_paper.html 04_paper/04_paper.pdf \

# make the whole paper ---------------------------------------------------------
all: 05_paper/05_paper.html \
04_diagnostics/04_diagnostics.html \
03_process/03_process.html \
02_fit/02_fit.html \
01_tidy/01_tidy.html

# clean ------------------------------------------------------------------------
# todo, decide what needs to go, and what needs to stay
clean:
	rm -rf outputs/*
	rm -rf */*_cache
	rm -rf */*_files
	rm -f */*.md
	rm -f */*.tex

# clobber ----------------------------------------------------------------------
clobber:
	rm -rf */*.html
	rm -rf */*.pdf

# Extras -----------------------------------------------------------------------

# which files are not files in the literal sense?
.PHONY: all clean clobber

# using parameters

# 02_fit/02_fit_fev1.html: 02_fit/02_fit.Rmd 01_tidy/01_tidy.html
# 	Rscript -e 'rmarkdown::render("$<")
	# params = list(n_iterations_adapt = $(nia), \
	# n_iterations_burnin = $(nib), \
	# n_iterations_model = $(nim), \
	# n_thin = $(nthin), \
	# n_chains = $(nchains), \
	# outcome = "fev1_perc"), \
	# output_file = "02_fit_fev1.html")'
# TO DO, make the data the prerequisite
