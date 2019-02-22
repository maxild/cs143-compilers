
ASSN = 2
#CLASS= cs143
CLASSDIR= ../..
LIB=

SRC= cool.flex test.cl README
CSRC= lextest.cc utilities.cc stringtab.cc handle_flags.cc
TSRC= mycoolc
HSRC=
LSRC= Makefile

CGEN= cool-lex.cc
HGEN=

LIBS= parser semant cgen
CFIL= ${CSRC} ${CGEN}
OBJS= ${CFIL:.cc=.o}
DEPS= $(OBJS:.o=.d)

OUTPUT= test.output

#CPPINCLUDE= -I. -I${CLASSDIR}/include/PA${ASSN} -I${CLASSDIR}/src/PA${ASSN}
CPPINCLUDE= -I. -I${CLASSDIR}/include/PA${ASSN}

FFLAGS= -d -ocool-lex.cc

CC=g++
CFLAGS= -g -Wall -Wno-unused -Wno-write-strings ${CPPINCLUDE}
FLEX=flex ${FFLAGS}
DEPEND = ${CC} -MM ${CPPINCLUDE}

source : ${SRC} ${TSRC} ${LSRC} ${LIBS} lsource

lsource: ${LSRC}

${OUTPUT}: lexer test.cl
	@rm -f test.output
	-./lexer test.cl >test.output 2>&1

dotest:	lexer test.cl
	./lexer test.cl

lexer: ${OBJS}
	${CC} ${CFLAGS} ${OBJS} ${LIB} -o lexer

# .cc.o: (I don't want to use old school double suffix rules)
%.o: %.cc
	${CC} ${CFLAGS} -c $<

cool-lex.cc: cool.flex
	${FLEX} cool.flex

${LIBS}:
	${CLASSDIR}/etc/link-object ${ASSN} $@

${TSRC} ${CSRC}:
	-ln -s ${CLASSDIR}/src/PA${ASSN}/$@ $@

${HSRC}:
	-ln -s ${CLASSDIR}/include/PA${ASSN}/$@ $@

clean :
	-rm -f ${OUTPUT} *.s core ${OBJS} ${DEPS} lexer cool-lex.cc *~ parser cgen semant

clean-compile:
	@-rm -f core ${OBJS} cool-lex.cc ${LSRC}

# outdated way to make dependency files
%.d: %.cc ${SRC} ${LSRC}
	${SHELL} -ec '${DEPEND} $< | sed '\''s/\($*\.o\)[ :]*/\1 $@ : /g'\'' > $@'

-include ${DEPS}


