# vim:set noet ts=4:
#
# Copyright (c) 2017 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2017 Red Hat, Inc.

NULL =

SUBDIRS = \
    annotations \
    annotationsDerived \
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
		if test x"$$CUSTOM_PREV_VERSION" != x ; then \
		    PREV_VERSION="$$CUSTOM_PREV_VERSION"; \
		elif test $(LOCAL_VERSION) -gt 1 ; then \
		    PREV_LOCAL_VERSION=`expr $(LOCAL_VERSION) - 1`; \
		    PREV_VERSION=\
"$(MAJOR_VERSION).$(MINOR_VERSION).$(MICRO_VERSION)_$$PREV_LOCAL_VERSION"; \
		elif test $(MICRO_VERSION) -gt 0 ; then \
		    PREV_MICRO_VERSION=`expr $(MICRO_VERSION) - 1`; \
		    PREV_VERSION=\
"$(MAJOR_VERSION).$(MINOR_VERSION).$${PREV_MICRO_VERSION}_$(LOCAL_VERSION)"; \
		elif test $(MINOR_VERSION) -gt 0 ; then \
		    PREV_MINOR_VERSION=`expr $(MINOR_VERSION) - 1`; \
		    PREV_VERSION=\
"$(MAJOR_VERSION).$${PREV_MINOR_VERSION}.$(MICRO_VERSION)_$(LOCAL_VERSION)"; \
		elif test $(MAJOR_VERSION) -gt 0 ; then \
		    PREV_MAJOR_VERSION=`expr $(MAJOR_VERSION) - 1`; \
		    PREV_VERSION=\
"$${PREV_MAJOR_VERSION}.$(MINOR_VERSION).$(MICRO_VERSION)_$(LOCAL_VERSION)"; \
		else \
		    echo "Wrong version $(VERSION)" 1>&2; \
		    exit 1; \
		fi; \
		echo "Changes between $(VERSION) and $$PREV_VERSION" 1>&2; \
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
