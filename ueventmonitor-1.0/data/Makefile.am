
NULL =

dbusservicedir       = $(datadir)/dbus-1/system-services
dbusservice_in_files = org.freedesktop.UeventMonitor.service.in
dbusservice_DATA     = $(dbusservice_in_files:.service.in=.service)

$(dbusservice_DATA): $(dbusservice_in_files) Makefile
	@sed -e "s|\@ueventmonitorprivdir\@|$(libexecdir)/ueventmonitor|" $< > $@

dbusconfdir = $(sysconfdir)/dbus-1/system.d
dbusconf_in_files = org.freedesktop.UeventMonitor.conf.in
dbusconf_DATA = $(dbusconf_in_files:.conf.in=.conf)

$(dbusconf_DATA): $(dbusconf_in_files) Makefile
	cp $< $@

systemdservice_in_files = ueventmonitor.service.in

if HAVE_SYSTEMD
systemdservicedir       = $(systemdsystemunitdir)
systemdservice_DATA     = $(systemdservice_in_files:.service.in=.service)

$(systemdservice_DATA): ueventmonitor.service.in Makefile
	@sed -e "s|\@ueventmonitorprivdir\@|$(libexecdir)/ueventmonitor|" ueventmonitor.service.in > ueventmonitor.service
endif


EXTRA_DIST =                                                                   \
	org.freedesktop.UeventMonitor.xml                                            \
	$(systemdservice_in_files)                                             \
	$(dbusservice_in_files)                                                \
	$(dbusconf_in_files)                                                   \
	$(NULL)

clean-local:
	rm -f *~                                                               \
	$(dbusservice_DATA)                                                    \
	$(dbusconf_DATA)                                                       \
	$(systemdservice_DATA)
