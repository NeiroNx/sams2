# not a GNU package. You can remove this line, if
# have all needed files, that a GNU package needs
AUTOMAKE_OPTIONS = foreign 1.4

SUBDIRS = src php doc plugins/loadavg plugins/fsusage
bin_SCRIPTS = scripts/sams_send_email

EXTRA_DIST = Makefile.cvs doc php etc spec debian redhat scripts
DISTCLEANFILES = Makefile.in configure aclocal.m4 config.guess config.sub depcomp install-sh ltmain.sh missing

dist-hook:
	find $(distdir) -type d -name .svn | xargs rm -rf

docdir = $(datadir)/doc/$(PACKAGE)-$(VERSION)

install-data-local:
#	$(mkinstalldirs) $(datadir)/$(distdir)
	$(mkinstalldirs) $(sysconfdir)
	if [ ! -f $(sysconfdir)/sams2.conf ] ; then \
	    $(install_sh) -c -m 644 $(top_srcdir)/etc/sams2.conf $(sysconfdir) ;\
	fi
	if [ ! -f $(HTTPD_INCLUDE)/sams2.conf ] ; then \
	    $(install_sh) -c -m 644 $(top_srcdir)/etc/httpd_conf $(HTTPD_INCLUDE)/sams2.conf ;\
	    sed -i -e 's,__WEBPREFIX,$(datadir)/sams2,g' $(HTTPD_INCLUDE)/sams2.conf ;\
	fi
	if [ ! -f $(HTTPD_INCLUDE)/doc4sams2.conf ] ; then \
	    $(install_sh) -c -m 644 $(top_srcdir)/etc/doc_sams2_conf $(HTTPD_INCLUDE)/doc4sams2.conf ;\
	    sed -i -e 's,__DOCPREFIX,$(docdir),g' $(HTTPD_INCLUDE)/doc4sams2.conf ;\
	fi


uninstall-local:
	if [ -f $(sysconfdir)/sams2.conf ] ; then \
		mv -f $(sysconfdir)/sams2.conf $(sysconfdir)/sams2.conf.save ;\
	fi
	if [ -f $(HTTPD_INCLUDE)/sams2.conf ] ; then \
		mv -f $(HTTPD_INCLUDE)/sams2.conf $(HTTPD_INCLUDE)/sams2.conf.save ;\
	fi
	if [ -f  $(HTTPD_INCLUDE)/doc4sams2.conf ] ; then \
		mv -f $(HTTPD_INCLUDE)/doc4sams2.conf $(HTTPD_INCLUDE)/doc4sams2.conf.save ;\
	fi
