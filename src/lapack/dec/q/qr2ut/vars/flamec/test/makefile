#
# test directory makefile
#

FNAME        := QR2_UT

SRC_PATH     := ..
OBJ_PATH     := .

INST_PATH    := $(HOME)/flame
LIB_PATH     := $(INST_PATH)/lib
INC_PATH     := $(INST_PATH)/include
FLAME_LIB    := $(LIB_PATH)/libflame.a
#BLAS_LIB     := $(LIB_PATH)/libgoto_core2.a
BLAS_LIB     := $(LIB_PATH)/libblas_clover.a

CC           := gcc
FC           := gfortran
LINKER       := $(CC)
CFLAGS       := -I$(SRC_PATH) -I$(INC_PATH) -g -O3 -Wall
FFLAGS       := $(CFLAGS)
LDFLAGS      := -L/usr/lib/gcc/x86_64-pc-linux-gnu/4.2.3 -L/usr/lib/gcc/x86_64-pc-linux-gnu/4.2.3/../../../../lib64 -L/lib/../lib64 -L/usr/lib/../lib64 -L/usr/lib/gcc/x86_64-pc-linux-gnu/4.2.3/../../../../x86_64-pc-linux-gnu/lib -L/usr/lib/gcc/x86_64-pc-linux-gnu/4.2.3/../../.. -lgfortranbegin -lgfortran -lm
LDFLAGS      += -lpthread

TEST_OBJS    := $(patsubst $(SRC_PATH)/%.c, $(OBJ_PATH)/%.o, $(wildcard $(SRC_PATH)/*.c))
TEST_OBJS    += test_$(FNAME).o \
                time_$(FNAME).o
TEST_BIN     := test_$(FNAME).x

$(OBJ_PATH)/%.o: $(SRC_PATH)/%.c
	$(CC) $(CFLAGS) -c $< -o $@
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

test_$(FNAME): $(TEST_OBJS)
	$(LINKER) $(TEST_OBJS) $(LDFLAGS) $(FLAME_LIB) $(LAPACK_LIB) $(BLAS_LIB) -o $(TEST_BIN)

clean:
	rm -f *.o $(OBJ_PATH)/*.o *~ core *.x

