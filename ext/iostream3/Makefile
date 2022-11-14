
SOURCEDIR=.
BUILDDIR=.

SOURCES = $(wildcard $(SOURCEDIR)/*.cc)
OBJECTS = $(patsubst $(SOURCEDIR)/%.cc, $(BUILDDIR)/%.os, $(SOURCES))

LIB=libiostream3.a

all: $(LIB)

$(LIB): $(OBJECTS)
	ar rcs $(LIB) $^

$(BUILDDIR)/%.os: $(SOURCEDIR)/%.cc
	$(CPP) $(CFLAGS) -c $< -o $@

clean:
	rm $(LIB) $(OBJECTS)
