ROOT=../../../c++

CXX=g++
CFLAGS+=-DBPMF_HYBRID_COMM -DBPMF_GPI_COMM -DBPMF_TBB_SCHED -DBPMF_PROFILING
#CFLAGS+=-DEIGEN_MALLOC_ALREADY_ALIGNED=0

SUPPORT=/work/y14/shared/eurompi/support

# for MPICH
CFLAGS+=-I$(CRAY_MPICH_DIR)/include
LDFLAGS+=-Wl,-rpath=$(CRAY_MPICH_DIR)/lib 
LDFLAGS+=-L$(CRAY_MPICH_DIR)/lib -lmpich

# for tbb
CFLAGS+=-I$(SUPPORT)/tbb/include
LDFLAGS+=-Wl,-rpath=$(SUPPORT)/tbb/lib 
LDFLAGS+=-L$(SUPPORT)/tbb/lib -ltbb

# for GPI2
CFLAGS+=$(shell pkg-config gpi2 --cflags)
LDFLAGS+=$(shell pkg-config gpi2 --libs)

# for allinea
#LDFLAGS+=-L$(ALLINEA_TOOLS_DIR)/lib/64 -Wl,--whole-archive -Wl,-Bstatic -ldmallocthcxx  -Wl,-Bdynamic -Wl,--no-whole-archive -Wl,--allow-multiple-definition

include ../../Makefile.common

all: bpmf
	install bpmf /work/y14/y14/vanderaa/eurompi/gpi-tbb/
