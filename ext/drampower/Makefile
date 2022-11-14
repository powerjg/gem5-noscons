
SOURCEDIR=src
BUILDDIR=src

SOURCES = $(wildcard $(SOURCEDIR)/*.cc) $(SOURCEDIR)/libdrampower/LibDRAMPower.cc
OBJECTS = $(patsubst $(SOURCEDIR)/%.cc, $(BUILDDIR)/%.os, $(SOURCES))


LIB=libdrampower.a

all: $(LIB)

$(LIB): $(OBJECTS)
	ar rcs $(LIB) $^

$(SOURCEDIR)/libdrampower/LibDRAMPower.os: $(SOURCEDIR)/libdrampower/LibDRAMPower.cc
	$(CPP) -Isrc $(CFLAGS) -c $< -o $@

$(BUILDDIR)/%.os: $(SOURCEDIR)/%.cc
	$(CPP) $(CFLAGS) -c $< -o $@

clean:
	rm $(LIB) $(OBJECTS)
