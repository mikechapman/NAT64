# This file uses AC_CONFIG_MACRO_DIR, so we need Autoconf 2.58 or better.
AC_PREREQ([2.58])

AC_INIT([WrapSix], [0.2.0], [xhire@wrapsix.org])
AM_INIT_AUTOMAKE([-Wall -Werror])

# prevent automatic adding of "-g -O2" to CFLAGS
OLD_CFLAGS=$CFLAGS
AC_PROG_CC
CFLAGS=$OLD_CFLAGS

AC_CONFIG_FILES([
	Makefile
	src/Makefile
])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADER([src/autoconfig.h.in])

###
# Configuration options
###

AC_ARG_ENABLE([debug],
	      AS_HELP_STRING([--enable-debug], [enable debugging]),
	      [debug=$enableval],
	      [debug=no])

if test "x$debug" = "xyes"; then
	AS_COMPILER_FLAGS(AM_CFLAGS, "-g -ggdb -O0 -pipe -pedantic -Wshadow -Wall -Wextra -Wno-missing-field-initializers -Wno-unused-parameter -Wold-style-definition -Wdeclaration-after-statement -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wpointer-arith -Wcast-align -Wwrite-strings -Winline -Wformat-nonliteral -Wformat-security -Wswitch-enum -Winit-self -Wmissing-include-dirs -Wundef -Waggregate-return -Wnested-externs -Wunsafe-loop-optimizations -Winvalid-pch")
	AC_DEFINE([DEBUG], [], [Turn on debug mode])
else
        AS_COMPILER_FLAGS(AM_CFLAGS, "-O2")
fi


AC_DEFINE([SYSCONFDIR], "--sysconfdir--", [Configuration files directory])

###
# Final commands
###

AC_SUBST([AM_CFLAGS])

AC_OUTPUT
