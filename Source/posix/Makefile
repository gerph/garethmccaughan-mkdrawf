

CFLAGS = -funsigned-char

all: test decdrawf mkdrawf

test: general.o \
      mouth.o \
      syscalls.o \
	  test.o

decdrawf: decdrawf.o \
          lowfile_c.o

mkdrawf: general.o \
         mouth.o \
         stomach.o \
         syscalls.o \
         tagfile.o

clean:
	rm -f *.o test decdrawf mkdrawf
