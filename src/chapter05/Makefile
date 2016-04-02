BIN = ../../bin
ODIR = ../../obj
SUBDIRS = 
CC = cc
CFLAGS = -std=c99 -Wall -g -I.
LINT = splint
LINTFLAGS = -compdef +quiet +skip-sys-headers +charintliteral +charint -shadow -preproc
DEPS =
_OBJ = getfloat.o getint.o

OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))

.PHONY: all clean

all: getint getfloat
	@for i in $(SUBDIRS); do \
		echo "make all in $$i..."; \
		cd $$i; \
		make all; \
		cd ..; \
		rm -f $(ODIR)/*.o; \
	done

clean:
	rm -f $(ODIR)/*.o

getfloat: $(ODIR)/getfloat.o
	$(CC) $(CFLAGS) $^ -o $(BIN)/$@

getint: $(ODIR)/getint.o
	$(CC) $(CFLAGS) $^ -o $(BIN)/$@

$(ODIR)/%.o: %.c $(DEPS)
	$(CC) $(CFLAGS) -c -o $@ $<
	$(LINT) $(LINTFLAGS) $<