# Process with automake to create Makefile.in

pixmapsdir = $(datadir)/pixmaps
docdir = $(datadir)/doc/$(PACKAGE)-$(VERSION)
appsdir = $(datadir)/applications

bin_SCRIPTS = recording-monitor

pixmaps_DATA = \
	recording-monitor.png

pkgdata_DATA = \
	version \
	recording-monitor.glade \
	recording-monitor.gladep \
	recording-monitor.png

doc_DATA = \
	README \
	COPYING \
	TODO \
	AUTHORS \
	ChangeLog \
	NEWS

man_MANS = recording-monitor.1

# Why do these need to be explicitly put in EXTRA_DIST?

EXTRA_DIST = \
	$(bin_SCRIPTS) \
	$(pkgdata_DATA) \
	$(pixmaps_DATA) \
	$(man_MANS) \
	recording-monitor.desktop recording-monitor.spec autogen.sh

install-data-hook:
	$(mkinstalldirs) $(DESTDIR)$(appsdir)
	$(DESKTOP_FILE_INSTALL) --vendor rudd-o --dir $(DESTDIR)$(appsdir) $(srcdir)/recording-monitor.desktop

rpm: dist
	rpmbuild -ta $(PACKAGE)-$(VERSION).tar.gz

bzdist: dist
	gunzip -c $(PACKAGE)-$(VERSION).tar.gz | bzip2 > $(PACKAGE)-$(VERSION).tar.bz2
