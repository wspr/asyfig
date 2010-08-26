
.SILENT:

TESTS = $(shell ls *.ltx | sed -e 's/.ltx//')
TEST_PDF = $(addsuffix -pdf.pdf,$(TESTS))
TEST_DVI = $(addsuffix -dvi.dvi,$(TESTS))


test: asymptote.sty clean $(TEST_PDF) $(TEST_DVI)
	make clean

clean:
	rm -f -- *-*.tex *.asy *.pre *.pdf *.eps *.dvi *.log *.aux *.out *.prc *.js *.synctex*

asymptote.sty: ../asymptote.sty
	cp $< $@

../asymptote.sty: ../asy-latex.dtx
	cd ..; tex asy-latex.dtx &> /dev/null;

%-pdf.pdf: %.ltx
	echo "Testing PDF output for test '$*'"
	echo "	Compiling PDF"
	pdflatex -jobname="$*-pdf" $*.ltx &> /dev/null
	echo "	Generating asy graphics"
	asy $*-pdf-*.asy
	echo "	Recompiling PDF"
	pdflatex -jobname="$*-pdf" $*.ltx &> /dev/null
	if grep -q "Package asymptote Warning" $*-pdf.log; \
		then echo "Failed; investigate $*-pdf.log" && false; fi
	echo "  "


%-dvi.dvi: %.ltx
	echo "Testing DVI output for test '$*'"
	echo "	Compiling DVI"
	latex -jobname="$*-dvi" $*.ltx &> /dev/null
	echo "	Generating asy graphics"
	asy $*-dvi-*.asy
	echo "	Recompiling DVI"
	latex -jobname="$*-dvi" $*.ltx &> /dev/null
	if grep -q "Package asymptote Warning" $*-dvi.log; \
		then echo "Failed; investigate $*-dvi.log" && false; fi
	echo "  "

