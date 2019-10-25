# vim:set et ts=4:
#
# Copyright (c) 2017-2019 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2017-2019 Red Hat, Inc.

m4_define([con_version], [$1_$2])
m4_define([major_version], [36])
m4_define([minor_version], [12])
# micro_version is Emoij minor version + commit date
m4_define([micro_version], [120191002])
m4_define([local_version], [0])

AC_PREFEQ([2.62])
AC_INIT([cldr-emoji-annotation], major_version.minor_version.con_version(micro_version, local_version),
        [https://github.com/fujiwarat/cldr-emoji-annotation/issues],
        [cldr-emoji-annotation])

# Define sustituted variables:
MAJOR_VERSION=major_version
MINOR_VERSION=minor_version
MICRO_VERSION=micro_version
LOCAL_VERSION=local_version
AC_SUBST(MAJOR_VERSION)
AC_SUBST(MINOR_VERSION)
AC_SUBST(MICRO_VERSION)
AC_SUBST(LOCAL_VERSION)

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

# Support silent build rules. Disable
# by either passing --disable-silent-rules to configure or passing V=1
# to make
AM_SILENT_RULES([yes])

# Check for programs.
AC_PROG_INSTALL
AC_PROG_MAKE_SET

# OUTPUT files
AC_CONFIG_FILES([
Makefile
cldr-emoji-annotation.pc
cldr-emoji-annotation.spec
annotations/Makefile
annotationsDerived/Makefile
])

AC_OUTPUT
AC_MSG_RESULT([
Build options:
  Version                       $VERSION
  Install prefix                $prefix
  Build shared libs             $enable_shared
  Build static libs             $enable_static
])

