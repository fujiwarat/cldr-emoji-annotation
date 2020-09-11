# vim:set et ts=4:
#
# Copyright (c) 2017-2020 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2017-2020 Red Hat, Inc.

m4_define([con_version], [$1_$2_$3_$4])
m4_define([cldr_major_version], [38-alpha1])
m4_define([cldr_minor_version], [0])
m4_define([emoji_major_version], [13])
m4_define([emoji_minor_version], [0])
# micro_version is commit date
m4_define([micro_version], [0])
m4_define([local_version], [1])

AC_PREFEQ([2.62])
AC_INIT([cldr-emoji-annotation], con_version(cldr_major_version.cldr_minor_version, emoji_major_version.emoji_minor_version, micro_version, local_version),
        [https://github.com/fujiwarat/cldr-emoji-annotation/issues],
        [cldr-emoji-annotation])

# Define sustituted variables:
CLDR_MAJOR_VERSION=cldr_major_version
CLDR_MINOR_VERSION=cldr_minor_version
EMOJI_MAJOR_VERSION=emoji_major_version
EMOJI_MINOR_VERSION=emoji_minor_version
MICRO_VERSION=micro_version
LOCAL_VERSION=local_version
AC_SUBST(CLDR_MAJOR_VERSION)
AC_SUBST(CLDR_MINOR_VERSION)
AC_SUBST(EMOJI_MAJOR_VERSION)
AC_SUBST(EMOJI_MINOR_VERSION)
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

# --enable-dtd option.
AC_ARG_ENABLE(dtd,
    AS_HELP_STRING([--enable-dtd],
                   [Install DTD files]),
    [enable_dtd=$enableval],
    [enable_dtd=no]
)
AM_CONDITIONAL([ENABLE_DTD], [test x"$enable_dtd" = x"yes"])
if test x"$enable_dtd" != x"yes"; then
    enable_dtd="no (disabled, use --enable-dtd to install DTD files)"
fi

# OUTPUT files
AC_CONFIG_FILES([
Makefile
cldr-emoji-annotation.pc
cldr-emoji-annotation.spec
annotations/Makefile
annotationsDerived/Makefile
common/Makefile
common/dtd/Makefile
])

AC_OUTPUT
AC_MSG_RESULT([
Build options:
  Version                       $VERSION
  Install prefix                $prefix
  Build shared libs             $enable_shared
  Build static libs             $enable_static
  Install DTD files             $enable_dtd
])

