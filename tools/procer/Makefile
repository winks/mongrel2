CFLAGS=-DNDEBUG -pthread -g -I../../src -Wall $(OPTFLAGS)
PREFIX?=/usr/local
SOURCES=$(wildcard *.c)
OBJECTS=$(patsubst %.c,%.o,${SOURCES})

all: procer


procer: ../../build/libm2.a ${OBJECTS}
	gcc $(OPTFLAGS) $(OPTLIBS) -o $@ ${OBJECTS} ../../build/libm2.a ${LIBS}

clean:
	rm -f *.o procer

pristine:
	rm -f *.o procer

install: procer
	install procer $(DESTDIR)$(PREFIX)/bin/

netbsd: OPTFLAGS += -I/usr/local/include -I/usr/pkg/include
netbsd: OPTLIBS += -L/usr/local/lib -L/usr/pkg/lib
netbsd: LIBS=-lzmq -lsqlite3 $(OPTLIBS)
netbsd: procer

freebsd: OPTFLAGS += -I/usr/local/include
freebsd: OPTLIBS += -L/usr/local/lib -pthread
freebsd: LIBS=-lzmq -lsqlite3 $(OPTLIBS)
freebsd: procer

openbsd: OPTFLAGS += -I/usr/local/include
openbsd: OPTLIBS += -L/usr/local/lib -pthread
openbsd: LIBS=-lzmq -lsqlite3 $(OPTLIBS)
openbsd: procer
