#Construct the lensing source codes into the programs to generate the lensing interpolant data 
#
#Targets:
#	all - Makes all lens programs in both current and binary directories
# 	bin_only - Makes all lens programs in binary directory only 
# 	user_only - Makes all lens programs in current directory only 

#C++ compiler and flags needed - requires dependencies openMP, arb, and flint 
CPP = g++
CPPFLAGS = -fopenmp -O3 -larb -lflint

#Do for all cxx files in this folder
CC_FILES = $(wildcard *.cc)
OUT_FILES = $(CC_FILES:%.cc=%)
BIN_DIR = $(HOME)/.local/bin
OUT_BIN = $(OUT_FILES:%=$(BIN_DIR)/%)

#Make All Lens Programs in both current directory and binary directory 
all: bin_only user_only 

#Make All Lens Programs in binary directory only
bin_only: $(OUT_BIN)

#Make All Lens Program is user directory only:
user_only: $(OUT_FILES) 

#Rule for Compiling the .cc source codes
%: %.cc
	$(CPP) -o $@ $< $(CPPFLAGS)

$(BIN_DIR)/%: %.cc
	$(CPP) -o $@ $< $(CPPFLAGS) 

#Debugging
variables:
	@echo CC_FILES: $(CC_FILES)
	@echo OUT_FILES: $(OUT_FILES) 
	@echo BIN_DIR: $(BIN_DIR)
	@echo OUT_BIN: $(OUT_BIN) 

#CLEAN TARGET
.PHONY: clean
clean:
	rm -f $(OUT_FILES) $(OUT_BIN) 

.PHONY: clean_local
clean_local:
	rm -f $(OUT_FILES) 

