
## CS143 Compilers

- https://lagunita.stanford.edu/courses/Engineering/Compilers/Fall2014/course/

- http://web.stanford.edu/class/cs143/

- https://web.stanford.edu/class/archive/cs/cs143/cs143.1128/

## F# links

- https://github.com/fsprojects/zzarchive-powerpack Where are FsLex and FsYacc?

## Lexer notes

> It is a C function that returns an integer, which is a code for one of the possible token names. The attribute value, whether it be another numeric code, a pointer to the symbol table, or nothing, is placed in a global variable `yylval` (in our case — `cool_yylval`), which is shared between the lexical analyzer and parser, thereby making it simple to return both the name and an attribute value of a token.
