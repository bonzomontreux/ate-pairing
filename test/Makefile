include ../common.mk

HEADER= ../include/zm.h ../include/bn.h
TARGET=test_zm bn ../lib/libzm.a

ifeq ($(BIT),-m64)
TARGET += bench_test
endif

all:$(TARGET)

.SUFFIXES: .cpp

test_zm: test_zm.o ../lib/libzm.a
	$(LD) -o $@ $< $(LDFLAGS) $(BIT)

bn: bn.o ../lib/libzm.a
	$(LD) -o $@ $< $(LDFLAGS) $(BIT)

bench_test: bench.o ../lib/libzm.a
	$(LD) -o $@ $< $(LDFLAGS) $(BIT) 

../lib/libzm.a:
	make -C ../src ../lib/libzm.a

clean:
	$(RM) *.o $(TARGET)
	make -C ../src clean

test: $(TARGET)
	./test_zm && ./bn

test_zm.o: test_zm.cpp $(HEADER)
bn.o: bn.cpp $(HEADER)
bench.o: bench.cpp $(HEADER)
