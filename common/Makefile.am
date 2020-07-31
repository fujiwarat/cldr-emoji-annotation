# vim:set noet ts=4:
#
# Copyright (c) 2020 Takao Fujiwara <takao.fujiwara1@gmail.com>
# Copyright (c) 2020 Red Hat, Inc.

NULL =

SUBDIRS = \
    dtd \
    $(NULL)

check:
	$(AM_V_at)for dir in annotations annotationsDerived; do \
	    CURRENT_DIR=`pwd`; \
	    cd $(srcdir); \
	    ln -s ../$$dir .; \
	    cd $$CURRENT_DIR; \
	    for xml in $(srcdir)/$$dir/*.xml; do \
	        echo xmllint --noout --valid --postvalid $$xml; \
	        xmllint --noout --valid --postvalid $$xml; \
	        if test $$? -ne 0; then \
	            echo "ERROR"; \
	            exit 1; \
	        fi; \
	    done; \
	    rm $(srcdir)/$$dir; \
	done;
	$(NULL)

