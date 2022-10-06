#HDF_INSTALL = /usr/local/hdf5
EXTLIB = -L/nasa/hdf5/1.8.18_mpt/lib -L/nasa/hdf5/1.8.18_mpt/lib/libhdf5_hl.a -L/nasa/hdf5/1.8.18_mpt/lib/libhdf5.a -L/nasa/szip/2.1.1/lib -L/nasa/pkgsrc/toss3/2021Q2/lib/
CC          = mpicc -cc=icc
CFLAGS      = -Wall -qopenmp -O2 -ipo -axCORE-AVX2 -xSSE4.2 
LIB         = -lz -lm -ldl -lgsl -lgslcblas -lm -lmpi -lsz -Wl,-rpath -Wl,/nasa/hdf5/1.8.18_mpt/lib -lhdf5

DEPS = mcrat.h mclib.h mclib_riken.h mclib_pluto.h mc_cyclosynch.h mcrat_input.h geometry.h mcrat_io.h mcrat_scattering.h mclib_flash.h
OBJ = mcrat.o mclib.o mclib_riken.o mclib_pluto.o mc_cyclosynch.o geometry.o mcrat_io.o mcrat_scattering.o mclib_flash.o
OBJ_MERGE = merge.o mclib.o mclib_riken.o mclib_pluto.o mc_cyclosynch.o geometry.o mcrat_io.o mcrat_scattering.o mclib_flash.o


INCLUDE   = -I/nasa/szip/2.1.1/include -I/nasa/hdf5/1.8.18_mpt/include -I/nasa/pkgsrc/toss3/2021Q2/include
LIBSHDF   =  $(EXTLIB)
 

%.o: %.c $(DEPS)
	$(CC) $(CFLAGS)  -c -o $@ $< $(INCLUDE) $(LIBSHDF) $(LIB)

MCRAT: $(OBJ)
	$(CC) $(CFLAGS)  -o $@ $^ $(INCLUDE) $(LIBSHDF) $(LIB)

MERGE: $(OBJ_MERGE) 
	$(CC) $(CFLAGS)  -o $@ $^ $(INCLUDE) $(LIBSHDF) $(LIB)

%.o: %.c $(DEPS)
	$(CC) $(CFLAGS)  -c -o $@ $< $(INCLUDE) $(LIBSHDF) $(LIB)

clean: 
	rm -f *.o 
 

.SUFFIXES:.o.c
