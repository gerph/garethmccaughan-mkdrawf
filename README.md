# RISC OS mkdrawf and decdrawf tools

## Summary

This repository contains the source for the `mkdrawf` and `decdrawf`
tools. These tools can create and decode RISC OS DrawFiles as text
files. The tools are able to be used on RISC OS and Ubuntu systems.


## Installation

The binaries are available from the
[Releases](https://github.com/gerph/garethmccaughan-mkdrawf/releases)
section of the GitHub site. The archives are labelled with the operating
system they are produced for.

Unzip the archive and copy the `mkdrawf` and `decdrawf` to a location
on your path (either `Run$Path` locations, or the Library directory on
RISC OS, or the `PATH` variable locations on Ubuntu).

## Usage

The tools can provide help when run without parameters, but more information
is available in the [Text manual](https://github.com/gerph/garethmccaughan-mkdrawf/blob/master/Doc/Manual/Text).

### mkdrawf

Usage: `mkdrawf <input-file> <output-file>`

The `mkdrawf` tool is used to create DrawFiles from definitions given in
text format. See the text manual for more details but a simple example you
could create a path with a definition like:


    Path {
      FillColour None
      OutlineColour r0g0b255
      Width 1               # points. 0 = as thin as possible
      Style {
        Mitred              # join style.
                            # Options: Mitred Round Bevelled
        EndCap Round        # Options: Butt Round
                            #          Square Triangular
        StartCap Triangular
        WindingRule NonZero # determines how filling is done.
                            # Alternative: EvenOdd
        CapWidth 32         # for triangular caps only.
                            # 0..255, in 16ths of line width
        CapLength 64        # ditto
        Dash {
          1 3 2 5 3         # if you have no idea what this
                            # means, experiment!
          Offset 2 }        # ditto
      }
      # Now the path itself
      Move 100 100
      Line 200 100
      Curve 250 100  200 300  400 400 # Bezier curve.
                                      # Two ctl points, end
      Close                # this subpath
      Move 200 200
      Line 300 200
      Move 500 500         # this begins a new subpath too,
                           # even though no Close before it
      Line 0 0
    }

### decdrawf

Usage: `decdrawf [-s <spritefile>] [-j <jpeg-prefix>] [-u <units>] [-x] [-e] <drawfile>`

The `decdrawf` tool converts a Drawfile into a textual description (which can
then be fed back to `mkdrawf` to create an original drawfile.

* Sprites can be written to a single file - only one sprite will be extracted - with the `-s` switch. By default they are embedded in the text file.
* JPEGs will be extracted to files with a prefix given by `-j`.
* The `-u` option allows you to specify units in the Drawfile in a different way:
    * `sp` - scaled points
    * `os` - OS units
    * `pt` - points
    * `mm` - millimetres
    * `cm` - centimetres
    * `in` - inches
* For explicit sizing given in the Drawfile, use `-x` for hexadecimal values for the scaled points.


## License

The `mkdrawf` software is (C) 1995-1998 Gareth McCaughan, and is released under MIT
license. Consult the LICENSE file.
