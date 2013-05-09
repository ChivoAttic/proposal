TEXFILES = $(wildcard *.tex)
PDFFILES = $(TEXFILES:.tex=.pdf)

all: pdf clean

pdf: $(PDFFILES)

%.pdf: %.tex
	@rubber --pdf $<
	@if [ -d publish ];then mv *.pdf publish; else mkdir publish; mv *.pdf publish/;fi

pdflatex: $(TEXFILES)
	@pdflatex $<
	@pdflatex $<
	@bibtex $(TEXFILES:.tex=)
	@pdflatex $<

clean:
	@rubber --clean $(TEXFILES:.tex=)
	@rm -f *.vrb

distclean: clean
	@rubber --clean --pdf $(TEXFILES:.tex=)
	@rm -rf publish

x:
	@evince publish/$(PDFFILES) &> /dev/null &
