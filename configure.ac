#                                               -*- Autoconf -*-
#  @configure_input@
#
#  Configuration scipt for ClearOS eCAP Adapter Library
#
# Process this file with autoconf to produce a configure script.

AC_INIT([ClearOS eCAP Adapter], [2.1], [], [clearos-ecap-adapter])
AC_CONFIG_AUX_DIR([m4])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_SRCDIR([src/ecap-adapter.cpp])
AC_CONFIG_HEADERS([src/autoconf.h])

AM_INIT_AUTOMAKE([nostdinc])
AM_MAINTAINER_MODE

LT_INIT

m4_include(m4/xstd_common.ac)
m4_include(m4/xstd_cpp_checks.ac)

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET

# Checks for libraries.
AC_CHECK_LIB([expat], [XML_ParserCreate],
    [LIBS="-lexpat $LIBS"],
    [AC_MSG_ERROR([libexpat is not found or unusable.])])

AC_CHECK_LIB([ecap], [main],
    [LIBS="-lecap $LIBS"],
    [AC_MSG_FAILURE([libecap is not found or unusable])]
)

# Checks for header files.
AC_CHECK_HEADERS([libecap/adapter/service.h])

# Checks for typedefs, structures, and compiler characteristics.
# AC_HEADER_STDBOOL
# AC_C_CONST

# Checks for library functions.

# Check word size
AC_CHECK_SIZEOF([long]) 
AS_IF([test "$ac_cv_sizeof_long" -eq 8], [OS_LIBDIR="lib64"], [OS_LIBDIR="lib"])
AC_SUBST([OS_LIBDIR])

AC_CONFIG_FILES([\
        clearos-ecap-adapter.spec \
        squid_ecap.conf \
        Makefile \
        src/Makefile \
])
AC_OUTPUT
