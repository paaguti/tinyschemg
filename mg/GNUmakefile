PROG=	mg

LIBS+=-lutil

CFLAGS += -D_GNU_SOURCE

CFLAGS+=$(shell pkg-config --cflags libbsd-overlay)
LIBS+=$(shell pkg-config --libs libbsd-overlay)

CFLAGS+=$(shell pkg-config --cflags ncursesw)
LIBS+=$(shell pkg-config --libs ncursesw)


# (Common) compile-time options:
#
#	FKEYS		-- add support for function key sequences.
#	REGEX		-- create regular expression functions.
#	STARTUP		-- look for and handle initialization file.
#	XKEYS		-- use termcap function key definitions.
#				note: XKEYS and bsmap mode do _not_ get along.
#
CFLAGS += -Wall -DFKEYS -DREGEX -DXKEYS -DSTARTUP
CFLAGS += -DNOTHEO 

SRCS=	autoexec.c basic.c buffer.c cinfo.c dir.c display.c \
	echo.c extend.c file.c fileio.c funmap.c help.c kbd.c keymap.c \
	line.c macro.c main.c match.c modes.c paragraph.c random.c \
	re_search.c region.c search.c spawn.c tty.c ttyio.c ttykbd.c \
	undo.c version.c window.c word.c yank.c

#
# More or less standalone extensions.
#
SRCS+=cscope.c tags.c grep.c cmode.c dired.c  
NOSRCS=theo.c 

# Tinyscheme extension
SRCS+=	scheme.c mgscheme.c
LIBS+=	-lm

OBJS=$(patsubst %.c,%.o,${SRCS})
CC=gcc
LD=gcc

all:	mg

# CFLAGS+=-DUSE_DL -O0
# SRCS += dynload.c
# LIBS += -l dl

# afterinstall:
# 	${INSTALL} -d ${DESTDIR}${DOCDIR}/mg
# 	${INSTALL} -m ${DOCMODE} -c ${.CURDIR}/tutorial \
# 		${DESTDIR}${DOCDIR}/mg
# 	${INSTALL} -d ${DESTDIR}${SHAREDIR}/mg
# 	${INSTALL} -m ${SHAREMODE} -c ${.CURDIR}/init.scm \
# 		${DESTDIR}${SHAREDIR}/mg

# .include <bsd.prog.mk>


mg:	${OBJS}
	${LD} -o mg ${OBJS} ${LIBS}

%.o:	%.c
	${CC} -c ${CFLAGS} ${CPPFLAGS} $< -o $@

.PHONY: clean
clean:
	rm -vf *.o *~

rebuild:	clean all
