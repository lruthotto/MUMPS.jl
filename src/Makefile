
topdir = MUMPS_5.0.1
libdir = $(topdir)/lib

metisdir = metis-5.1.0
# LMETISDIR = $(topdir)/../$(metisdir)/build/Linux-x86_64/libmetis/
LMETISDIR = $(metisdir)/build/Darwin-x86_64/libmetis/

include $(topdir)/Makefile.inc


SRC = mumps_cmplx_p.f90  mumps_p.f90 call_mumps_cmplx_p.f90 call_mumps_p.f90  
LIB = -L$(topdir)/lib -ldmumps -lzmumps -lmumps_common -lpord  -L$(LMETISDIR) -lmetis  $(LIBSEQ)  $(LIBBLAS)


all: $(SRC)
	 (make -C $(metisdir) config )
	 (make -C $(metisdir) )
	 (make -C $(topdir) d z)
	 $(FL) $(OPTL)  $(SRC) -o ../lib/MUMPS -I$(topdir)/include $(LIB)
clean:
	(cd $(metisdir); make distclean)
	(cd $(topdir); make clean)
	rm ../lib/MUMPS

