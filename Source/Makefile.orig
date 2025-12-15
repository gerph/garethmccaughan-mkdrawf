# Makefile for mkdrawf 3

#-----------------------------------------------------

CC	= cc
CC3	= cc3		# see file !!Note
AS	= objasm
LINK	= link

CFLAGS	= -fah #-DTAGS
LFLAGS	= 
DEFS	= 

LIBS	= C:o.stubs

INSTDIR	= $.bin.gjm# where you want executables to go
TAGOBJ	= #o.tagfile	# define this if you use -DTAGS

#-----------------------------------------------------

.SUFFIXES: .o .s .c

.c.o:;	$(CC) -c $(CFLAGS) $(INCLUDE) $(DEFS) $<
.s.o:;	$(AS) $<

#-----------------------------------------------------

all: mkdrawf decdrawf

squeeze: mkdrawf decdrawf
  squeeze -v mkdrawf
  squeeze -v decdrawf

install:
  copy mkdrawf $(INSTDIR).mkdrawf f~c
  copy decdrawf $(INSTDIR).decdrawf f~c

# --CAUTION-- If you have no assembler, change the first line of the following!
# You might also want to lose the "remove" lines, but I doubt it.
clean:
  wipe o.* ~c
  remove mkdrawf
  remove decdrawf

dist: squeeze
  remove o.decdrawf
  remove o.general
  remove o.mouth
  remove o.stomach
  remove o.tagfile
  remove o.test

#-----------------------------------------------------

mkdrawf: o.mouth o.stomach o.general o.syscalls $(TAGOBJ) h.mkdrawf
  $(LINK) $(LFLAGS) -o mkdrawf o.mouth o.stomach o.general o.syscalls\
	$(TAGOBJ) $(LIBS)

decdrawf: o.decdrawf o.lowfile
  $(LINK) $(LFLAGS) -o decdrawf o.decdrawf o.lowfile $(LIBS)

test: o.mouth o.general o.syscalls o.test $(TAGOBJ)
  $(LINK) $(LFLAGS) -o test o.mouth o.general o.syscalls o.test\
	$(TAGOBJ) $(LIBS)

#-----------------------------------------------------

o.mouth: c.mouth
  $(CC3) -c $(CFLAGS) $(INCLUDE) $(DEFS) c.mouth
