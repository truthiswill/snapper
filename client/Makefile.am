#
# Makefile.am for snapper/client
#

SUBDIRS = 		\
	utils		\
	Command

AM_CPPFLAGS = -I$(top_srcdir) $(DBUS_CFLAGS)

noinst_LTLIBRARIES = libclient.la
libclient_la_SOURCES =                  \
	types.cc	types.h		\
	commands.cc	commands.h      \
	errors.cc	errors.h

libclient_la_LIBADD =  utils/libutils.la ../dbus/libdbus.la

bin_PROGRAMS = snapper

snapper_SOURCES =					\
	snapper.cc					\
	cleanup.cc		cleanup.h		\
	proxy.cc		proxy.h			\
	proxy-dbus.cc		proxy-dbus.h		\
	proxy-lib.cc		proxy-lib.h		\
	misc.cc			misc.h			\
	Options.cc		Options.h		\
	GlobalOptions.cc	GlobalOptions.h		\
	Command.cc		Command.h

snapper_LDADD = 			\
	libclient.la			\
	../snapper/libsnapper.la	\
	utils/libutils.la		\
	Command/libcommand.la		\
	../dbus/libdbus.la

libexecdir = /usr/lib/snapper

libexec_PROGRAMS = systemd-helper

systemd_helper_SOURCES =		\
	systemd-helper.cc		\
	cleanup.cc	cleanup.h	\
	proxy.cc	proxy.h		\
	proxy-dbus.cc	proxy-dbus.h	\
	proxy-lib.cc	proxy-lib.h	\
	misc.cc		misc.h

systemd_helper_LDADD = libclient.la ../snapper/libsnapper.la utils/libutils.la ../dbus/libdbus.la

if ENABLE_BTRFS

libexec_PROGRAMS += installation-helper

installation_helper_SOURCES =		\
	installation-helper.cc		\
	misc.cc		misc.h

installation_helper_LDADD = ../snapper/libsnapper.la utils/libutils.la

if ENABLE_ROLLBACK

sbin_PROGRAMS = mksubvolume

mksubvolume_SOURCES =			\
	mksubvolume.cc

mksubvolume_LDADD = ../snapper/libsnapper.la utils/libutils.la

endif

endif

