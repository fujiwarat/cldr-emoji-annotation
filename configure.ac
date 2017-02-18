# vim:set et ts=4:
#
# Copyright (c) 2017 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2017 Red Hat, Inc.

m4_define([major_version], [30])
m4_define([minor_version], [0])
m4_define([micro_version], [3])

AC_PREFEQ([2.62])
AC_INIT([cldr-annotations], major_version.minor_version.micro_version,
        [https://github.com/fujiwarat/cldr-annotations/issues],
        [cldr-annotations])

# Define sustituted variables:
MAJOR_VERSION=major_version
MINOR_VERSION=minor_version
MICRO_VERSION=micro_version
AC_SUBST(MAJOR_VERSION)
AC_SUBST(MINOR_VERSION)
AC_SUBST(MICRO_VERSION)

# For dislpay date.
m4_define(datedisplay,
    m4_esyscmd(date '+%a %b %d %Y' | tr -d '\n\r'))
DATE_DISPLAY="datedisplay"
AC_SUBST(DATE_DISPLAY)

AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])

# Init automake.
AM_INIT_AUTOMAKE([1.11.1])
AM_MAINTAINER_MODE([enable])
AC_GNU_SOURCE

# Support silent build rules. Disable
# by either passing --disable-silent-rules to configure or passing V=1
# to make
AM_SILENT_RULES([yes])

# Check for programs.
AC_PROG_INSTALL
AC_PROG_MAKE_SET

# Define PACKAGE_VERSION_* variables.
AM_DISABLE_STATIC
LT_INIT

# OUTPUT files
AC_CONFIG_FILES([
Makefile
cldr-annotations.pc
cldr-annotations.spec
annotations/Makefile
])

AC_OUTPUT
AC_MSG_RESULT([
Build options:
  Version                       $IBUS_VERSION
  Install prefix                $prefix
  Build shared libs             $enable_shared
  Build static libs             $enable_static
])

