#
# Copyright (C) 2012, Northwestern University.
# See COPYRIGHT notice in top-level directory.
#
# @configure_input@

ACLOCAL_AMFLAGS = -I m4

SUBDIRS      = src . run
DIST_SUBDIRS = src run

EXTRA_DIST = ACKNOWLEDGEMENTS README.md RELEASE_NOTES doc inputs

# For VPATH build (parallel build), try delete all sub-directories
distclean-local:
	if [ "$(abs_builddir)" != "$(abs_srcdir)" ] ; then \
           for d in $(DIST_SUBDIRS) ; do \
               rmdir $$d || true ; \
           done ; \
        fi

install-exec-hook:
	@echo '+----------------------------------------------------------------------------+'
	@echo '|'
	@echo '|  GCRM-IO has been successfully installed under'
	@echo '|        ./run'
	@echo '|'
	@echo '|  * The executable name: gcrm_io'
	@echo '|  * Addition input parameter files are available under'
	@echo '|        $(abs_srcdir)/inputs'
	@echo '|'
	@echo '+----------------------------------------------------------------------------+'


dist-hook:
	$(SED_I) -e "1,10s|_RELEASE_DATE_|`date '+%B %e, %Y'`|" $(distdir)/RELEASE_NOTES
	$(SED_I) -e "1,10s|_VERSION_|$(VERSION)|" $(distdir)/RELEASE_NOTES
	$(SED_I) -e "s|_VERSION_|$(VERSION)|" $(distdir)/INSTALL

