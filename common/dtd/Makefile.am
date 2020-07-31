# vim:set noet ts=4:
#
# Copyright (c) 2020 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2020 Red Hat, Inc.

NULL =

dtd_files = $(wildcard $(srcdir)/*.dtd)

if ENABLE_DTD
dtddir = $(datadir)/unicode/cldr/common/dtd
dtd_DATA = $(dtd_files)
endif

EXTRA_DIST = \
    $(dtd_files) \
    $(NULL)
