#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_INIT([lustre-tools-llnl], [1.8.12])
AC_CONFIG_AUX_DIR([config])
AC_CONFIG_SRCDIR([src/lpurge.c])
AC_CONFIG_HEADER([config.h])

AC_CANONICAL_HOST
AC_CANONICAL_SYSTEM

# Check for system capabilities
AC_SYS_LARGEFILE
case "$target_cpu" in
        i[[3456]]86*)
                # need large file support on 32-bit systems
                AC_DEFINE([_LARGEFILE64_SOURCE], [1], [Support large file sizes])
                ;;
        *)
                ;;
esac

# Automake support
AM_INIT_AUTOMAKE([foreign no-define])
AM_MAINTAINER_MODE

AC_MSG_CHECKING([whether to configure just enough for make dist])
AC_ARG_ENABLE([dist],
        AC_HELP_STRING([--enable-dist],
                        [only configure enough for make dist]),
        [], [enable_dist="no"])
AC_MSG_RESULT([$enable_dist])

AS_IF([test "x$enable_dist" = "xno"], [

# Checks for programs.
AC_PROG_CC

# Check for headers
AC_CHECK_HEADERS([lustre/lustre_user.h], [],
        [AC_MSG_ERROR([lustre header not found])])

]) dnl enable_dist

AC_CONFIG_FILES([lustre-tools-llnl.spec
                 Makefile
                 doc/Makefile
                 doc/man/Makefile
                 src/Makefile
                 scripts/Makefile])


AC_OUTPUT
