# This file is part of the nesC compiler.
# 
# This file is derived from the RC Compiler. It is thus
#    Copyright (C) 2000-2001 The Regents of the University of California.
# Changes for nesC are
#    Copyright (C) 2002 Intel Corporation
# 
# The attached "nesC" software is provided to you under the terms and
# conditions of the GNU General Public License Version 2 as published by the
# Free Software Foundation.
# 
# nesC is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with nesC; see the file COPYING.  If not, write to
# the Free Software Foundation, Inc., 51 Franklin St, Fifth Floor,
# Boston, MA 02110-1301 USA.

dnl -*- m4 -*-

# force autoconf 2.5 on Debian systems
AC_PREREQ(2.50)

AC_INIT(nesc, 1.3.6)
AC_CONFIG_AUX_DIR(../config-aux)
AC_CONFIG_SRCDIR(c-parse.y)
AC_CONFIG_HEADERS(autoconf.h)
AM_INIT_AUTOMAKE

: ${CFLAGS=-g}

AC_CANONICAL_HOST
AC_SUBST(CPPFLAGS)
AC_SUBST(CFLAGS)

AC_PROG_CC
AC_PROG_RANLIB
AC_PROG_MAKE_SET

CPARSE_TRY_CFLAGS(-Wall)
CPARSE_TRY_CFLAGS(-Wno-long-double)

AC_MSG_CHECKING(whether we are using rcc)
AC_TRY_COMPILE([], [void * traditional pointer;], RCC=yes, RCC=no)
AM_CONDITIONAL(USING_RCC, test "$RCC" = yes)
AC_MSG_RESULT($RCC)

AC_CHECK_SIZEOF(long long)
AC_CHECK_SIZEOF(void *)

AC_FUNC_ALLOCA

AC_REPLACE_FUNCS(strtold)
AC_CHECK_FUNCS(poll realpath mmap)
AC_CHECK_FUNCS(regcomp, [ REGCOMP=yes ])
AC_CHECK_FUNCS(fnmatch, [ FNMATCH=yes ])

AM_CONDITIONAL(NEED_FNMATCH, test "$FNMATCH" != yes)
AM_CONDITIONAL(NEED_REGEX, test "$REGCOMP" != yes)

AM_ICONV

RC_CHECK_DECL(strtold, stdlib.h)

AC_OUTPUT(
	Makefile
	libcompat/Makefile
	)
