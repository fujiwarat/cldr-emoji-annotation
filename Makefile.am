# vim:set noet ts=4:
#
# Copyright (c) 2017 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2017 Red Hat, Inc.

NULL =

SUBDIRS = \
    annotations \
    $(NULL)

pkgconfigdir = $(datadir)/pkgconfig
pkgconfig_DATA = cldr-emoji-annotation.pc

EXTRA_DIST = \
    cldr-emoji-annotation.pc.in \
    cldr-emoji-annotation.spec.in \
    unicode-license.txt \
    $(NULL)

dist-hook:
	if test -d .git ; then \
		git log --name-status --date=iso > $(distdir)/ChangeLog ; \
		PREV_LOCAL_VERSION=`expr $(LOCAL_VERSION) - 1`; \
		PREV_VERSION=\
"$(MAJOR_VERSION).$(MINOR_VERSION).$(MICRO_VERSION)_$$PREV_LOCAL_VERSION"; \
		echo "Changes in cldr-annotations $(VERSION)" > $(distdir)/NEWS; \
		echo "" >> $(distdir)/NEWS; \
		if test "x$$PREV_VERSION" = x30.0.3_1 ; then \
		    PREV_VERSION=30.0.3; \
		fi; \
		git log $$PREV_VERSION...$(VERSION) --reverse \
		        --pretty=format:'%s (%an) %h' >> $(distdir)/NEWS; \
	fi

distclean-local:
	if test "x$(srcdir)" = "x."; then :; else \
		rm -f ChangeLog; \
		rm -f NEWS; \
	fi
