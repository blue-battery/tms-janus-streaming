ACLOCAL_AMFLAGS = -I m4
JANUS_PATH=$(exec_prefix)
CFLAGS = $(shell pkg-config --cflags glib-2.0) -I$(JANUS_PATH)/include/janus
LIBS = $(shell pkg-config --libs glib-2.0)

lib_LTLIBRARIES = libjanus_tms_rtprx.la
libjanus_tms_rtprx_la_SOURCES = janus_plugin_tms_rtprx.c
libjanus_tms_rtprx_la_LDFLAGS = -version-info 0:0:0 $(shell pkg-config --libs glib-2.0) -L$(JANUS_PATH)/lib
libdir = $(exec_prefix)/lib/janus/plugins