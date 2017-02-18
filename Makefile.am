# vim:set noet ts=4:
#
# Copyright (c) 2017 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2017 Red Hat, Inc.

NULL =

SUBDIRS = \
    annotations \
    $(NULL)

pkgconfigdir = $(datadir)/pkgconfig
pkgconfig_DATA = cldr-annotations.pc

EXTRA_DIST = \
    cldr-annotations.pc.in \
    cldr-annotations.spec.in \
    unicode-license.txt \
    $(NULL)

dist-hook:
	if test -d .git ; then \
		git log --name-status --date=iso > $(distdir)/ChangeLog ; \
		PREV_MICRO_VERSION=`expr $(MICRO_VERSION) - 1`; \
		PREV_VERSION=\
"$(MAJOR_VERSION).$(MINOR_VERSION).$$PREV_MICRO_VERSION"; \
		echo "Changes in cldr-annotations $(VERSION)" > $(distdir)/NEWS; \
		echo "" >> $(distdir)/NEWS; \
		git log $$PREV_VERSION...$(VERSION) --reverse \
		        --pretty=format:'%s (%an) %h' >> $(distdir)/NEWS; \
	fi

distclean-local:
	if test "x$(srcdir)" = "x."; then :; else \
		rm -f ChangeLog; \
		rm -f NEWS; \
	fi
