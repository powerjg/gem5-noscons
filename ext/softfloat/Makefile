
SOURCEDIR=.
BUILDDIR=.

SOURCES = $(wildcard $(SOURCEDIR)/*.c)
OBJECTS = $(patsubst $(SOURCEDIR)/%.c, $(BUILDDIR)/%.os, $(SOURCES))

LIB=libsoftfloat.a

all: $(LIB)

$(LIB): $(OBJECTS)
	ar rcs $(LIB) $^

$(BUILDDIR)/%.os: $(SOURCEDIR)/%.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm $(LIB) $(OBJECTS)
