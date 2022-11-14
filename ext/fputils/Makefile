
SOURCEDIR=.
BUILDDIR=.

SOURCES = $(wildcard $(SOURCEDIR)/*.c)
OBJECTS = $(patsubst $(SOURCEDIR)/%.c, $(BUILDDIR)/%.os, $(SOURCES))

LIB=libfputils.a

all: $(LIB)

CFLAGS=-Iinclude/

$(LIB): $(OBJECTS)
	ar rcs $(LIB) $^

$(BUILDDIR)/%.os: $(SOURCEDIR)/%.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm $(LIB) $(OBJECTS)
