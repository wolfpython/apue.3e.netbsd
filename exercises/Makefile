ROOT=..
PLATFORM=$(shell $(ROOT)/systype.sh)
include $(ROOT)/Make.defines.$(PLATFORM)

ifeq "$(PLATFORM)" "freebsd"
  GETPW = getpw44bsd
  FMEM = fmemopen.o
  EXTRALIBS=-pthread
endif
ifeq "$(PLATFORM)" "netbsd"
  GETPW = getpw44bsd
  #netbsd 6.0 has fmmopen,while freebsd 8 does not,check it later in 9
  #FMEM = fmemopen.o
  EXTRALIBS=-pthread
endif
ifeq "$(PLATFORM)" "linux"
  GETPW = getpwsvr4
  FMEM =
  EXTRALIBS=-pthread
endif
ifeq "$(PLATFORM)" "macos"
  GETPW = getpw44bsd
  FMEM = fmemopen.o
endif
ifeq "$(PLATFORM)" "solaris"
  GETPW = getpwsvr4
  FMEM =
endif

PROGS =	bo fifo1 getlogin goodexit longpath pendlock prtime sizepipe vfork3 zombie

all:	$(PROGS) asyncsocket.o $(FMEM) openmax.o sleep.o sleepus_poll.o sleepus_select.o $(GETPW)

$(PROGS):	$(LIBAPUE)
		$(CC) $(CFLAGS) $@.c -o $@ $(LDFLAGS) $(LDLIBS)

clean:
	rm -f $(PROGS) $(TEMPFILES) *.o $(GETPW)

include $(ROOT)/Make.libapue.inc
