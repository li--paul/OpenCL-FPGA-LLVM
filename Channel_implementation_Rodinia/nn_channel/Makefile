include ../common/make.config

#C compiler
CC = g++

# Altera OpenCL
ALTERA_SDACCEL :=/root/intelFPGA/16.1/hld
DSA := de5net_a7
AOC := $(ALTERA_SDACCEL)/bin/aoc

SRC_GPU = nearestNeighbor_gpu.cpp clutils_gpu.cpp utils.cpp
#SRC_FPGA = nearestNeighbor_fpgacu2.cpp clutils_fpga.cpp utils.cpp
#SRC_FPGA = nearestNeighbor_fpgacu3.cpp clutils_fpga.cpp utils.cpp
SRC_FPGA = nearestNeighbor_fpga.cpp clutils_fpga.cpp utils.cpp
#SRC_FPGA = nearestNeighbor_fpga_old.cpp clutils_fpgabase.cpp utils.cpp

#CC_FLAGS = -g -O3
CC_FLAGS = -Wall

all: clean \
	 nn_gpu.exe \
     nn_fpga.exe \

nn_gpu.exe:
	$(CC) $(CC_FLAGS) -lOpenCL  -fopenmp $(SRC_GPU) -o $@ -I$(OPENCL_INC) -L$(OPENCL_LIB)
	
nn_fpga.exe:
	$(CC) $(CC_FLAGS) -g -lOpenCL  -fopenmp $(SRC_FPGA) -o $@ -I$(OPENCL_INC) -L$(OPENCL_LIB) -I$(ALTERA_OPENCL_INC) -L$(ALTERA_OPENCL_LIB)

clean: 
	rm -f *.exe 
