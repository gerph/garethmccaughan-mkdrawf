# Makefile for !drawf
#
# You won't be able to recreate o.glib, because the source code for that
# isn't included. Contact me if you want it.

CC	= cc
AS	= objasm

.SUFFIXES: .o .s

.o.s:; $(as) $< 

GOBS	= $.p.gjmlib.o.wimp* $.p.gjmlib.o.hglass $.p.gjmlib.o.load+save\
 $.p.gjmlib.o.dde

^.!runimage: c.drawf o.glib
  $(CC) -DTHROWBACK -DHELPFUL -o ^.!RunImage c.drawf o.glib
  squeeze -v ^.!RunImage

o.glib: $(GOBS)
  makeALF -o o.glib $(GOBS)
