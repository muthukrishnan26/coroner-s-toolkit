SHELL	= /bin/sh
CC	= gcc
OPT	= -O
DEBUG	= -g
INCL	= -I../../src/aux
CFLAGS	= $(DEFS) $(INCL) $(OPT) $(DEBUG)
LIBS	= ../../src/aux/aux_lib.a
BIN_DIR	= .
#BIN_DIR	= ../../bin
MAN_DIR	= ../../man
PROGS	= $(BIN_DIR)/entropy
MANPAGES= entropy.1
#MANPAGES= $(MAN_DIR)/man1/entropy.1

what:
	@sh makedefs

all:	$(PROGS)

manpages: $(MANPAGES)

$(BIN_DIR)/entropy: entropy.c $(LIBS)
	$(CC) $(CFLAGS) -o $@ entropy.c $(LIBS) $(SYSLIBS) -lm

#$(MAN_DIR)/man1/entropy.1: entropy.c
entropy.1: entropy.c
	srctoman $? >$@

clean:
	rm -f $(PROGS) $(LIB) *.o *core

depend: $(MAKES)
	(sed '1,/^# do not edit/!d' Makefile; \
	set -e; for i in [a-z][a-z0-9]*.c; do \
	    $(CC) -E $(DEFS) $(INCL) $$i | sed -n -e '/^# *1 *"\([^"]*\)".*/{' \
	    -e 's//'`echo $$i|sed 's/c$$/o/'`': \1/' -e 'p' -e '}'; \
	done) | grep -v '[.][o][:][ ][/]' >$$$$ && mv $$$$ Makefile

# do not edit - this was generated with make depend
entropy.o: entropy.c
entropy.o: ../../src/aux/error.h
