SHELL	= /bin/sh
CC	= gcc
OPT	= -O
DEBUG	= -g
CFLAGS	= $(DEFS) $(OPT) $(DEBUG)
LIBOBJ	= mymalloc.o error.o strerror.o split_at.o 
LIB	= aux_lib.a
BIN_DIR	= 
PROGS	= 

what:
	@sh makedefs

all:	$(LIB)

manpages: 

$(LIB):	$(LIBOBJ)
	$(AR) $@ $?
	$(RANLIB) $@

clean:
	rm -f $(PROGS) $(LIB) *.o *core

depend: $(MAKES)
	(sed '1,/^# do not edit/!d' Makefile; \
	set -e; for i in [a-z][a-z0-9]*.c; do \
	    $(CC) -E $(DEFS) $(INCL) $$i | sed -n -e '/^# *1 *"\([^"]*\)".*/{' \
	    -e 's//'`echo $$i|sed 's/c$$/o/'`': \1/' -e 'p' -e '}'; \
	done) | grep -v '[.][o][:][ ][/]' >$$$$ && mv $$$$ Makefile

# do not edit - this was generated with make depend
error.o: error.c
error.o: error.h
mymalloc.o: mymalloc.c
mymalloc.o: error.h
mymalloc.o: mymalloc.h
split_at.o: split_at.c
split_at.o: split_at.h
strerror.o: strerror.c
