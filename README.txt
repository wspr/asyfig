__________________
The ASYFIG package

This package provides an alternative to the asymptote package for including Asymptote graphics in a LaTeX document. In this package, all Asymptote figures are defined separately from the source in their own individual ".asy" files. This package uses Asymptote's inline mode so that labels in the graphics are produced by the main typesetting run; this ensures consistent font and size selection of text within the graphics. In addition, each individual ".asy" graphic can be very quickly processed individually to facilitate easy maintenance and editing of the graphics.

____________
INSTALLATION

Run `latex` on asyfig.tex to produce the files
  asyfig.ins, asyfig.sty, asyalign.sty, asyprocess.sty, and README.txt,
as well as to compile the PDF documentation.

Execute `tex pstool.ins` to produce the files above
except pstool.ins (and the PDF file, obviously).

___________
MAINTENANCE

Please report bugs or request features:
  <http://github.com/wspr/asyfig/issues>

Developmental and historical versions:
  <http://github.com/wspr/asyfig>

Current release version:
  <http://ctan.tug.org/pkg/asyfig>

______________
Will Robertson
Copyright 2008-2009
