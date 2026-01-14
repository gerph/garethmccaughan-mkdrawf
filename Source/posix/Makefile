

CFLAGS = -funsigned-char

all: test decdrawf mkdrawf

TEST_OBJS = general.o \
      mouth.o \
      syscalls_c.o \
	  test.o

DEC_OBJS = decdrawf.o \
          lowfile_c.o

MK_OBJS = general.o \
         mouth.o \
         stomach.o \
         syscalls_c.o \
         fake_fontscanstring.o \
         tagfile.o

test: ${TEST_OBJS}
	${CC} ${TEST_OBJS} -lm -o $@

decdrawf: ${DEC_OBJS}
	${CC} ${DEC_OBJS} -lm -o $@

mkdrawf: ${MK_OBJS}
	${CC} ${MK_OBJS} -lm -o $@

clean:
	rm -f *.o test decdrawf mkdrawf
