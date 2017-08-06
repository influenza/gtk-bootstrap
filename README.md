# Gtk Bootstrap

An opinionated tool for creating GTK3 projects.

# Quick Start

To created a sample project (spreadsheet v1.0.0):

    ./gtk-bootstrap spreadsheet /work/spreadsheet/ 1.0.0 bugs@spreadsheet.org
    cd /work/spreadsheet
    git init .
    make
    ./src/main

# Choices

* Autotools is the preferred build system
* C11 support is required
* `gcc` is used
* The generated `Makefile`s use silent rules
* glib 2.0 and gtk+ 3.0 are required
* The following standard functions are required
  * bzero
  * memmove
  * memset
  * strerror
