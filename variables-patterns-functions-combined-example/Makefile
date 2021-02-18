# usage:
# make    # compile all binary
# make clean     # remove all binaries and objects

.PHONY: all clean

CC = gcc

LINKERFLAG = -lm

SRCS := $(wildcard *.c)
BINS := $(SRCS:%.c=%)

all: $(BINS)

%: %.o
	@echo "Checking..."
	$(CC) $(LINKERFLAG) $< -o $@

%.o: %.c
	@echo "Creating object..."
	$(cc) -c $<

clean:
	@echo "Cleaning up..."
	rm -rvf *.o $(BINS)
