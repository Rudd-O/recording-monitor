# Process with automake to create Makefile.in

pixmapsdir = $(datadir)/pixmaps
docdir = $(datadir)/doc/$(PACKAGE)-$(VERSION)
appsdir = $(datadir)/applications

bin_SCRIPTS = recording-level-monitor

pixmaps_DATA = \
	recording-level-monitor.png

pkgdata_DATA = \
	version \
	recording-level-monitor.glade \
	recording-level-monitor.gladep \
	recording-level-monitor.png

doc_DATA = \
	README \
	COPYING \
	TODO \
	AUTHORS \
	ChangeLog \
	NEWS

man_MANS = recording-level-monitor.1

# Why do these need to be explicitly put in EXTRA_DIST?

EXTRA_DIST = \
	$(bin_SCRIPTS) \
	$(pkgdata_DATA) \
	$(pixmaps_DATA) \
	$(man_MANS) \
	recording-level-monitor.desktop recording-level-monitor.spec autogen.sh

install-data-hook:
	$(mkinstalldirs) $(DESTDIR)$(appsdir)
	$(DESKTOP_FILE_INSTALL) --vendor rudd-o --dir $(DESTDIR)$(appsdir) $(srcdir)/recording-level-monitor.desktop

rpm: dist
	rpmbuild -ta $(PACKAGE)-$(VERSION).tar.gz

bzdist: dist
	gunzip -c $(PACKAGE)-$(VERSION).tar.gz | bzip2 > $(PACKAGE)-$(VERSION).tar.bz2
