AM_CPPFLAGS = -I$(top_srcdir)/src/include
zabbixdir = ${prefix}/zabbix

lib_LTLIBRARIES = libilocrst.la

libilocrst_la_SOURCES = base64.c ilo-credit-store.cpp 

libilocrst_la_LDFLAGS = -shared -fPIC -ltdb -lssl -lcrypto

AUTOMAKE_OPTIONS = foreign

if COMPILING_ON_64
  lib_path = /usr/lib64
else
  lib_path = /usr/lib
endif

if COMPILING_ON_DEBIAN
  LIBPATH = /usr/lib/x86_64-linux-gnu
else
  LIBPATH = ${lib_path}
endif

install:
	install -m 755 .libs/libilocrst.so.0.0.0 $(LIBPATH); \
        ln -sf $(LIBPATH)/libilocrst.so.0.0.0 $(LIBPATH)/libilocrst.so.0; \
	install -m 755 .libs/libilocrst.so $(zabbixdir)/libilocrst.so

clean: clean-am
	unlink $(LIBPATH)/libilocrst.so.0; \
	rm -f $(LIBPATH)/libilocrst.so.0.0.0

uninstall:
	rm -f $(zabbixdir)/libilocrst.so; \
	rm -f /etc/zabbix/.zabbix_credential.tdb
