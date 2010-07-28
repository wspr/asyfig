
.SILENT:

TESTS = $(shell ls *.ltx | sed -e 's/.ltx//')
TEST_PDF = $(addsuffix -pdf.pdf,$(TESTS))
TEST_DVI = $(addsuffix -dvi.dvi,$(TESTS))


test: asymptote.sty clean $(TEST_PDF) $(TEST_DVI)
	make cleanmost

clean:
	rm -f *_.tex *.asy *.pre *.pdf *.eps *.dvi *.log *.aux

cleanmost:
	rm -f *_.tex *.asy *.pre *.log *.aux

asymptote.sty: ../asymptote.sty
	cp -f $< $@

%-pdf.pdf: %.ltx
	echo "Testing PDF output for test '$*'"
	echo "	Compiling PDF"
	pdflatex -batchmode -jobname="$*-pdf" $*.ltx &> /dev/null
	echo "	Generating asy graphics"
	asy $*-pdf-*.asy
	echo "	Recompiling PDF"
	pdflatex -batchmode -jobname="$*-pdf" $*.ltx &> /dev/null
	if grep -q "Package asymptote Warning" $*-pdf.log; \
		then echo "Failed; investigate $*-pdf.log" && false; fi
	echo "  "


%-dvi.dvi: %.ltx
	echo "Testing DVI output for test '$*'"
	echo "	Compiling DVI"
	latex -batchmode -jobname="$*-dvi" $*.ltx &> /dev/null
	echo "	Generating asy graphics"
	asy $*-dvi-*.asy
	echo "	Recompiling DVI"
	latex -batchmode -jobname="$*-dvi" $*.ltx &> /dev/null
	if grep -q "Package asymptote Warning" $*-dvi.log; \
		then echo "Failed; investigate $*-dvi.log" && false; fi
	echo "  "

