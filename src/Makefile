INCLUDE_DIRS = ../inc
CFLAGS += -O2

all: c_kzg_4844.o lib

c_kzg_4844.o: c_kzg_4844.c Makefile
	clang -Wall -I$(INCLUDE_DIRS) $(CFLAGS) -c $<

# Will fail with "patch does not apply" if it has already been patched.
# Safe to ignore.
blst:
	cd ../blst; \
	git apply < ../blst_sha.patch; \
	./build.sh && \
	cp libblst.a ../lib && \
	cp bindings/*.h ../inc

# Copy make sure c_kzg_4844.o is built and copy it for the NodeJS bindings
lib: c_kzg_4844.o Makefile
	cp *.o ../bindings/node.js
