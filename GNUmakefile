#------------------------------------------------------------------------------
# primary source: .eps
# store ROOT plots in .eps format, make .png and .pdf out of .eps files
#------------------------------------------------------------------------------
dir=.

note := main

tex_files := $(note).tex # $(wildcard *.tex)

pdfs1 := $(patsubst images/chapter1/%.eps, images/chapter1/%.pdf,  $(wildcard images/chapter1/*.eps ))
pdfs2 := $(patsubst images/chapter2/%.eps, images/chapter2/%.pdf,  $(wildcard images/chapter2/*.eps ))
pdfs3 := $(patsubst images/chapter3/%.eps, images/chapter3/%.pdf,  $(wildcard images/chapter3/*.eps ))
pngs1 := $(patsubst images/chapter1/%.eps, images/chapter1/%.png, $(wildcard images/chapter1/*.eps ))
pngs2 := $(patsubst images/chapter2/%.eps, images/chapter2/%.png, $(wildcard images/chapter2/*.eps ))
pngs3 := $(patsubst images/chapter3/%.eps, images/chapter3/%.png, $(wildcard images/chapter3/*.eps ))

figure_03160: figures/eps/figure_03160_flsh0s36b0_vdet_9_time.eps 
	convert -density 400 -depth 8 -quality 85 -trim $? figures/png/figure_03160_flsh0s36b0_vdet_9_time.png 

figures/pdf/%.pdf: figures/eps/%.eps
	ps2pdf -dEPSCrop $? $@

figures/png/%.png: figures/eps/%.eps
	convert -density 400 -depth 8 -quality 85 -trim $? $@

pdf: $(pdfs) 
# 	echo $?
png: $(pngs1) 
# 	echo $?
png: $(pngs2) 
# 	echo $?
png: $(pngs3) 
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
