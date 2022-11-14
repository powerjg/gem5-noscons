
SOURCEDIR=lib
BUILDDIR=lib

SOURCES = $(wildcard $(SOURCEDIR)/*.cc)
OBJECTS = $(patsubst $(SOURCEDIR)/%.cc, $(BUILDDIR)/%.os, $(SOURCES))

CFLAGS=-Iinclude/

LIB=libnomali.a

all: $(LIB)

$(LIB): $(OBJECTS)
	ar rcs $(LIB) $^

$(BUILDDIR)/%.os: $(SOURCEDIR)/%.cc
	$(CPP) $(CFLAGS) -c $< -o $@

clean:
	rm $(LIB) $(OBJECTS)
