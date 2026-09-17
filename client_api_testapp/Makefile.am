AM_CFLAGS = \
    -DDEBUG \
    -I./ \
    $(GPSUTILS_CFLAGS) \
    $(LOCUTILS_CFLAGS) \
    $(LOCCLIENTAPI_CFLAGS) \
    $(LOCINTEGRATIONAPI_CFLAGS) \
    -std=c++11
# HALDAEMON is requird only for msg.h

ACLOCAL_AMFLAGS = -I m4
AM_CPPFLAGS = \
    -std=c++11 \
    -I$(top_srcdir)/client_api/inc \
    -I$(top_srcdir)/integration_api/inc

requiredlibs = \
    $(GPSUTILS_LIBS) \
    $(LOCCLIENTAPI_LIBS) \
    $(LOCINTEGRATIONAPI_LIBS)

h_sources =

c_sources = \
    main.cpp

location_client_api_testapp_SOURCES = \
    $(c_sources) $(h_sources)

######################
# Build location_client_api_testapp
######################

if USE_GLIB
location_client_api_testapp_CFLAGS = -DUSE_GLIB $(AM_CFLAGS) @GLIB_CFLAGS@
location_client_api_testapp_LDFLAGS = -lstdc++ -g -Wl,-z,defs -lpthread @GLIB_LIBS@
location_client_api_testapp_CPPFLAGS = -DUSE_GLIB $(AM_CFLAGS) $(AM_CPPFLAGS) @GLIB_CFLAGS@
else
location_client_api_testapp_CFLAGS = $(AM_CFLAGS)
location_client_api_testapp_LDFLAGS = -lstdc++ -Wl,-z,defs -lpthread
location_client_api_testapp_CPPFLAGS = $(AM_CFLAGS) $(AM_CPPFLAGS)
endif

location_client_api_testapp_LDADD = \
    $(top_builddir)/client_api/liblocation_client_api.la \
    $(top_builddir)/integration_api/liblocation_integration_api.la \
    $(GPSUTILS_LIBS) -lstdc++ -lc -ldl

bin_PROGRAMS = location_client_api_testapp
