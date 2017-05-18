#DEBUG = -DDEBUG -ggdb

# Linux
CC = g++ -O3 ${DEBUG}
# OSX 10.7.5
#CC = g++ -O3 -framework opencl -I../ ${DEBUG}

# uncomment next line if you installed NTL with gf2x
#LIBGF2X = -lgf2x
# uncomment next line if you installed NTL with gmp
#LIBGMP = -lgmp
#LINKOPT = -lntl ${LIBGF2X} ${LIBGMP}

.SUFFIXES:      .cl .clh

all:
	${MAKE} mtgp32-sample

mtgp32-sample: mtgp32-sample.cpp \
		opencl_tools.hpp \
		mtgp32-sample-common.h \
		../kernels_src/cl/mtgp32.cl \
		../kernels_src/clh/mtgp32.clh \
		mtgp32-fast.h \
		parse_opt.o \
		mtgp32-fast.o \
		mtgp32-param-fast.o
	${CC} -o $@ mtgp32-sample.cpp \
		parse_opt.o \
		mtgp32-fast.o \
		mtgp32-param-fast.o \
		-lOpenCL

.c.o:
	gcc -O3 -std=c99 ${DEBUG} -c -o $@ $<

.cpp.o:
	g++ -O3 ${DEBUG} -c -o $@ $<

.cl.cli:
	cpp $< $@

clean:
	rm -rf *.o *~ *.dSYM