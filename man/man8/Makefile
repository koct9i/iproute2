# SPDX-License-Identifier: GPL-2.0
TARGETS = ip-address.8 ip-link.8 ip-route.8

MAN8PAGES = $(TARGETS) $(filter-out $(TARGETS),$(wildcard *.8))

all: $(TARGETS)

ip-address.8: ip-address.8.in
	sed "s|@SYSCONFDIR@|$(CONFDIR)|g" $< > $@

ip-link.8: ip-link.8.in
	sed "s|@SYSCONFDIR@|$(CONFDIR)|g" $< > $@

ip-route.8: ip-route.8.in
	sed "s|@SYSCONFDIR@|$(CONFDIR)|g" $< > $@

distclean: clean

clean:
	@rm -f $(TARGETS)

install:
	$(INSTALLDIR) $(DESTDIR)$(MANDIR)/man8
	$(INSTALLMAN) $(MAN8PAGES) $(DESTDIR)$(MANDIR)/man8

check: all
	@for page in $(MAN8PAGES); do test 0 -eq $$($(MAN_CHECK) $$page \
		$(MAN_REDIRECT)) || { echo "Error in $$page"; exit 1; }; done

.PHONY: install clean distclean check
