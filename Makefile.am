##
# global flags

# Default C++ compiler flags. Overidden by target-specific _CXXFLAGS definitions,
# so include this variable on such definitions!
AM_CXXFLAGS := \
    -fdiagnostics-show-option \
    -Werror \
    -Wall \
    -Wextra

AM_CPPFLAGS := \
    $(GMODULE_CFLAGS) \
    $(GTK2_CFLAGS) \
    $(ICAL_CFLAGS) \
    $(SQLITE3_CFLAGS)

AM_LDFLAGS := \
    $(GMODULE_LIBS) \
    $(GTK2_LIBS) \
    $(ICAL_LIBS) \
    $(SQLITE3_LIBS)

# Adding files to MOSTLYCLEANFILES causes them to be removed in the 'clean'
# target. In order to append to it later, we set it to an empty value here.
# Note that we use '=' and not ':='; this is so that variable lookup is
# performed at expansion time.
MOSTLYCLEANFILES = 

##
# targets
bin_PROGRAMS := calendari 
check_PROGRAMS := test_ics_read test_ics_write 

##
# test suite
TESTS := test_ics_read test_ics_write

##
# target info
calendari_SOURCES := \
    calendari.cc \
    calendarlist.cc \
    callback.cc \
    db.cc \
    detailview.cc \
    event.cc \
    ics.cc \
    monthview.cc \
    queue.cc

test_ics_read_CPPFLAGS := $(AM_CPPFLAGS) \
    -DCALENDARI__ICAL__READ__TEST

test_ics_read_SOURCES := \
    ics.cc \
    db.cc \
    event.cc \
    queue.cc

test_ics_write_CPPFLAGS := $(AM_CPPFLAGS) \
    -DCALENDARI__ICAL__WRITE__TEST

test_ics_write_SOURCES := \
    ics.cc \
    db.cc \
    event.cc \
    queue.cc

##
# custom targets
.PHONY: doxygen
doxygen:
	srcdir=$(srcdir) \
	       doxygen $(srcdir)/Doxyfile
