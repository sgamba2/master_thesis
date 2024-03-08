#------------------------------------------------------------------------------
# primary source: .eps
# store ROOT plots in .eps format, make .png and .pdf out of .eps files
#------------------------------------------------------------------------------
#------------------------------------------------------------------------------
# primary source: .eps
# store ROOT plots in .eps format, make .png and .pdf out of .eps files
#------------------------------------------------------------------------------
dir=.

note := main

tex_files := $(note).tex # $(wildcard *.tex)

pdfs := $(patsubst figures/eps/%.eps, figures/pdf/%.pdf,  $(wildcard figures/eps/*.eps ))

pngs := $(patsubst figures/eps/%.eps, figures/png/%.png, $(wildcard figures/eps/*.eps ))
jpgs := $(patsubst figures/eps/%.eps, figures/jpg/%.jpg, $(wildcard figures/eps/*.eps ))

figure_03160: figures/eps/figure_03160_flsh0s36b0_vdet_9_time.eps 
	convert -density 400 -depth 8 -quality 85 -trim $? figures/png/figure_03160_flsh0s36b0_vdet_9_time.png 

figures/pdf/%.pdf: figures/eps/%.eps
	ps2pdf -dEPSCrop $? $@

figures/png/%.png: figures/eps/%.eps
	convert -density 400 -depth 8 -quality 85 -trim $? $@

pdf: $(pdfs) 
# 	echo $?
png: $(pngs) 
# 	echo $?
jpg: $(jpgs) 
# 	echo $?

note: $(tex_files) pdf 
	if [ ! -d tmp ] ; then mkdir tmp ; fi ; \
	pdflatex -output-directory=tmp $^ ; \
	cd tmp ; \
	bibtex $(note) ; \
	cd .. ; \
	pdflatex -output-directory=tmp $^

all: pdf note
	echo $(pdfs)
	echo $?
